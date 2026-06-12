---
title: "GRUB Question?"
date: 2007-02-14
forum: General Help
---

### Post by U2X001 on 2007-02-14
Hi! I just finished installing ubuntu 6.10 on my Sony VAIO VGN-FS21B my laptop has some kind of disk space protected on it's hard disk that if ever my windows on my C:\ be formatted and you accessed the recovery back up on my hard disk return my laptop from it's original installation.

Now my question is how can I prevent GRUB from listing that recovery space for my laptop, i don't want it to be deleted i just want it not to be displayed and also I have an english version of XP installed on my laptop since the the first XP is in japanese.

My GRUB list look like this:

Ubuntu
Windows XP (this is the recovery that i don't want to be listed in case somene used it)
Windows XP (Has a little problem because if you select this this will bring you to another OS Selection by windows w/c is the japanes and the english version)

if possible i want to list the two OS to GRUB directly and not listing the recovery.

Hope you could help me thanks!

---

### Post by Mba7eth on 2007-02-14
Easy :D
```
$sudo nano /boot/grub/menu.list
```

find the line you want it to be hidden, add only # in front it to make it a comment. And in the future you can just get it back by removing the #.
Enjoy \\:D/

---

