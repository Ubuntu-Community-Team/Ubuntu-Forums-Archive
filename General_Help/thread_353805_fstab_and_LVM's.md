---
title: "fstab and LVM's"
date: 2007-02-05
forum: General Help
---

### Post by Trapper on 2007-02-05
I have an IDE1 primary with FC6 and Win2k. I added a secondary IDE1 and put Ubuntu 6.10 on it. I allowed Ubuntu to write to the mbr of hd0 and am booting using Ubuntu's grub. I added my FC6 and Win2K to grub and I can boot to all.

PROBLEM:

I want to mount  FC6 for access when I boot into Ubuntu. I edited my fstab for my Win2K partitions okay but am unable to get FC6 partitions to mount. I know why I am having this difficulty. I just do not know how to reasonably resolve it. My FC6 is an LVM setup. I am not considering changing that. I either find a way to mount my FC6 / partition or perhaps I reinstall Ubuntu with LVM. (???) Whatever, I hopefully find a way to mount FC6 / under the current scenario, if possible.

Here's my current Ubuntu fstab:

proc            /proc           proc    defaults        0       0
# /dev/hdb1
UUID=2c2aaf08-c62c-4009-bf58-809642b9859f /               ext3    defaults,errors=remount-ro 0       1
# /dev/hdb5
UUID=53d3cbfd-5500-4699-ab4f-f95ab90618ea none            swap    sw              0       0
/dev/hdd        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/           /media/floppy0  auto    rw,user,noauto  0       0
/dev/hda1               /mnt/Drive_C             vfat    auto,users,rw,umask=0 0 0 0 0
/dev/hda5               /mnt/Drive_D             vfat    auto,users,rw,umask=0 0 0 0 0
/dev/hda6               /mnt/Drive_E             vfat    auto,users,rw,umask=0 0 0 0 0
/dev/hda7               /mnt/Drive_F             vfat    auto,users,rw,umask=0 0 0 0 0


Here's my FC6 fstab:

/dev/VolGroup00/LogVol00 /                       ext3    defaults        1 1
LABEL=/boot             /boot                   ext3    defaults        1 2
devpts                  /dev/pts                devpts  gid=5,mode=620  0 0
tmpfs                   /dev/shm                tmpfs   defaults        0 0
proc                    /proc                   proc    defaults        0 0
sysfs                   /sys                    sysfs   defaults        0 0
/dev/VolGroup00/LogVol01 swap                    swap    defaults        0 0
/dev/hda1               /mnt/Drive_C             vfat    auto,users,rw,umask=0 0 0 0 0
/dev/hda5               /mnt/Drive_D             vfat    auto,users,rw,umask=0 0 0 0 0
/dev/hda6               /mnt/Drive_E             vfat    auto,users,rw,umask=0 0 0 0 0
/dev/hda7               /mnt/Drive_F             vfat    auto,users,rw,umask=0 0 0 0 0
/dev/hdb1               /Ubuntu                 ext3    defaults    0 0

Accessing Ubuntu from FC6 goes well. I just want to do the opposite and access FC6 from Ubuntu. Can I do it?

---

### Post by talowe on 2007-02-05
> **Trapper said:**
> I have an IDE1 primary with FC6 and Win2k. I added a secondary IDE1 and put Ubuntu 6.10 on it. I allowed Ubuntu to write to the mbr of hd0 and am booting using Ubuntu's grub. I added my FC6 and Win2K to grub and I can boot to all.

PROBLEM:

I want to mount  FC6 for access when I boot into Ubuntu. I edited my fstab for my Win2K partitions okay but am unable to get FC6 partitions to mount. I know why I am having this difficulty. I just do not know how to reasonably resolve it. My FC6 is an LVM setup. I am not considering changing that. I either find a way to mount my FC6 / partition or perhaps I reinstall Ubuntu with LVM. (???) Whatever, I hopefully find a way to mount FC6 / under the current scenario, if possible.

Here's my current Ubuntu fstab:

proc            /proc           proc    defaults        0       0
# /dev/hdb1
UUID=2c2aaf08-c62c-4009-bf58-809642b9859f /               ext3    defaults,errors=remount-ro 0       1
# /dev/hdb5
UUID=53d3cbfd-5500-4699-ab4f-f95ab90618ea none            swap    sw              0       0
/dev/hdd        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/           /media/floppy0  auto    rw,user,noauto  0       0
/dev/hda1               /mnt/Drive_C             vfat    auto,users,rw,umask=0 0 0 0 0
/dev/hda5               /mnt/Drive_D             vfat    auto,users,rw,umask=0 0 0 0 0
/dev/hda6               /mnt/Drive_E             vfat    auto,users,rw,umask=0 0 0 0 0
/dev/hda7               /mnt/Drive_F             vfat    auto,users,rw,umask=0 0 0 0 0


Here's my FC6 fstab:

/dev/VolGroup00/LogVol00 /                       ext3    defaults        1 1
LABEL=/boot             /boot                   ext3    defaults        1 2
devpts                  /dev/pts                devpts  gid=5,mode=620  0 0
tmpfs                   /dev/shm                tmpfs   defaults        0 0
proc                    /proc                   proc    defaults        0 0
sysfs                   /sys                    sysfs   defaults        0 0
/dev/VolGroup00/LogVol01 swap                    swap    defaults        0 0
/dev/hda1               /mnt/Drive_C             vfat    auto,users,rw,umask=0 0 0 0 0
/dev/hda5               /mnt/Drive_D             vfat    auto,users,rw,umask=0 0 0 0 0
/dev/hda6               /mnt/Drive_E             vfat    auto,users,rw,umask=0 0 0 0 0
/dev/hda7               /mnt/Drive_F             vfat    auto,users,rw,umask=0 0 0 0 0
/dev/hdb1               /Ubuntu                 ext3    defaults    0 0

Accessing Ubuntu from FC6 goes well. I just want to do the opposite and access FC6 from Ubuntu. Can I do it?

ubuntu seems to install evms  by default, look for /dev/evms/VolGroup00/LogVol00 or something very similar to mount.

.../LogVol01 should be able to be used as swap for both systems, saving some space.

---

### Post by Trapper on 2007-02-06
> **talowe said:**
> ubuntu seems to install evms  by default, look for /dev/evms/VolGroup00/LogVol00 or something very similar to mount.

.../LogVol01 should be able to be used as swap for both systems, saving some space.

Thanks for the reply but I had already moved on to a different strategy by the time it was posted. I simply copied everything of importance from my FC6 install onto Ubuntu and simply wiped my FC6 drive, partitioned that portion of hd0 without LVM, reinstalled FC6, moved all my personal stuff back to FC6 from the Ubuntu storage and installed grub to the MBR from the FC6 install. It didn't give me the correct parameters to boot from Ubuntu so I took Ubuntu's menu.lst and used it as FC6's grub.conf. I edited in the grub info from the FC6 grub for FC6 and Win2K. 

Shortened up for posting it looks like this:

title           Fedora Core (2.6.19-1.2895.fc6)
root            (hd0,2)
kernel          /boot/vmlinuz-2.6.19-1.2895.fc6 ro root=LABEL=/ rhgb quiet
initrd          /boot/initrd-2.6.19-1.2895.fc6.img
savedefault
boot

title           Fedora Core (2.6.18-1.2798.fc6)
root            (hd0,2)
kernel          /boot/vmlinuz-2.6.18-1.2798.fc6 ro root=LABEL=/ rhgb quiet
initrd          /boot/initrd-2.6.18-1.2798.fc6.img
boot

title		Ubuntu, kernel 2.6.17-10-generic
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.17-10-generic root=/dev/hdb1 ro quiet splash
initrd		/boot/initrd.img-2.6.17-10-generic
quiet
boot

title		Ubuntu, kernel 2.6.17-10-generic (recovery mode)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.17-10-generic root=/dev/hdb1 ro single
initrd		/boot/initrd.img-2.6.17-10-generic
boot

title		Ubuntu, memtest86+
root		(hd1,0)
kernel		/boot/memtest86+.bin
quiet
boot

title		Microsoft Windows 2000 Professional
root		(hd0,0)
makeactive
chainloader	+1


I adjusted the FC6 and Ubuntu fstab's and now can access both nix flavors and win2k from either nix.

I'll probably just stay away from default FC installs and LVM until there comes a time when and if I really need LVM. I don't foresee that happening anytime soon.

I appreciate your input. I will retain your comments and probably try what you suggested on an old test box that I have, eventually

Trapper

---

