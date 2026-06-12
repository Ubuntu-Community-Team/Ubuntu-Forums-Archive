---
title: "Can Windows see Ubuntu Partition ?"
date: 2005-08-16
forum: General Help
---

### Post by diffuser78 on 2005-08-16
Hello,

I have a dual boot with Win XP and Ubuntu .

Is there a way that we can access Ubuntu files from Windows ?

Please help,

Thanks

---

### Post by jasmuz on 2005-08-16
Windows can't natively read Ext3 partitions but there is a little program called explore2fs that will allow you to export files from the Ext3 partition to your NTFS partition.

Link: [http://uranus.it.swin.edu.au/~jn/linux/](http://uranus.it.swin.edu.au/~jn/linux/)

Hope this helps

---

### Post by izmaelis on 2005-08-16
[QUOTE=jasmuz]...export files from the Ext3 partition to your NTFS partition.[/QUOTE]
I think that you can export files from the Ext3 partition to your FAT32 partition too. What I want to say is that destination partition can have any filesystem type supported by MS Windows OS.

---

### Post by TiMBuS on 2005-08-16
explore2fs is okay, but theres a driver that lets you mount ext2 and 3 in windows, allows for read and write, but its a bit dodgey on ext3. can cause errors on ext3 but its just great for ext2.

Its called Ext2Fsd, get it at [http://ext2.yeah.net](http://ext2.yeah.net)

---

### Post by diffuser78 on 2005-08-16
Thanks guys, I will try as I go home !!!

---

