---
title: "hard drive speed info?"
date: 2008-06-27
forum: General Help
---

### Post by firsttimeuser on 2008-06-27
Hello guys, I am trying to figure out what is the hard disk RPM on this ubuntu box, any command I can use? Or do I need to install a specific software?

---

### Post by logos34 on 2008-06-27
I don't know of any command that shows rpm.  (dmidecode, hdparm, lshw)

try

sudo lshw -C disk

then google the make and model

Desktop drives are almost all 7200 rpm.  Laptops usually 5400, but some are 4200

---

