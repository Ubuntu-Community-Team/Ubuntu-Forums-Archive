---
title: "Some problems: Hibernation among other stuff"
date: 2007-12-29
forum: General Help
---

### Post by Knoll318 on 2007-12-29
I think I installed Wubi onto a dedicated partition, but I still don't have Hibernate, even though I could on Windows.  Also, is there any way I can check if Wubi is on a partiton?  In addition, my NTFS partition has a flag that says they can't find the bootpoint, but everything works fine.  What's going on?

---

### Post by tylerspaska on 2007-12-30
i'm not sure what you mean by installing wubi onto a dedicated partition. everytime i have installed it, the program has made a ext3 folder on a windows partition (fat32 or ntfs). i'm not sure if writing to a dedicated partition would really do anything different than the standard installation. also, if you have a separate partition already, why don't you just install there using conventional methods?

is there anyway to check the partition? if it boots, then it is in it's ext3 folder and should be on its own pseudo-partition (because it's really just a folder)

as for the bootpoint, i have no idea, sorry.

---

### Post by Knoll318 on 2007-12-30
Thanks for trying.

The Partition thig is so I can Hibernate and have not penalty on my disk speed.

I want to know if I have it on a separate partiton because I read if you upgrade Wubi Feisty ot Wubi Gutsy, then weird things happen.  As such, I want to upgrade.

---

### Post by ago on 2007-12-30
cat /proc/mounts

look for the line that is mounted onto /, if it uses loopfiles then you are not on a dedicated device.

---

### Post by Knoll318 on 2007-12-30
rootfs / rootfs rw 0 0
none /sys sysfs rw,nosuid,nodev,noexec 0 0
none /proc proc rw,nosuid,nodev,noexec 0 0
udev /dev tmpfs rw 0 0
/dev/disk/by-uuid/953c2a3b-7d1d-44d9-844d-237cda634eca / ext3 rw,data=ordered 0 0
/dev/disk/by-uuid/953c2a3b-7d1d-44d9-844d-237cda634eca /dev/.static/dev ext3 rw,data=ordered 0 0
tmpfs /var/run tmpfs rw,nosuid,nodev,noexec 0 0
tmpfs /var/lock tmpfs rw,nosuid,nodev,noexec 0 0
tmpfs /lib/modules/2.6.20-15-generic/volatile tmpfs rw 0 0
tmpfs /dev/shm tmpfs rw 0 0
devpts /dev/pts devpts rw 0 0
usbfs /dev/bus/usb/.usbfs usbfs rw 0 0
udev /proc/bus/usb tmpfs rw 0 0
usbfs /proc/bus/usb/.usbfs usbfs rw 0 0
fusectl /sys/fs/fuse/connections fusectl rw 0 0
tmpfs /var/run tmpfs rw,nosuid,nodev,noexec 0 0
tmpfs /var/lock tmpfs rw,nosuid,nodev,noexec 0 0
/dev/disk/by-uuid/C828BDFBCC5D389D /media/host0 fuseblk rw,nosuid,nodev,noatime,user_id=0,group_id=0,allow_other 0 0
binfmt_misc /proc/sys/fs/binfmt_misc binfmt_misc rw 0 0
/dev/sde2 /media/SAMI'S\040IPOD vfat rw,nosuid,nodev,uid=1000,fmask=0077,dmask=0077,codepage=cp437,iocharset=iso8859-1,shortname=mixed,utf8 0 0

Can you make sense of that?

---

### Post by ago on 2008-01-01
yes you are on a dedicated partition

---

### Post by Knoll318 on 2008-01-01
Thanks.  I also kida figured that out when I still had Ubuntu after I uninstalled Wubi.

---

