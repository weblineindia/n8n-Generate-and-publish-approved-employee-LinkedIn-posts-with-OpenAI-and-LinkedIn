## Quick Overview

This workflow scans an RSS blog feed on a schedule, logs newly found posts to Google Sheets, uses OpenAI to generate role-based LinkedIn drafts, and emails approval links via Gmail; approved drafts are then published to LinkedIn and tracked in Google Sheets, with Slack alerts on failures.

## How it works

1. Runs on a schedule and reads the latest item from your blog’s RSS feed.
2. Checks Google Sheets to see if the blog URL has already been processed and continues only for new posts.
3. Formats the blog details, saves the blog as processed in Google Sheets, and passes the content into a linked "AI Content Personalization Engine" workflow.
4. Receives the blog content from the sub-workflow, defines employee personas (CEO, HR, Developer, Marketing), and uses OpenAI to generate a LinkedIn draft per role.
5. Stores each generated draft in a Google Sheets **generated_posts** tab with a Pending status and emails approval/rejection links via Gmail.
6. Receives an approve/reject webhook click, updates the post’s status in Google Sheets, and returns a confirmation response to the browser.
7. Fetches approved posts from Google Sheets, posts unpublished items to LinkedIn via the LinkedIn API, marks them as published in Google Sheets when creation succeeds, and sends a Slack alert if the LinkedIn API response is not successful.

## Requirements

- [**n8n account** (Self-hosted or Cloud)](https://n8n.partnerlinks.io/om1efg2qgvwi)
- Google Sheets account
- OpenAI API credentials
- Gmail account
- LinkedIn Developer App with permission to publish posts
- Slack workspace and credentials
- RSS feed URL containing blog posts to monitor

## Setup

1. Add credentials for Google Sheets, OpenAI, Gmail, LinkedIn, and Slack.
2. Set your RSS feed URL in the RSS reader and configure the schedule interval for how often you want to scan for new posts.
3. Create a Google Sheets spreadsheet with two tabs matching the workflow:
   - **processed_blogs** (url, title, processed_at)
   - **generated_posts** (role, tone, postId, status, blog_title, created_at, generated_post, published)
4. Replace `YOUR_N8N_URL_HERE` in the approval link templates and configure the webhook path (`approve-post`) to be reachable from your email recipients.
5. Update the Gmail recipient address used for approvals and ensure your LinkedIn app/connection has permission to create posts via the LinkedIn REST API.

## Need Help?

If you need help setting up this workflow, customizing the AI content generation process or building advanced publishing automations, our **n8n developers** at WeblineIndia are here to help.

We can help you:

- Deploy and customize n8n workflows for your business.
- Build AI-powered content generation and approval workflows.
- Integrate LinkedIn, Google Workspace, Slack and other business applications.
- Develop scalable [Process Automation Solutions](https://www.weblineindia.com/process-automation-solutions.html).
- Extend and optimize workflows with our [n8n Automation Services](https://www.weblineindia.com/n8n-automation/).

👉 [Contact WeblineIndia](https://www.weblineindia.com/contact-us.html) or hire our dedicated [n8n Developers](https://www.weblineindia.com/hire-n8n-developers/) to build production-ready automation solutions tailored to your business.
