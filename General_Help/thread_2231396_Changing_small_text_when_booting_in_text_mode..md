---
title: "Changing small text when booting in text mode."
date: 2014-06-25
forum: General Help
---

### Post by tubos2 on 2014-06-25
- I'm booting 14.04 LTS in text mode 
-The text font is very small to read.

Can I change this so it boots in a bigger text font / mode?
Maybe by adding a parameter in the /etc/default/grub file?

---

### Post by Gyokuro on 2014-06-25
Hi

It's already documented in the forums and check posting #7: [http://ubuntuforums.org/showthread.php?t=1542338](http://ubuntuforums.org/showthread.php?t=1542338) but make a backup of your files before you change anything.

- HTH

---

### Post by tubos2 on 2014-06-25
I used this to change the resolution :

GRUB_GFXMODE=640x480

It seems to work at first for the grub menu , but after linux boots and the messages go by
suddenly the displaymode is changed again to a small font text screen.

How Can i keep my chosen mode until the terminal login screen?

---

### Post by tubos2 on 2014-06-26
bump

---

### Post by tgalati4 on 2014-06-26
Try turning off video mode-setting.  Search for nomodeset.

---

