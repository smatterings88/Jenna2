# Deployment Guide for Render.com

## Prerequisites

1. A Render.com account
2. Your repository pushed to GitHub, GitLab, or Bitbucket
3. All required API keys and credentials

## Environment Variables

Before deploying, you'll need to set up the following environment variables in your Render dashboard:

### Required Variables:
- `TWILIO_ACCOUNT_SID` - Your Twilio Account SID
- `TWILIO_AUTH_TOKEN` - Your Twilio Auth Token  
- `TWILIO_PHONE_NUMBER` - Your Twilio phone number (e.g., +1234567890)
- `ULTRAVOX_API_KEY` - Your Ultravox API key
- `GHL_API_KEY` - Your GoHighLevel API key
- `GHL_LOCATION_ID` - Your GoHighLevel location ID

### Optional Variables:
- `SERVER_BASE_URL` - Will be auto-detected if not set
- `NODE_ENV` - Set to "production" (already configured in render.yaml)
- `PORT` - Set to 10000 (already configured in render.yaml)

## Deployment Steps

### Option 1: Using render.yaml (Recommended)

1. **Connect your repository** to Render
2. **Create a new Web Service** from your repository
3. **Set environment variables** in the Render dashboard
4. **Deploy** - Render will automatically use the `render.yaml` configuration

### Option 2: Manual Configuration

1. **Create a new Web Service** on Render
2. **Connect your repository**
3. **Configure the service:**
   - **Environment:** Node
   - **Region:** Oregon (or your preferred region)
4. **Add environment variables** (see list above)
5. **Deploy**

## Post-Deployment

## Important Notes

- **Cold starts:** Free tier services may experience cold starts after periods of inactivity
- **Logs:** Monitor your application logs in the Render dashboard
- **SSL:** Render automatically provides SSL certificates for all deployments
- **Custom domains:** You can add custom domains in the Render dashboard

## Troubleshooting

### Common Issues:

1. **Environment variables not set:** Check that all required variables are configured
2. **Phone number format:** Ensure phone numbers are in E.164 format (+1234567890)
3. **API key issues:** Verify all API keys are valid and have proper permissions
4. **Webhook URLs:** Make sure external services are configured with your new Render URL

### Checking Logs:

```bash
# View recent logs in Render dashboard or use Render CLI
render logs -s your-service-name
```

## Health Check

The application includes a health check endpoint at `/health` that Render uses to monitor service health.

## Scaling

- **Free tier:** Limited resources and may sleep after inactivity
- **Paid tiers:** Better performance and no sleeping
- **Auto-scaling:** Available on higher tier plans