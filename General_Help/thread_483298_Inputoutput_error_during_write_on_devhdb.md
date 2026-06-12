---
title: "Input/output error during write on /dev/hdb"
date: 2007-06-24
forum: General Help
---

### Post by rvb on 2007-06-24
I connected an external USB harddrive to my computer. Then I ejected it and later turned off the computer. Next day when I start the computer I get "Error 29: Disk write error" after choosing Ubuntu in GRUB. I got the same when choosing Windows XP. Reset BIOS to defaults, now I got to the Ubuntu splash screen showing how it's loading but then it turned black and several messages about I/O, sectors and ext3 (don't remember exactly what). I used the Windows XP disc to do fixmbr which allowed me to use XP again, there I deleted the partition containing Ubuntu and the swap partition. Rebooted to install Ubuntu again, but when I'm at the partitioning part and choose 'yes' to save the changes I *still* get this error:

"Input/output error during write on /dev/hb
ERROR!!!"

Someone at #ubuntu told me he had a similar problem after connecting an external USB harddrive and said that it had somehow messed up the order in GRUB and that I should press 'e' in GRUB to somehow change it back. However I don't have GRUB installed anymore and I'm not able to install Ubuntu so what do I do now? I'm using version 7.04

---

### Post by rvb on 2007-06-25
I tried the windows xp cs's fixboot which fixes the boot sector and fixmbr again which fixes the master boot record but I still get the same message when trying to install. Anyone have any idea whatsoever how this can be solved?

---

### Post by reed026 on 2007-06-25
Is the external harddrive still connected to your System?

If it isn't it looks like ubuntu is attempting to install to the external drive when there isn't one connected.

---

### Post by rvb on 2007-06-25
No it's not. It was only connected a short time.

---

### Post by rvb on 2007-06-25
I tried installing Debian now and this is what I got at the partition part:

"Input/output error during read on /dev/ide/host0/bus0/target1/lun0/disc
ERROR !!!"

I've already done fixboot and fixmbr with a windows disc, I tried reformatting the drive through both the ubuntu and debian discs, nothing works.

---

### Post by rvb on 2007-06-26
I did dmesg and got several: "end_request: I/O error, dev hdb, sector" and then a number. There were lots of 0 and 8 and a few 74252424

---

### Post by rvb on 2007-06-26
I just formatted the whole drive with the Windows XP cd and reinstalled Windows XP on it but I *still* get that message when trying to partition the drive with the ubuntu or debian cd's. I also loaded fail-safe defaults (instead of optimized defaults which I chose before) on BIOS but that didn't change anything. 

Any ideas on where the problem is? Any at all?

---

