---
title: "Grub error 17 after resizing ext3 partition with Gparted from Ubuntu 7.10 Live CD"
date: 2007-12-22
forum: General Help
---

### Post by zhouxing on 2007-12-22
I have a duel-boot of Microsoft Windows Media Center edition on driver C (/dev/sda1) and Ubuntu 7.10 on the the last sectors of my 100GB harddisk. My Laptop is DELL Insprion 9300.

During installation of Ubuntu 7.10, I give only 8GB for it and it soons turns to be insufficient.

I therefore resized (increased) the ext3 partition of Ubuntu 7.10 from 8GB to 18GB by using Gparted from Ubuntu 7.10 Live CD.

However, after I rebooted, the Grub error 17 appears. Now I am stuck. I could not log in to either Windows or Ubuntu.

I searched forums for a while and tried some solutions but did not work.

The result of fdisk -ul is listed below:

=============================================
Disk /dev/sda: 100.0 GB, 100030242816 bytes
255 heads, 63 sectors/track, 12161 cylinders, total 195371568 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x92fc5002

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63    36869174    18434556    7  HPFS/NTFS
/dev/sda2        36869175   195366464    79248645    f  W95 Ext'd (LBA)
/dev/sda5        36869238    77834924    20482843+   7  HPFS/NTFS
/dev/sda6        77834988   118800674    20482843+   7  HPFS/NTFS
/dev/sda7       118800738   154384649    17791956    7  HPFS/NTFS
/dev/sda8       156023343   195366464    19671561   83  Linux
/dev/sda9       154384713   156023279      819283+  82  Linux swap / Solaris

Partition table entries are not in disk order
=============================================

/dev/sda8 is my Ubuntu 7.10 ext3 partition, /dev/sda9 is Swap. /dev/sda1 is the Windows partition.

The menu.lst in Grub is listed below:

===============================
title		Ubuntu 7.10, kernel 2.6.22-14-generic
root		(hd0,8)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=b4b363d6-7060-43d4-b345-fd2725183dc2 ro quiet nosplash locale=zh_CN
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

title		Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root		(hd0,8)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=b4b363d6-7060-43d4-b345-fd2725183dc2 ro single
initrd		/boot/initrd.img-2.6.22-14-generic

title		Ubuntu 7.10, memtest86+
root		(hd0,8)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Windows XP Media Center Edition
root		(hd0,0)
savedefault
makeactive
chainloader	+1
===============================

The result of df -h is as follows:

===============================
Filesystem            Size  Used Avail Use% Mounted on
tmpfs                 506M   16M  491M   3% /lib/modules/2.6.22-14-generic/volatile
tmpfs                 506M   16M  491M   3% /lib/modules/2.6.22-14-generic/volatile
varrun                506M   92K  506M   1% /var/run
varlock               506M     0  506M   0% /var/lock
udev                  506M   92K  506M   1% /dev
devshm                506M     0  506M   0% /dev/shm
tmpfs                 506M  356K  506M   1% /tmp
/dev/sda5              20G  8.0G   12G  41% /media/SOFTWARE
/dev/sda8              19G  7.9G   11G  44% /media/disk
===============================

As it can be seen from above, the mount point for /dev/sda8 is /media/disk instead of /

I couldn't figure how to mount it as .

Anyone who can help will be greatly appreciated!

---

### Post by pyronaut on 2007-12-22
try changing the root=uuid..... to root =/dev/sda8 ..your partition... it might have changed the drive id and now grub cant recognize it 
booting from grub command line 
grub >root (hd0,0)
grub>kernel /boot/vmlinuz-2.6.22-14-generic root=/dev/sda8 ro single
grub> initrd /boot/initrd.img-2.6.22-14-generic
grub> boot

---

### Post by zhouxing on 2007-12-22
i tried above method. still got Grub error 17 after reboot.

---

### Post by meierfra on 2007-12-22
Ubuntu is on /dev/sda8 which is (hd0,7). So you need to change all "root (hd0,8 )" in menu.lst to "root (hd0,7)".  Also change "groot (hd0,8 )" to "groot (hd0,7)". 

Edit: This  opens  "menu.lst" from the live cd:

```
mkdir ubuntu
sudo mount -t ext3 /dev/sda8 ubuntu
gksudo gedit ubtuntu/boot/grub/menu.lst
```

Finally you need to reinstall grub:

```
sudo grub
```

and at the "grub>" prompt:

```
root (hd0,7)
setup  (hd0)
quit
```

---

### Post by zhouxing on 2007-12-22
Great1 After change 0,8 to 0,7, it worked! Now I am back in my Ubuntu 7.10! Thanks a lot!

By the way, I have also removed UUID=...... stuffs from menu.lst and changed them to /dev/sda8.

---

