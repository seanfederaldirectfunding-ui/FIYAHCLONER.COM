# FIYAHCLONER AI NEXUS - Netlify Deployment Guide

## Prerequisites

Before deploying to Netlify, ensure you have:

1. A Netlify account (sign up at https://netlify.com)
2. Your Stripe account credentials
3. Git repository with your code

## Environment Variables

You need to set up the following environment variables in Netlify:

### Required Stripe Variables

\`\`\`
STRIPE_SECRET_KEY=sk_test_... (or sk_live_... for production)
STRIPE_PUBLISHABLE_KEY=pk_test_... (or pk_live_... for production)
NEXT_PUBLIC_STRIPE_PUBLISHABLE_KEY=pk_test_... (or pk_live_... for production)
\`\`\`

**Note:** Your Stripe account ID is `acct_1SLAHTAUgbM676qQ`

### Optional Variables (for future integrations)

\`\`\`
# AI API Keys (if you want to connect real AI services)
OPENAI_API_KEY=your_openai_key
ANTHROPIC_API_KEY=your_anthropic_key
XAI_API_KEY=your_xai_key
GROQ_API_KEY=your_groq_key

# Database (if you add database features)
DATABASE_URL=your_database_url
\`\`\`

## Deployment Steps

### Option 1: Deploy via Netlify UI (Recommended)

1. **Push your code to GitHub**
   \`\`\`bash
   git init
   git add .
   git commit -m "Initial commit - FIYAHCLONER AI NEXUS"
   git branch -M main
   git remote add origin https://github.com/yourusername/fiyahcloner.git
   git push -u origin main
   \`\`\`

2. **Connect to Netlify**
   - Go to https://app.netlify.com
   - Click "Add new site" → "Import an existing project"
   - Choose "GitHub" and authorize Netlify
   - Select your repository

3. **Configure Build Settings**
   - Build command: `npm run build`
   - Publish directory: `.next`
   - Click "Show advanced" and add environment variables

4. **Add Environment Variables**
   - Click "Add environment variable"
   - Add all required Stripe variables (see above)
   - Make sure `NEXT_PUBLIC_STRIPE_PUBLISHABLE_KEY` is set

5. **Deploy**
   - Click "Deploy site"
   - Wait for build to complete (usually 2-5 minutes)
   - Your site will be live at `https://your-site-name.netlify.app`

### Option 2: Deploy via Netlify CLI

1. **Install Netlify CLI**
   \`\`\`bash
   npm install -g netlify-cli
   \`\`\`

2. **Login to Netlify**
   \`\`\`bash
   netlify login
   \`\`\`

3. **Initialize Netlify**
   \`\`\`bash
   netlify init
   \`\`\`
   - Choose "Create & configure a new site"
   - Select your team
   - Enter a site name (or leave blank for random)

4. **Set Environment Variables**
   \`\`\`bash
   netlify env:set STRIPE_SECRET_KEY "your_stripe_secret_key"
   netlify env:set STRIPE_PUBLISHABLE_KEY "your_stripe_publishable_key"
   netlify env:set NEXT_PUBLIC_STRIPE_PUBLISHABLE_KEY "your_stripe_publishable_key"
   \`\`\`

5. **Deploy**
   \`\`\`bash
   netlify deploy --prod
   \`\`\`

## Post-Deployment Checklist

After deployment, verify the following:

### 1. Test Core Features
- [ ] Homepage loads correctly
- [ ] Navigation works (all menu items)
- [ ] Universal AI Maker interface displays
- [ ] Page Master feature is accessible

### 2. Test Admin Panel
- [ ] Navigate to `/admin`
- [ ] Login with master credentials:
  - Email: `sean.federaldirectfunding@gmail.com`
  - Password: `Rasta4iva`
- [ ] Verify admin dashboard loads

### 3. Test Stripe Integration
- [ ] Navigate to `/pricing`
- [ ] Click "Get Started" on any plan
- [ ] Verify Stripe checkout modal opens
- [ ] Test with Stripe test card: `4242 4242 4242 4242`

### 4. Test Digital Handyman
- [ ] Navigate to `/handyman`
- [ ] Verify all tools load:
  - Code Analyzer
  - Website Health Check
  - Deployment Tool
  - Migration Tool
  - Error Fixer

## Troubleshooting

### Build Fails

**Error: "Module not found"**
- Solution: Run `npm install` locally and commit `package-lock.json`

**Error: "Environment variable not found"**
- Solution: Double-check all environment variables are set in Netlify dashboard

### Runtime Errors

**Stripe checkout not working**
- Verify `NEXT_PUBLIC_STRIPE_PUBLISHABLE_KEY` is set (must have `NEXT_PUBLIC_` prefix)
- Check Stripe dashboard for API key validity
- Ensure you're using test keys for testing

**Admin login fails**
- Verify credentials are correct
- Check browser console for errors
- Ensure API routes are deployed correctly

### Performance Issues

**Slow page loads**
- Enable Netlify's "Asset Optimization" in Site settings
- Consider adding a CDN for static assets
- Check Netlify Analytics for bottlenecks

## Custom Domain Setup

1. **Add Custom Domain**
   - Go to Site settings → Domain management
   - Click "Add custom domain"
   - Enter your domain name

2. **Configure DNS**
   - Add Netlify's nameservers to your domain registrar:
     - `dns1.p01.nsone.net`
     - `dns2.p01.nsone.net`
     - `dns3.p01.nsone.net`
     - `dns4.p01.nsone.net`

3. **Enable HTTPS**
   - Netlify automatically provisions SSL certificates
   - Wait 24-48 hours for DNS propagation

## Continuous Deployment

Netlify automatically deploys when you push to your main branch:

\`\`\`bash
git add .
git commit -m "Update feature"
git push origin main
\`\`\`

Your site will rebuild and deploy automatically!

## Monitoring & Analytics

1. **Enable Netlify Analytics**
   - Go to Site settings → Analytics
   - Enable server-side analytics

2. **Monitor Build Logs**
   - Check Deploys tab for build status
   - Review logs for any errors

3. **Set Up Notifications**
   - Go to Site settings → Build & deploy → Deploy notifications
   - Add email or Slack notifications

## Production Checklist

Before going live with real payments:

- [ ] Replace Stripe test keys with live keys
- [ ] Test all payment flows thoroughly
- [ ] Set up proper error monitoring (e.g., Sentry)
- [ ] Configure custom domain
- [ ] Enable HTTPS
- [ ] Set up backup/monitoring
- [ ] Review Stripe webhook settings
- [ ] Test admin panel security
- [ ] Enable rate limiting on API routes
- [ ] Add proper logging

## Support

For issues:
- Netlify Support: https://answers.netlify.com
- Stripe Support: https://support.stripe.com
- Next.js Docs: https://nextjs.org/docs

## Security Notes

1. **Never commit sensitive keys** to Git
2. **Use environment variables** for all secrets
3. **Rotate keys regularly** (every 90 days)
4. **Enable 2FA** on Netlify and Stripe accounts
5. **Monitor access logs** in admin dashboard
6. **Keep dependencies updated** with `npm audit`

---

**Your FIYAHCLONER AI NEXUS is now ready for deployment!**

For questions or issues, contact: sean.federaldirectfunding@gmail.com
\`\`\`

```json file="" isHidden
