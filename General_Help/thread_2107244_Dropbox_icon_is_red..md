---
title: "Dropbox icon is red."
date: 2013-01-21
forum: General Help
---

### Post by gabo.cr on 2013-01-21
Hi,

I changed my desktop from Unity to Gnome. But now the Dropbox icon is red. I believe I installed this application manually last year. I created a folder and is not syncing. I do have the Internet working. I'm not sure if this is related to Gnome, but I think is a big coincidence that it happened as soon as I switched.

Should I remove the application from the Synaptic Manager and reinstall ?

I don't want to loose my files and having to sync again, I have about 4Gb in documents.

(screen-shot attached)

Any suggestions ?

---

### Post by LewisTM on 2013-01-21
You should completely reinstall Dropbox. Just removing it from Synaptic won't do much since the program is actually downloaded for each user during the first logon/linking process.

First quit Dropbox from the indicator menu. Then run these commands in a terminal:
```
rm -rf .dropbox .dropbox-dist
dropbox start -i
```
You should now be prompted to log onto Dropbox and link your computer. It will merge with your existing Dropbox folder, sync and index everything. You shouldn't lose anything but if you do remember you can undelete everything from the web interface.

Cheers!

---

### Post by gabo.cr on 2013-01-21
I had to reboot the computer and Dropbox is working again.

I will keep those commands at hand anyways.

Thank You !

---

