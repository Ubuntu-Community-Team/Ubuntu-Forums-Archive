---
title: "Renamed External USB HD - Does Not Mount Anymore"
date: 2007-12-17
forum: General Help
---

### Post by OffHand on 2007-12-17
Hi Guys,

 I have renamed my external USB HD and now it does not mount anymore. Please check the screenshot for error message. The file system is vfat. Generic name was My Book. I tried to rename it to MyBook. 


Thanks in advance!

---

### Post by vanadium on 2007-12-17
How did you rename?

---

### Post by OffHand on 2007-12-17
> **vanadium said:**
> How did you rename?

Right click > Properties > Change mount point to /media/MyBook

---

### Post by OffHand on 2007-12-17
Also tried to fix it using this post: [http://ubuntuforums.org/showpost.php?p=897856&postcount=10](http://ubuntuforums.org/showpost.php?p=897856&postcount=10)

Output is:

xxx@ubuntu-lap:~$ mcd i:
xxx@ubuntu-lap:~$ sudo mlabel -s i:
 Volume label is MyBook (abbr=MYBOOK     )
xxx@ubuntu-lap:~$ sudo mlabel i:My Book
Mtools version 3.9.10, dated March 2nd, 2005
Usage: mlabel [-vscVn] [-N serial] drive:
xxx@ubuntu-lap:~$ sudo mlabel i:My_Book
xxx@ubuntu-lap:~$ sudo mlabel -s i:
 Volume label is My_Book (abbr=MY_BOOK    )

---

### Post by vanadium on 2007-12-17
Yet another victim of this Ubuntu useability bug: go back to that dialog, change /media/MyBook into MyBook and your drive will happily mount again thereafter.

---

### Post by OffHand on 2007-12-17
> **vanadium said:**
> Yet another victim of this Ubuntu useability bug: go back to that dialog, change /media/MyBook into MyBook and your drive will happily mount again thereafter.

Can't change it back if it doesn't mount anymore  :s

I took it to work and formatted it with a mac... windows cannot even format it to fat32 anymore.

---

### Post by vanadium on 2007-12-17
Isn't the icon there in Places - Computer if the drive is not mounted? If that does not help, then change the volume label. At that point, Ubuntu will think it is another drive and mount it under the same name as your volume label.

---

### Post by OffHand on 2007-12-17
> **vanadium said:**
> Isn't the icon there in Places - Computer if the drive is not mounted? If that does not help, then change the volume label. At that point, Ubuntu will think it is another drive and mount it under the same name as your volume label.

I wouldn't know if that would have fixed it and there is no way to test it anymore. I left it at work doing a low level format. Anyways - I consider this a bug so I might make a report.

---

### Post by vanadium on 2007-12-18
It is indeed a useability issue woth filing (if it hasn't already been): the dialog suggests that you could enter a path (mount point), and in fact allows you to enter a pad, while you may not: you just should enter a label. Anyway, it is always better to control the naming through the drives label instead of through Places - Computer: that way you are sure your drive will be mounted with the same name on an other system or after an upgrade.

---

