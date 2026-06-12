---
title: "Live CD - why no flash support?"
date: 2007-12-11
forum: General Help
---

### Post by Packrat1947 on 2007-12-11
I use two distros; Ubuntu 7.10 and PClinuxOS.  Ubuntu lacks support, but the other has support, and even Youtube plays fine.

I found this out while solving a "Youtube no-sound" problem in a customer's XP box.  I did eventually solve the no-sound problem.

Just wondering what the issue is.  

Also, over there on the PClinuxOS side, they don't have full ntfs capabiliites.

---

### Post by ruibernardo on 2007-12-11
Hi Packrat1947,

due to the questionable legality of redistributing adobes flash player (not even Windows have it installed - PCLinuxOS do it don't know why) and propriety codecs, Ubuntu doesn't install them and/or have them enabled. You have flash in the browser (EDIT: Ubuntu Gutsy comes with an opensource alternative - gnash - installed by default), but you don't have the codecs to see videos for example.

Look at this thread to enable multimedia in Ubuntu - [Enabling Multimedia in Feisty (HOW-TO)]("http://ubuntuforums.org/showthread.php?t=413625") - or this webpage -  [https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats).

---

