# Leo's Link Page

A single-file linktree replacement. No dependencies, no build step.

## Editing

Open `index.html` and edit the `CONFIG` object at the top:

- **links** — main link buttons
- **highlights** — featured article cards (great for Instagram carousel links)
- **socials** — social icons at the bottom
- **avatar** — set a URL for your profile photo (or leave empty for initials)

## Deployment Options

### GitHub Pages (free, easiest)

1. Create a repo (e.g. `links` or `theleoborges.github.io`)
2. Push `index.html` to the `main` branch
3. Settings → Pages → Source: `main` / `/ (root)` → Save
4. Point a custom domain (e.g. `links.leo.wtf`) via CNAME

### Netlify (free)

1. Drag-and-drop the folder at [app.netlify.com/drop](https://app.netlify.com/drop)
2. Set custom domain in site settings

### Cloudflare Pages (free)

1. Connect repo or direct upload
2. No build command needed, publish directory: `/`

### This VPS with Caddy

```bash
# Install caddy if needed
sudo apt install -y caddy

# Example Caddyfile for links.leo.wtf
sudo tee /etc/caddy/Caddyfile << 'EOF'
links.leo.wtf {
    root * /home/ubuntu/.openclaw/workspace/linktree
    file_server
    encode gzip
    header Cache-Control "public, max-age=3600"
}
EOF

sudo systemctl reload caddy
```

### Nginx (alternative)

```nginx
server {
    listen 80;
    server_name links.leo.wtf;
    root /home/ubuntu/.openclaw/workspace/linktree;
    index index.html;
    gzip on;
    gzip_types text/html text/css application/javascript;
}
```

## Custom Domain

Point a DNS A record (or CNAME) to wherever you host it. All the free hosts above support custom domains with automatic HTTPS.
