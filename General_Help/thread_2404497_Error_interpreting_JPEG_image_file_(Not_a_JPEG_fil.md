---
title: "Error interpreting JPEG image file (Not a JPEG file: starts with 0x72 0x73)"
date: 2018-10-24
forum: General Help
---

### Post by nilandj-nilandsplace on 2018-10-24
I have in my Downloads folder a great many pictures in various file types/formats, GIF, JPG and PNG I can't view or open in any image viewer or editor. They are all about a year old And I am sure they where local backups/copies on my local machine or copied from another local (LAN) machine. All have similar errors like: ```
Error interpreting JPEG image file (Not a JPEG file: starts with 0x72 0x73)
``` and in the command line screen indicate file:```
file 10discountCoupon1.gif10discountCoupon1.gif: rdiff network-delta signature data (block length=512, signature strength=8)
```
or
```
file boker.jpgboker.jpg: rdiff network-delta signature data (block length=512, signature strength=8)
```


I get messages like "Fatal error reading PNG image file: Not a PNG file", File does not appear to be a GIF file, Error interpreting JPEG image file (Not a JPEG file: starts with 0x72 0x73)
I have tried PhotoRec, ImageMagick, Gimp, and renaming schemes. I also know I could previously open them. 

The only major change to the Ubuntu-server 14.04.5 was I uninstalled Virtualmin/webmin subscription, removed the LAMP-stack and reinstalled the GPL Version. I am using PHP5.6 version and I remember before the PHP version was also PHP5. Since I am redoing an Older Magento (M1) version I am sticking PHP5.6 even though PHP7.2 is available as it does not have Mcrypt for php (PHP5.6-mcrypt) needed by Magento 1.9.3.4 version

This "rdiff network-delta signature data" is beyond my understanding, so I don't know what it indicates. Would there be anything with it coming from a 32-bit machine? , that I dismiss anyway, because it had been years since I got rid of that box.

I don't know how to sort this out and it is far to many images to try to source again if I can even find them?

---

### Post by spjackson on 2018-10-27
All of those messages suggest that the files have been corrupted. You would need to recover from a backup, if you have one. I'm sorry that doesn't help much.

---

