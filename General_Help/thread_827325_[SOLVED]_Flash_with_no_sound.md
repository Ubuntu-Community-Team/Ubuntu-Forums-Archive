---
title: "[SOLVED] Flash with no sound"
date: 2008-06-12
forum: General Help
---

### Post by yami280 on 2008-06-12
Ok i before my flash used to work on youtube and stuff.  but today it seems to not have anymore sound.  any solutions?

---

### Post by cernoch on 2008-06-12
I will probably be not much of help, but I noticed that this happened to me when proprietary adobe plugin and last.fm player were running at the same time.

I resorted to logout and login and it helped

---

### Post by plesset on 2008-06-12
After an onslaught of updates on my 8.04 for the last few days, something
finally gave - and it was the sound in FF3. After digging around here for
a few minutes without really finding anything helpful, I tried

sudo apt-get remove flashplugin-nonfree --purge
sudo apt-get install flashplugin-nonfree* libflashsupport

and got my sound back.

Hopfully this helps!

---

### Post by yami280 on 2008-06-12
Thanks it works now.

---

