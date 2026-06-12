---
title: "Grub not loading"
date: 2018-05-19
forum: General Help
---

### Post by xceptone on 2018-05-19
Mornings all,
It's another 'grub not loading on a dual boot system' question.

So  far I've changed UEFI BIOS settings, re-installed Ubuntu 18.04, ran boot  repair after an installed via Live USB and still I can't get grub to  load.

Fast boot and secure boot are both disabled.

The machine I'm using if interested is a MSI GT72-2QE.

The  W10 partition is running fine and loads as default. Only way I can get  into my Ubuntu side is via the boot select option via BIOS.
I can provide a boot repair report but that's long winded but still.
What else can I try?

---

### Post by oldfred on 2018-05-19
You can post the link to the Summary report that Boot-Repair gives.

But issues may be similar to these, not sure if 18.04 is any different?
 MSi GT72VR-6RE Dominator Pro - some settings required
[https://ubuntuforums.org/showthread.php?t=2365997](https://ubuntuforums.org/showthread.php?t=2365997)
Failing to Boot Ubuntu 16.10 in MSI GP72
[http://askubuntu.com/questions/838212/failing-to-boot-ubuntu-16-10-in-msi-gp72](http://askubuntu.com/questions/838212/failing-to-boot-ubuntu-16-10-in-msi-gp72)
[SOLVED] MSI GT72S 6QE - Freezes on boot unless acpi=off is used
[http://ubuntuforums.org/showthread.php?t=2303544](http://ubuntuforums.org/showthread.php?t=2303544)
MSI GS60 2QE 2xSSD RAID 0 + 1TB HDD dual boot w8.1/w10 problem 
[http://ubuntuforums.org/showthread.php?t=2297815](http://ubuntuforums.org/showthread.php?t=2297815)

---

### Post by yancek on 2018-05-19
Did you read the official Ubuntu documentation at the link below before installing?

[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

If you can boot Ubuntu or windows from the BIOS boot options, then you probably just need to set Ubuntu first with efibootmgr.  Posting the boot repair output will help.

---

### Post by shanasman450 on 2018-05-19
I have the same issue but reversed. I get no grub and it boots straight to ubuntu.

---

### Post by oldrocker99 on 2018-05-19
I discovered, after a lot of frustration, that, when I booted in UEFI mode, grub would always fail to install. I finally got smart and booted it legacy, and all was well.

---

### Post by xceptone on 2018-05-20
Resolving it, apparently doing a boot repair for the x'th amount of time fixed it, Grub now loads!

---

