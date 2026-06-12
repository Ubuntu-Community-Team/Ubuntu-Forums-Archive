---
title: "CUPS printing unsual stuff !!"
date: 2006-10-29
forum: General Help
---

### Post by tuxy on 2006-10-29
I have HP6210 Officejet printer connected to my desktop running on Ubuntu 6.06 desktop. I have networked it so that I can print from my laptop as well which is also running on Ubuntu 6.06. If I try to print anything from the laptop I get some strange unsual alpha numeric stuff printed out!!

I dont know whats the reason behind it? But it prints perfectly from the desktop which it is connected through USB cable. I tried everything by restarting both the PC's and also restrating the CUPS server on both ends and even removed the printer from the printer list and added again but no luck I get the same result.

I have attached the output of the print out in .PNG image format.
Any suggestions would be greatley appreciated.

---

### Post by tuxy on 2006-10-29
im still waiting any hints ?

---

### Post by tuxy on 2006-10-30
I figured it out! I found the solution from this post:
[http://www.ubuntuforums.org/showpost.php?p=1378794&postcount=12](http://www.ubuntuforums.org/showpost.php?p=1378794&postcount=12)

Hope this one helps some one :)

---

### Post by PaDV on 2006-11-13
This is a known bug in Dapper, see [https://launchpad.net/distros/ubuntu/+source/cupsys/+bug/55828](https://launchpad.net/distros/ubuntu/+source/cupsys/+bug/55828).

---

