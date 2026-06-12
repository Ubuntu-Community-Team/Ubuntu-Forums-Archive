---
title: "How do you reinstall grub?"
date: 2008-02-09
forum: General Help
---

### Post by keeler1 on 2008-02-09
How do I reinstall grub.

I recently installed ubuntu 6.10 on another partition of my machine which switched where grub was installed.  

Grub itself is still installed in the MBR, but all of the files it uses are on the 6.10 partition not my 7.10 partition.  

So essentially I just need to get grub to use the files on my 7.10 partition.

---

### Post by taurus on 2008-02-09
[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html)

or

[https://help.ubuntu.com/community/?action=fullsearch&context=180&value=grub&titlesearch=Titles](https://help.ubuntu.com/community/?action=fullsearch&context=180&value=grub&titlesearch=Titles)

---

### Post by sandysandy on 2008-02-09
post output of sudo fdisk -lu.

please explain the issue in more detail.

if its just a grub problem, maybe Super Grub Disk may help.

regards

---

