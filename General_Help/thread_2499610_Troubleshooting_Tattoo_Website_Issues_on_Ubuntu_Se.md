---
title: "Troubleshooting Tattoo Website Issues on Ubuntu Server"
date: 2024-08-03
forum: General Help
---

### Post by jimbrown11 on 2024-08-03
Hi everyone,
I recently launched a [tattoogaze.com]("https://tattoogaze.com/") website dedicated to tattoo art and design, hosted on an Ubuntu server, and I've encountered some issues that I hope to get help with.
Everything was working perfectly until I tried integrating some new features for a better user experience. The site includes a gallery of tattoo designs, and after adding a custom plugin for image display, I've noticed the following problems:

[LIST=1]
[*]**Slow Loading Times:** The pages with high-resolution tattoo images load much slower than before.
[*]**Image Rendering Issues:** Some images don't appear correctly on mobile devices, and others don't load at all.
[*]**SSL Conflict:** I initially set up SSL with Cloudflare, but after switching to DreamHost, their SSL was automatically installed. Could this be causing a conflict with image loading?
[/LIST]
I've been using Ubuntu 22.04 and Apache as my web server. If anyone has suggestions or has faced similar issues, I'd appreciate your insights!
Thanks in advance for any help you can provide!

---

### Post by euol on 2024-08-03
You can compress and use modern formats for images, enable browser caching through Apache's .htaccess file, and use a CDN for faster content delivery. Verify SSL configurations to avoid conflicts between Cloudflare and DreamHost, and clear any caches after changes. Check Apache logs for errors.

---

