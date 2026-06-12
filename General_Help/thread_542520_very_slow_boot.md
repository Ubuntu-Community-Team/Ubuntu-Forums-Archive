---
title: "very slow boot"
date: 2007-09-04
forum: General Help
---

### Post by atlfalcons866 on 2007-09-04
My computer is taking forever to boot up. It stalls for 4 Mintues for the 1st part of the loading area. then it is normal speed after that. I found out that it is taking forever for it to mount my cd drive. I disabled my cd drive in the bios. It went normal speed with it disabled. The cd drive is not defective as i just used it to reinstall ubuntu. 
Here my fstab

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=ada3360a-c0cf-4b14-8602-2abe1ffaa109 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda2
UUID=0c356031-e2fd-45f6-a073-b1da75ec9b78 /home           ext3    defaults        0       2
# /dev/sda3
UUID=1615ca10-b91e-41b2-b67f-8a6ead7abad2 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0

and 

jack@jack-desktop:~$ cat /etc/mtab
/dev/sda1 / ext3 rw,errors=remount-ro 0 0
proc /proc proc rw,noexec,nosuid,nodev 0 0
/sys /sys sysfs rw,noexec,nosuid,nodev 0 0
varrun /var/run tmpfs rw,noexec,nosuid,nodev,mode=0755 0 0
varlock /var/lock tmpfs rw,noexec,nosuid,nodev,mode=1777 0 0
procbususb /proc/bus/usb usbfs rw 0 0
udev /dev tmpfs rw,mode=0755 0 0
devshm /dev/shm tmpfs rw 0 0
devpts /dev/pts devpts rw,gid=5,mode=620 0 0
lrm /lib/modules/2.6.20-16-generic/volatile tmpfs rw 0 0
/dev/sda2 /home ext3 rw 0 0
binfmt_misc /proc/sys/fs/binfmt_misc binfmt_misc rw 0 0
jack@jack-desktop:~$

---

