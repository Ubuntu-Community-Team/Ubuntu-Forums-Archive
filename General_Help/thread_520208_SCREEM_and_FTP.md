---
title: "SCREEM and FTP"
date: 2007-08-07
forum: General Help
---

### Post by Pitt Stains on 2007-08-07
I'm trying to give SCREEM a try as my IDE for web-based projects and it looks OK to me so far, but I am having a hard time figuring out how to connect to my remote site. For it to be any kind of useful to me, I need to be able to browse files on the remote server, and download/upload files from within the app.

I am used to Dreamweaver in Windoze, where I can view local files and remote files side by side. SCREEM either doesn't do anything like this or I haven't been able to figure it out. Anyone have any luck with this?

By the way, SCREEM is not a WYSIWYG editor, nor am I looking for one.

---

### Post by Pitt Stains on 2007-08-10
Ba-bump!

---

### Post by David A Knight on 2007-08-11
If you are working with individual files, forget it from within screem, just open the site in nautilus and copy the files.

If you are working on a site with screem set up the ftp details in the site settings, then let the upload wizard do all the work of keeping the remote site in sync (Tools->Upload)

Screem only supports updating the remote site to keep it in sync with the local copy, it doesn't let you copy files from remote to local.

---

