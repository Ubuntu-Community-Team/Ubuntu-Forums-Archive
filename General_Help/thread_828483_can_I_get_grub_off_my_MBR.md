---
title: "can I get grub off my MBR"
date: 2008-06-13
forum: General Help
---

### Post by Whizza on 2008-06-13
Hi, I installed (using default precedures) ubuntu 8.04 from a live cd, onto an external HD connected to my computer via USB. This seems to work fine except that now I must allways have this external drive switched on even if I want to just use windows. Could someone please tell me if there is any way of restoring my MBR with out losing my pre-existing internal drive partitions, while at the same time still being able to boot ubuntu via the USB when required, perhaps using just my BIOS settings.

Cheers

---

### Post by Whizza on 2008-06-13
can I get grub off my MBR 

--------------------------------------------------------------------------------

Hi, I installed (using default precedures) ubuntu 8.04 from a live cd, onto an external HD connected to my computer via USB. This seems to work fine except that now I must allways have this external drive switched on even if I want to just use windows. Could someone please tell me if there is any way of restoring my MBR with out losing my pre-existing internal drive partitions, while at the same time still being able to boot ubuntu via the USB when required, perhaps using just my BIOS settings.

Cheers

---

### Post by Bodsda on 2008-06-13
If you want to boot windows without the external hdd, then you will have to set the windows drive to the primary boot device in bios, then boot the windows recovery cd and at the recovery prompt type
```
fixmbr
```

To use the externel hdd's grub loader you will have to set it as primary boot device when needed

---

### Post by kansasnoob on 2008-06-13
It's a bit different depending on whether you're using XP or Vista.

---

### Post by TeoBigusGeekus on 2008-06-13
Give [supergrub]("http://www.supergrubdisk.org/") a look.

---

### Post by issih on 2008-06-13
Answer is it depends on your bios..

If it can boot from an external hard drive then yes you can.

To get rid of grub from the mbr of the internal drive, boot from a windows cd and enter recovery console, then type:

```
fixmbr
```

Alternatively download supergrub disk:

[http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)

which can also repair the windows bootloader for you.

In order to be able to boot ubuntu (assuming your bios can boot an external hd) you need to install grub into the mbr of the external hard drive.

To do this either redo the install completely, but on the last configuration page hit the advanced button and tell the installer to place grub onto the external disk's mbr, or if you want to avoid reinstalling, follow the instructions here under command line:

[https://help.ubuntu.com/community/GrubHowto#head-4c7a8640a439568ee312c9f262cc1099634f25ef](https://help.ubuntu.com/community/GrubHowto#head-4c7a8640a439568ee312c9f262cc1099634f25ef)

Once that is done you need to set your bios boot priority so that the external is tried ahead of the internal, ubuntu will then boot whenever you plugin the external hd

Hope that helps

---

### Post by Xiong Chiamiov on 2008-06-13
This is a cross-post of [here]("http://ubuntuforums.org/showthread.php?t=828483").

---

### Post by PmDematagoda on 2008-06-13
Whizza:- Please do not create duplicate threads on the same topic, just one thread in the proper section would be more than enough.

---

### Post by Whizza on 2008-06-13
No Worries. I'm kind of new to all this. This forum has been a great help.

cheers

---

