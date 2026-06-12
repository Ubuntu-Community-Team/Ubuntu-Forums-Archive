---
title: "mdadm issues... system will not boot (not even close)"
date: 2007-05-06
forum: General Help
---

### Post by Stormx on 2007-05-06
Hokay. First up, a little context. Copied my ubuntu partitions (/, /home, swap) to another hard drive. Reconfigured grub, which is now on the new disk. Grub loads, and finds the stuff in /boot. I've rejigged the menu.lst, which allows me to boot from my new ubuntu partition. Well, it doesn't really... it starts okay.

Then, I get this, after "Loading, please wait..."

> 
mdadm: No devices listed in conf file were found
  Check root= bootarg cat /proc/cmdline
  or missing modules, devices: cat /proc/modules ls /dev
ALERT! /dev/disk/by-uuid/(some hex here) does not exist. Dropping to a shell!

BusyBox (some details of version here).....

/bin/sh: can't access tty; job control turned off
(initramfs) _

Here is my fstab:
> 
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hdb2 -- converted during upgrade to edgy
# UUID=46dd796a-aa07-409d-ae01-d5997bddc8b5 / ext3 defaults,errors=remount-ro 0 1
/dev/hda6 / defaults,errors=remount-ro 0 1
# /dev/hdb6 -- converted during upgrade to edgy
# UUID=e4446c88-cd0a-45ad-ad5c-33e0c667c77c /home ext3 defaults 0 2
/dev/hda7 /home ext3 defaults 0 2
# /dev/hdb1 -- converted during upgrade to edgy
# UUID=0000-0D63 /media/Music vfat defaults,utf8,umask=0000 0 0
# /dev/hda1 -- converted during upgrade to edgy
# UUID=08D81C2ED81C1D0E /media/WinXP ntfs-3g defaults,locale=en_US.utf8 0 0
# /dev/hda5 -- converted during upgrade to edgy
# UUID=44A6-9501 /media/Stuff vfat defaults,utf8,umask=000,gid=46 0 0
# /dev/hdb5 -- converted during upgrade to edgy
# UUID=877b03b7-86f4-4377-be33-0ee827cfb63d none swap sw 0 0
/dev/hda5 none swap sw 0 0
# /dev/hdd        /media/cdrom0   udf,iso9660 user,noauto     0       0


Note that I have commented out the original lines and replaced them without the uuids - as I figured the uuids would be invalid (the new partitions are on a new disk and are larger)

Finally, my system is 1.4ghz 32bit / 768mb RAM. I have access to an ubuntu 6.06 live CD, and can boot windows. I can burn any additional cds and boot from them, if need be. As my /home is on another partition, a reinstall isn't out of the question.

Oh, and when I attach the original hdd as a slave, ubuntu boots... but I'm not sure what is mounted where (whether / is the original, or the new partition, copied from the original).

Suggestions?

---

