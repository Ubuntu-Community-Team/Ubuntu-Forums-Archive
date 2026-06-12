---
title: "latest samba update (16.05.07) = broken package ?"
date: 2007-05-16
forum: General Help
---

### Post by scotty64 on 2007-05-16
The updatemanager asked me to update three files today - all samba related. During the installation process I got the following error and samba is listed as "broken" now:

E: samba: subprocess pre-removal script returned error exit status 102

I tried to remove samba and install again, but I am  getting the same error when synaptic tries to uninstall samba.

---

### Post by kaamos on 2007-05-16
Just a guess: make sure that samba is running (sudo /etc/init.d/samba restart) before starting the upgrade/uninstall.

---

### Post by scotty64 on 2007-05-16
Solved the problem myself, but it is still odd:
trying to remove the pakage with dpkg -r samba gave a "dangling symlink" error and indeed there was a symlink in /etc/rc2.d named S91samba but pointing to /samba. :confused: :confused: :confused: 
I think switching services off in gnome service control panel is creating these odd symlinks.
Deleting the link and running dpkg again safely removed samba.

---

