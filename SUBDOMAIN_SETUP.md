# Setting Up Subdomain: beta.peachsounds.com

For subdomains, you use **CNAME records** instead of A records. It's actually simpler!

## DNS Setup for beta.peachsounds.com

### Add This CNAME Record:

At your domain registrar (Namecheap, GoDaddy, etc.):

```
Type: CNAME
Name: beta
Value: sarel-128.github.io
TTL: Automatic (or 3600)
```

**That's it!** Just one record needed.

## GitHub Pages Setup

1. **Go to:** https://github.com/sarel-128/dynamicmusicvst-landing/settings/pages
2. **Custom domain:** Enter `beta.peachsounds.com` (not `peachsounds.com`)
3. **Click Save**
4. GitHub will create a CNAME file with `beta.peachsounds.com`

## Differences: Subdomain vs Apex Domain

### Apex Domain (peachsounds.com):
- Requires **4 A records** (more complex)
- Points to IP addresses: 185.199.108.153, etc.
- Takes longer to verify
- Can't use CNAME (DNS limitation)

### Subdomain (beta.peachsounds.com):
- Requires **1 CNAME record** (simpler!)
- Points to: `sarel-128.github.io`
- Usually verifies faster
- Easier to set up

## Advantages of Using Subdomain

✅ **Simpler setup** - Just one CNAME record
✅ **Faster verification** - Usually works within minutes
✅ **Easier to change** - Can point to different services later
✅ **Less DNS conflicts** - Won't interfere with main domain
✅ **Better for testing** - Can have multiple subdomains

## Step-by-Step Setup

### 1. Add CNAME Record

**At your domain registrar:**

1. Go to DNS Management
2. Add new record:
   - **Type:** CNAME
   - **Name/Host:** `beta`
   - **Value/Target:** `sarel-128.github.io`
   - **TTL:** Auto or 3600
3. Save

### 2. Configure GitHub Pages

1. Repository → Settings → Pages
2. Custom domain: `beta.peachsounds.com`
3. Save
4. Wait for DNS check (usually 5-30 minutes)

### 3. Verify DNS

Check if it's working:
```bash
# Check CNAME record
dig beta.peachsounds.com +short
# Should return: sarel-128.github.io
```

Or use: https://www.whatsmydns.net/#CNAME/beta.peachsounds.com

### 4. Enable HTTPS

Once DNS is verified:
1. GitHub Pages settings
2. Check "Enforce HTTPS"
3. Done!

## Your Site Will Be Live At:

- `https://beta.peachsounds.com` ✅

## Multiple Subdomains

You can have multiple subdomains pointing to different things:

- `beta.peachsounds.com` → Landing page (GitHub Pages)
- `app.peachsounds.com` → Your app (if you host it)
- `www.peachsounds.com` → Main website
- `peachsounds.com` → Main domain (can point elsewhere)

Each subdomain is independent!

## Troubleshooting

**If HTTPS still not available:**

1. **Check CNAME record:**
   - Must point to: `sarel-128.github.io` (exact match)
   - No trailing dot
   - Name should be just `beta` (not `beta.peachsounds.com`)

2. **Wait for DNS propagation:**
   - Can take 5 minutes to 24 hours
   - Usually works within 30 minutes for subdomains

3. **Verify in GitHub:**
   - Settings → Pages
   - Should show green checkmark ✅
   - "DNS check successful"

4. **Check CNAME file:**
   - Should exist in repository
   - Should contain: `beta.peachsounds.com`

## Quick Checklist

- [ ] CNAME record added: `beta` → `sarel-128.github.io`
- [ ] Custom domain set in GitHub: `beta.peachsounds.com`
- [ ] CNAME file created by GitHub
- [ ] DNS propagated (check with whatsmydns.net)
- [ ] DNS check successful in GitHub
- [ ] HTTPS enabled

That's it! Subdomains are actually easier than apex domains. 🚀

