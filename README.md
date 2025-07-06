Blog Post Agent - AI-Powerd Content Agent
Transform your Google Sheets ideas into published WordPress blog posts with AI-powered content generation.

This is a single-page app. 

For a modular version that includes creation of Instagram captions, check out https://github.com/sweehan/agent-post.

🚀 Overview
Blog Post Agent is a web-based automation tool that:
- Reads blog post ideas from Google Sheets
- Generates content using AI (Claude/OpenAI) or manual templates
- Publishes directly to WordPress
- Sends email notifications
- Tracks all activity with detailed logs
✨ Features
- Google Sheets Integration - Pull blog ideas from any spreadsheet
- AI Content Generation - Support for Claude API and OpenAI
- WordPress Publishing - Direct publishing via REST API
- Email Notifications - Get notified when posts are processed
- Activity Logging - Track all actions and errors
- Secure Credential Storage - All credentials stored locally in browser
- No Backend Required - Runs entirely in the browser
📋 Prerequisites
1. Google Cloud Account (for Sheets API)
2. WordPress Site with REST API enabled
3. AI API Key (optional - for Claude/OpenAI)
4. Web Server to host the HTML file

🛠️ Setup Instructions

Step 1: Google Sheets API Setup
- Go to Google Cloud Console
- Create a new project or select existing
- Enable Google Sheets API:
- APIs & Services → Library
- Search "Google Sheets API"
- Click Enable
- Create API Key:
- APIs & Services → Credentials
- Create Credentials → API Key
- Restrict key to Google Sheets API
- Set up your spreadsheet:
- Create a Google Sheet with columns: Title | Keywords | Topic | Status
- Share → Anyone with link can view
- Copy the Spreadsheet ID from the URL

Step 2: WordPress Configuration
- Enable Application Passwords:
- Log into WordPress admin
- Users → Your Profile
- Scroll to "Application Passwords"
- Enter name: "Blog Post Agent"
- Generate password and copy it
- Verify REST API:
- Visit: https://yoursite.com/wp-json/wp/v2/posts
- Should see JSON data (or authentication error)

Step 3: AI Setup (Optional)
For Claude:
- Get API key from Anthropic Console
- Deploy Cloudflare Worker for CORS (see cloudflare-worker.js)
- Enter Worker URL in the tool
 
 For Manual Mode:
- No API needed - uses template content

Step 4: Deploy the Tool
- Download blog-post-agent.html
- Upload to your web server
- Access via HTTPS: https://yoursite.com/tools/blog-post-agent.html
- For security, consider password protecting the directory or using zero-trust access

📖 Usage Guide

Initial Configuration
- Credentials Tab:
- Enter Google API Key and Spreadsheet ID
- Add WordPress URL, username, and app password
- Configure AI provider (manual/Claude,OpenAI)
- Set up email notifications (optional)
- Save All Settings:
- Click each "Save" button
- Settings persist in browser localStorage

Running the Automation
- Dashboard Tab:
- Click "Check for New Posts" to scan your sheet
- Review pending posts count
- Click "Process All Pending" to generate and publish
- Monitor Progress:
- Watch status messages
- Check Activity Logs tab for details
- Published posts appear as drafts in WordPres
- Google Sheets Format
- Your spreadsheet should have these columns:
   - Title
   - Keywords
   - Topic
   - Status
- Status column is optional (defaults to "pending")
- Only rows with "pending" or empty status are processed

🔒 Security Notes
- All credentials are stored locally in your browser
- Never commit credentials to version control
- Use HTTPS for production deployment
- Consider IP restrictions or password protection
- Use Application passwords NOT main passwords

🐛 Troubleshooting

"Failed to publish" error
- Verify WordPress credentials
- Check if REST API is accessible
- Ensure you're not logged into WordPress (it can interfere)
- Try "Test Connections" first

"Failed to fetch" error
- Check API keys are correct
- Verify Google Sheet is publicly viewable
- For AI APIs, ensure CORS proxy is set up

No Posts Found
- Check spreadsheet ID and range
- Verify sheet has correct column structure
- Ensure status column doesn't say "published"

🤝 Contributing
Feel free to fork and submit pull requests. Some ideas for improvements:
- Add support for featured images
- Include SEO metadata
- Schedule posts for future dates
- Support for categories/tags
- Batch processing limits
📄 License
MIT License - feel free to use and modify for your needs.
🙏 Acknowledgments
Built with vanilla JavaScript and modern browser APIs. Special thanks to the WordPress REST API and Google Sheets API documentation.

Note: Never share your API keys or credentials. Always use environment-specific configurations for production deployments. For the highest security, a zero-trust security model is recommended for access to the tool, e.g. CloudFlare Zero Trust
