# Dance Moves Tracker

A serverless single-page application to track Bachata dance moves. This project uses a static HTML frontend hosted on GitHub Pages and utilizes Google Sheets as a database via Google Apps Script.

## Features

- **Move Tracking**: Log successful attempts of specific Bachata moves (Body Roll, Folding Combre, etc.) across different positions (Face to Face, Shadow, etc.).
- **Serverless Architecture**: No backend server maintenance required. Data is processed by Google Apps Script and stored directly in Google Sheets.
- **Spam Protection**: Implements a hidden "Honeypot" field to trap and reject bot submissions without CAPTCHAs.
- **Responsive UI**: Styled with Tailwind CSS using a soft, pastel color palette (Rose/Slate/Emerald).
- **Smart Defaults**: Automatically assigns "Anonymous [Row ID]" if the follower name is left blank.

## Technologies Used

- **Frontend**: HTML5, JavaScript (Fetch API)
- **Styling**: Tailwind CSS (CDN), FontAwesome (Icons)
- **Backend**: Google Apps Script
- **Database**: Google Sheets
- **Hosting**: GitHub Pages

## Setup Guide

### 1. Google Sheets & Apps Script (Backend)

1.  Create a new Google Sheet.
2.  Open **Extensions** > **Apps Script**.
3.  Paste the backend logic (handling `doPost`, locking, and row appending).
4.  **Deploy**:
    - Click **Deploy** > **New deployment**.
    - Select type: **Web app**.
    - Description: "Dance Tracker v1".
    - Execute as: **Me** (your email).
    - Who has access: **Anyone** (Crucial for the form to work without login).
5.  Copy the generated **Web App URL**.

### 2. Frontend Configuration

1.  Open `index.html`.
2.  Find the `scriptURL` constant in the `<script>` tag at the bottom:
    ```javascript
    const scriptURL = 'https://script.google.com/macros/s/YOUR_DEPLOYMENT_ID/exec';
    ```
3.  Replace the URL with the Web App URL you copied in the previous step.

### 3. Deployment to GitHub Pages

1.  Commit and push your changes to GitHub.
2.  Go to your repository **Settings**.
3.  Navigate to **Pages** (under "Code and automation").
4.  Under **Build and deployment** > **Branch**, select `main` and `/ (root)`.
5.  Click **Save**. Your site will be live shortly at `https://<username>.github.io/<repo-name>/`.

## Customization

To add new moves:
1.  Add a new row in the HTML `<table>` following the existing pattern.
2.  Ensure the `name` attribute of the checkbox matches a header in your Google Sheet.
3.  Update the `HEADERS` array in your Google Apps Script to include the new field name.

## License

MIT