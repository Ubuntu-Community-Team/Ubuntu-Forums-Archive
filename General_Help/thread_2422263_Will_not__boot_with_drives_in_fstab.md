---
title: "Will not  boot with drives in fstab"
date: 2019-07-04
forum: General Help
---

### Post by dodot on 2019-07-04
I am using Ubuntu 19.04, clean install.
If I reboot or restart the machine it ends up at the emergency prompt.
If I log in and rem out all my drives in /etc/fstab, (not system drives) it will then boot to the desktop.
I then edit /etc/fstab, remove the rems 
then sudo mount -a 
and all my drives and network drives are mounted and accessible.

What extra steps does the system take on boot that does not happen with mount?
Also is this indicative of a deeper problem with my hard drives?

thanks

---

### Post by sisco311 on 2019-07-04
Please post the content of /etc/fstab.

---

### Post by oldfred on 2019-07-04
Are some drives external?
If so, they may not spin up (if HDD) as fast as boot?

Or network may not load before trying to mount network drive?

I have seen some threads where users had to create script & add it to end of boot process to get it to work. Did not save details or links, sorry.

---

### Post by dodot on 2019-07-04
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
/dev/mapper/ubuntu--vg-root /               ext4    errors=remount-ro 0       1
# /boot was on /dev/sda2 during installation
UUID=c26344a6-xxxx-424d-a1d3-d9a228e1b85f /boot           ext4    defaults        0       2
# /boot/efi was on /dev/sda1 during installation
UUID=FFF9-xxxx  /boot/efi       vfat    umask=0077      0       1
/dev/mapper/ubuntu--vg-swap_1 none            swap    sw              0       0
#
#my drives
UUID=d4b23cff-b64f-43b6-xxxx-aa4f28b10b4e  /media/dave/disk_1     auto defaults,errors=remount-ro 0       1
UUID=d8bce75d-7f86-410e-xxxx-198614b9f23f  /media/dave/disk_2     auto defaults,errors=remount-ro 0       1

#usb drives
UUID=cbbf4de8-xxxx-48fa-a886-390123c5a06b       /media/dave/usb_1     auto defaults,errors=remount-ro 0       1
UUID=8E5EDxxxxED35415                           /media/dave/usb_2     auto defaults,errors=remount-ro 0       1
UUID=54D8Dxxxx8D94ABE                           /media/dave/usb_3    auto defaults,errors=remount-ro 0       1
UUID=4349cfa4-xxxx-47c0-a993-9664b56c0074       /media/dave/usb_4     auto defaults,errors=remount-ro 0       1


#network shares
//192.168.1.xx/backup /mnt/nailgun/backup    auto vers=2.0,username=xxxxxxxxxx,password=xxxxxxxx 0 0


2 internal drives, 4 usb drive and a network drive

---

### Post by uRock on 2019-07-04
This is how my added drives look in fstab and everything works fine. Could it be something with the options you're using?

```
#   My Drives
#	Old Home
UUID=a731a653-a268-4de3-9f0f-0b907bc5dc5b /media/ronnie/Old\040Home ext4 rw,nosuid,nodev,relatime,data=ordered 0 0
#	Old Home
UUID=f8c923c0-2235-402a-88b2-704695678d46 /media/ronnie/Other\040Files ext4 rw,nosuid,nodev,relatime,data=ordered 0 0
```

---

### Post by oldfred on 2019-07-04
I have seen this:

       [https://help.ubuntu.com/community/Autofs](https://help.ubuntu.com/community/Autofs)
use autofs for any storage that isn't connected directly to the system with SAS, SATA, eSATA, or Infiniband connections

[https://ubuntuforums.org/showthread.php?t=2400094](https://ubuntuforums.org/showthread.php?t=2400094)

---

### Post by dodot on 2019-07-05
Thank you. Using autofs solved the problem

---

