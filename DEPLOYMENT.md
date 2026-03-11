# Study Quest - Deployment Guide

## Prerequisites
- GitHub account
- Vercel account (free)
- Supabase project (already set up)

## Step-by-Step Deployment

### 1. Prepare Your Repository

If you haven't already pushed to GitHub:

```bash
git init
git add .
git commit -m "Initial commit: Study Quest app"
git branch -M main
git remote add origin YOUR_GITHUB_REPO_URL
git push -u origin main
```

### 2. Deploy to Vercel

1. Go to https://vercel.com
2. Sign in with your GitHub account
3. Click "Add New Project"
4. Import your Study Quest repository
5. Configure the project:
   - **Framework Preset**: Next.js (auto-detected)
   - **Root Directory**: ./
   - **Build Command**: npm run build (default)
   - **Output Directory**: .next (default)

6. Add Environment Variables:
   - Click "Environment Variables"
   - Add these variables from your `.env` file:
     ```
     NEXT_PUBLIC_SUPABASE_URL=your_supabase_url
     NEXT_PUBLIC_SUPABASE_ANON_KEY=your_anon_key
     ```

7. Click "Deploy"

8. Wait 2-3 minutes for deployment to complete

9. Your app will be live at: `https://your-project.vercel.app`

### 3. Configure Custom Domain (Optional)

1. In Vercel dashboard, go to your project
2. Click "Settings" → "Domains"
3. Add your custom domain
4. Follow DNS configuration instructions

### 4. Supabase Configuration

Ensure your Supabase database has:
- All migrations applied
- RLS policies enabled
- Authentication enabled

No additional Supabase configuration needed - your environment variables handle the connection.

## Alternative Platforms

### Netlify
```bash
# Build command
npm run build

# Publish directory
.next

# Environment variables (same as Vercel)
NEXT_PUBLIC_SUPABASE_URL
NEXT_PUBLIC_SUPABASE_ANON_KEY
```

### Railway
1. Connect GitHub repository
2. Add environment variables
3. Railway auto-detects Next.js and deploys

## Post-Deployment Checklist

- [ ] Test user registration
- [ ] Test user login
- [ ] Create a task
- [ ] Complete a Pomodoro session
- [ ] Check leaderboard
- [ ] Verify XP and streak tracking
- [ ] Test on mobile devices

## Troubleshooting

### Database Connection Issues
- Verify environment variables are set correctly
- Check Supabase URL doesn't have trailing slash
- Ensure migrations are applied

### Authentication Issues
- Verify Supabase auth is enabled
- Check CORS settings in Supabase dashboard
- Add your deployment URL to allowed origins

### Build Failures
- Check all dependencies are in package.json
- Ensure Node version is compatible (18+)
- Review build logs for specific errors

## Monitoring

After deployment:
- Check Vercel Analytics for usage
- Monitor Supabase dashboard for database activity
- Review error logs in Vercel dashboard

## Environment Variables Reference

```env
# Required
NEXT_PUBLIC_SUPABASE_URL=https://your-project.supabase.co
NEXT_PUBLIC_SUPABASE_ANON_KEY=your-anon-key-here
```

## Support

If you encounter issues:
1. Check Vercel deployment logs
2. Review Supabase logs
3. Verify environment variables are correct
4. Ensure migrations are applied to Supabase

---

Built with Next.js, Supabase, and Tailwind CSS
