# Gmail Weather Report Automation with n8n

An n8n workflow that retrieves weather data for Bengaluru, uses Google Gemini to turn the forecast into a readable daily report, and sends the report through Gmail.

## Workflow

1. **Manual Trigger** — starts the workflow when you click Execute.
2. **HTTP Request** — retrieves weather data from `https://wttr.in/bengaluru?format=j1`.
3. **Message a model (Google Gemini)** — generates a concise full-day weather report from the API response.
4. **Send a message (Gmail)** — emails the generated report.

## Screenshots

### n8n workflow
![Complete n8n workflow](screenshots/Gmail-workflow.png)

### Email received in Gmail
![Generated weather report in Gmail](screenshots/gmail.png)

## Requirements

- An n8n instance
- Google Gemini API credentials configured in n8n
- Gmail OAuth2 credentials configured in n8n
- Internet access for the weather API

## Import and configure

1. Download `Gmail_Weather_Report.json` from this repository.
2. In n8n, import the JSON workflow.
3. Open the **Message a model** node and select/configure your own Google Gemini credentials.
4. Open the **Send a message** node and select/configure your own Gmail OAuth2 credentials.
5. Replace `YOUR_EMAIL@example.com` in the Gmail node with the recipient email you intend to use.
6. Execute the workflow and check the node outputs and destination inbox.

## Important notes

- The shared workflow JSON has had credential references removed and the recipient email replaced with a placeholder. You must configure your own credentials after importing it.
- This version uses a **Manual Trigger**. It does not send automatically every morning. To automate it, add a **Schedule Trigger**, configure the desired time and timezone, connect it to the HTTP Request node, and publish/activate the workflow as supported by your n8n version.
- The weather endpoint is an external service; availability and response format may change.
- Never commit API keys, OAuth tokens, `.env` files, or other secrets to GitHub.

## Technologies

- n8n
- HTTP Request / wttr.in weather API
- Google Gemini
- Gmail OAuth2

## License

Add a license if you want others to reuse or distribute this project. Without a license, normal copyright restrictions apply.
