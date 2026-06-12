---
title: "Unable to boot, boot-repair doesn't suggests any repairs"
date: 2018-10-09
forum: General Help
---

### Post by pelegs on 2018-10-09
Somehow grub does not recognize my Ubuntu partition (I don't have any other system installed), giving me the following error:
> Gave up waiting for root device. Common problems:
 - Boot args (cat /proc/cmdline)
   - Check rootdelay= (did the system wait long enough?)
   - Check root= (did the system wait for the right device?)
 - Missing modules (cat /proc/modules; ls /dev)
ALERT! /dev/disk/by-uuid/<<uuid>> does not exist. Dropping to a shell!

Using a live-usb, I ran fdisk -l, which showed only the usb partitions (sda1 and sda2).

Boot-repair didn't suggest any solution. This is its log:
[http://paste.ubuntu.com/p/9PrZzpDQbC/](http://paste.ubuntu.com/p/9PrZzpDQbC/)

Perhaps my hard-drive is physically disconnected? I rather check more stuff before I open my laptop...

---

### Post by oldfred on 2018-10-09
Script does not fully show NVMe drives.
But the parts that normally show NVMe partitions are not showing anything.

Turn off UEFI Secure Boot.
Does UEFI show NVMe drive? Or did settings get changed to RAID or Intel SRT, drive needs to be in AHCI mode.

---

### Post by pelegs on 2018-10-10
Turned off UEFI Secure Boot, changed settings to AHCI. It now boots normally into my system.
Thanks!

---

