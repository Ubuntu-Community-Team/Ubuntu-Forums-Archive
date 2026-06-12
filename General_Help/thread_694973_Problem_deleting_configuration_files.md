---
title: "Problem deleting configuration files"
date: 2008-02-12
forum: General Help
---

### Post by lanruisen on 2008-02-12
I have a problem with both Listen and Banshee media players.
In listen I turned on the splash screen to see what it looks like and now it just crashes, so I uninstalled it and reinstalled but the problem persists, so I deleted the desktop configuration file and re-installed, but the problem is still there. The same thing with banshee, I wanted re=install and start over with a new library, but even after the configuration file is deleted all my songs still come back, i would just remove the song from the library manually, but i have far too many.

How can I get a clean install of these 2 programs and start from scratch.

Thanks in advance for the help.

I'm using Ubuntu 7.10

---

### Post by apetresc on 2008-02-12
Try using the --purge flag to apt-get remove. Like this:
```
sudo apt-get remove --purge banshee
```
Hope this helps :)

---

### Post by lanruisen on 2008-02-12
No, that didn't work. Listen still had my last.fm account registered and other preferences, and Banshee still has all my old library in it even after a purge and re-install.
Thanks for the help,though.

---

