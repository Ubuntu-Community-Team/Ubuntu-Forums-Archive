---
title: "How to Fix the Grub Error 18..."
date: 2008-05-26
forum: General Help
---

### Post by ricky_bains on 2008-05-26
freinds i was havin windows XP and SUSE 9 dual booting running successfully but after installing xbuntu 8.04 LTS I m stucked with this bootloader problem the  whole error is
[B]GRUB Loading Stage 1.5.

   GRUB Loading, Please wait
   Error 18[/B]

my partition table is :
Device Boot    Start       End    Blocks   Id  System
/dev/hdb1   *         1      1275  10241406    7  HPFS/NTFS
/dev/hdb2          1276      2550  10241437+   7  HPFS/NTFS
/dev/hdb3          2551      4865  18595237+   f  Win95 Ext'd (LBA)
/dev/hdb5          2551      2600    401593+  82  Linux swap
/dev/hdb6          2601      3906  10490413+  83  Linux
/dev/hdb7          3907      4161   2048256    b  Win95 FAT32
/dev/hdb8          4162      4865   5654848+  83  Linux

kindly help me
how can i fix this problem so that m able to boot properly again.


thanks
aman

---

### Post by Kevbert on 2008-05-26
Try a Super Grub disk.  It can be found here: [http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)

---

### Post by Gunman1982 on 2008-05-26
Read the part at the end.
[http://wiki.linuxquestions.org/wiki/GRUB]("http://wiki.linuxquestions.org/wiki/GRUB")

---

### Post by ricky_bains on 2008-05-26
> **Kevbert said:**
> Try a Super Grub disk.  It can be found here: [http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)

but i said it was working fine with windows XP and SUSE 9, problem came only when i installed xbuntu along with them(SUSE 9 and WIN XP)

---

### Post by ricky_bains on 2008-05-26
gunman1982 can you tell me how super grub disk works

---

### Post by Gunman1982 on 2008-05-26
Uh I never used super grub disk, sry. Did you read the post regarding the error on the wiki? Actually I don't know an easy solution to make Win+Suse+Ubuntu work. If I'm right SuSE still uses lilo boot loader? You could reinstall that one (best way to ask in a suse forum for that) and use that as the boot loader.

---

### Post by ricky_bains on 2008-05-26
have u ever used super grub disk Kevbert, if yes pls tell me how it works

---

### Post by ricky_bains on 2008-05-26
no SUSE 9 uses grub bootloader n t was workin fine before this xbuntu issue

---

### Post by Kevbert on 2008-05-26
Basically Super Grub will detect what operating systems you have and then rewrite your boot files at the start of the hard disk.  
You have error 18 by the look of it as you've possibly added a new hard disk to an old machine and the bios cannot see the xubuntu partition/boot files (which I assume is hdb8).
Documentation for Super Grub can be found here; [http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html]("http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html")

---

### Post by ricky_bains on 2008-05-27
thanks for your intrest friends

---

### Post by VMC on 2008-05-27
I've use Super Grub in the past. It is kind of difficult to explain straight away. There are a lot of text pages. It tries to take into account all grub issues. It has worked for me in the past, but I understand Grub a little better now and I only have one Linux installed.

I', assuming SUSE is here, on /dev/hdb6:
/dev/hdb6 2601 3906 10490413+ 83 Linux
And ubuntu is here , on /dev/hdb8:
/dev/hdb8 4162 4865 5654848+ 83 Linux

Is that right? Try and locate menu.lst . It's inside grub directory (/boot/grub/menu.lst)
You may have one inside both Suse and ubuntu partitions.

Is there any point that you can hit escape key when grub starts and edit it's menu?
If not try a rescue cd, like Puppy, rescuecd, and then find the menu.lst file.
You need that file, and it needs to be correct.

---

