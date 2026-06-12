---
title: "Thinkpad E420 Boot Error initramfs"
date: 2016-02-18
forum: General Help
---

### Post by Redalien0304 on 2016-02-18
Got a Thinkpad E420, installed Ubuntu 14.04 Restarted i get this. had Win 7 on it same thing, so i removed win 7. Reinstalled Ubuntu 14.04 got same thing. Also did new Partition Record after deleting all partitions. Laptap has UEFI but is set boot from both UEFI & Legacy.

> "Gave up waiting for root device. Common problems:
- Boot args (cat /proc/cmdline) 
  - Check rootdelay= (did the system wait long enough?)
  - Check root= (did the system wait for the right device?)
- Missing modules (cat /proc/modules; ls /dev)
ALERT! /dev/disk/by-uuid/1fa5a004-f2cc-41af-9e6c-41f150fb4776 does not exist.

BusyBox v1.121.1 (Ubuntu 1:1.21.0-1ubuntu1) built-in shell (ash)
Enter `help` for  a list of built-in commands.

(initramfs)"

Any info is welcome
Thanks in advance.

---

### Post by Redalien0304 on 2016-02-20
Solved by using Ubuntu Startup USB Creator

---

