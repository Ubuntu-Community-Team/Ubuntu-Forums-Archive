---
title: "Image resizer shell script?"
date: 2008-05-08
forum: General Help
---

### Post by lackofcreativity on 2008-05-08
I use the Gimp to resize all my images by 4%, then save them to my desktop. Is it possible to make a shell script to do this?

---

### Post by p_quarles on 2008-05-08
The "convert" utility in the Imagemagick suite (included in an Ubuntu base installation) does this.

---

### Post by chrisccoulson on 2008-05-08
Also note that there is a Nautilus extension (nautilus-image-converter) which can resize multiple images at once by selecting them in the file browser.

---

### Post by mardawi on 2008-05-08
> **chrisccoulson said:**
> Also note that there is a Nautilus extension (nautilus-image-converter) which can resize multiple images at once by selecting them in the file browser.
nice! didn't know that.

---

### Post by mankygitt on 2008-05-08
You might also want to check out "MailPictures" perl script by Guillaume Tissier (razerraz-AT-free.fr)

This is a nice perl script you add to your scripts folder to enable right-click functions in Nautilus.
It has a nice GUI which allows you to set your preferences, and output to a filespace, or fire up evolution and attach the new sized images.

[http://www.grumz.net/?q=search/node/MailPictures&PHPSESSID=5b30d0bc6dfbee6c7fb4d70a1277f85b](http://www.grumz.net/?q=search/node/MailPictures&PHPSESSID=5b30d0bc6dfbee6c7fb4d70a1277f85b)
Note, you probably will need to install/configure nautilus-actions for this. I dont recall whether I did or not, it was some time ago, but it works very well.

Regards
Manky

---

### Post by lackofcreativity on 2008-05-10
Thanks all!

---

