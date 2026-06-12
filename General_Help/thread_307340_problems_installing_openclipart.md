---
title: "problems installing openclipart"
date: 2006-11-26
forum: General Help
---

### Post by BlueStreak on 2006-11-26
I tried installing openclipart via synaptic and it failed because it was unable to fetch some files from the server.  Now I seem to be stuck in a vortex.  This is a little hard to explain but when I try to do anything with apt-get I receive errors relating to openclipart even if the package I'm working with has nothing to do with it.

For example, I tried to apt-get remove denemo (a guitar tab package that I don't want anymore) and I got the following error:

(Reading database ... dpkg: error processing denemo (--remove):
 files list file for package `openclipart-png' contains empty filename

I try to remove openclipart and get the same type of error and reinstallation also fails

It seems like the system thinks it's installed but really it's only partially installed.  I hope this post makes some sense, I'm really not sure how to explain it

---

### Post by halfvolle melk on 2006-11-26
Try
```
sudo apt-get install -f
```
It may fix the issue or it may give a usefull error message. In the later case please post it here.

---

### Post by BlueStreak on 2006-11-26
I tried that and no luck.  It didn't fix the issue but didn't give any error messages either.

At this point I don't care if clipart is installed or not.  It's just that it appears to be installed in synaptic yet I can't remove it or reinstall it without getting that error.  I'm at a loss

---

### Post by BlueStreak on 2006-11-26
If it's of any use, this is the exact error I get when attempting to reinstall clipart via synaptic:

E: /var/cache/apt/archives/openclipart-png_0.18+dfsg-4_all.deb: files list file for package `openclipart-png' contains empty filename

---

