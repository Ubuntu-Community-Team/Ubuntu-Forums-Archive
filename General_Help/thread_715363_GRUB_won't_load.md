---
title: "GRUB won't load"
date: 2008-03-04
forum: General Help
---

### Post by lizard_b on 2008-03-04
I'm having trouble getting one of my hard disks to boot with ubuntu 7.1.

I did a clean whole-disk guided install with 7.1 on hda.

Booting directly to that disk results in getting to "Loading GRUB..." and no change even after a long time.

I also copied the menu.lst entry from hda (which is readable when booted from another disk) to the menu.lst for hdb, which has a functional dapper drake install.  Booting to GRUB on hdb and using that menu entry results in GRUB telling me "file not found".

I don't really know how to start troubleshooting this.  It's not the /etc/usplash.conf issue.  e2fsck reports no problems.


Below is my fdisk -l
```

Disk /dev/hda: 20.4 GB, 20419854336 bytes
255 heads, 63 sectors/track, 2482 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        2373    19061091   83  Linux
/dev/hda2            2374        2482      875542+   5  Extended
/dev/hda5            2374        2482      875511   82  Linux swap / Solaris

Disk /dev/hdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1        1216     9765625   83  Linux
/dev/hdb2            1216        1338      976562+  82  Linux swap / Solaris
/dev/hdb3            1338        9279    63787109   83  Linux

Disk /dev/hdd: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdd1   *           1        1275    10241437   83  Linux
/dev/hdd2            1276        1403     1028160   82  Linux swap / Solaris
/dev/hdd3            1404        4865    27808515   83  Linux

```

Below is my fstab
```

# Pluggable devices are handled by uDev, they are not in fstab
/dev/hdb1 / ext3 defaults,noatime 1 1
/dev/hdb2 swap swap sw,pri=1 0 0
none /proc proc defaults 0 0
none /proc/bus/usb usbfs devmode=0666 0 0
none /dev/pts devpts mode=0622 0 0
none /sys sysfs defaults 0 0
/dev/hdb3 /home ext3 defaults,noatime 1 2
/dev/hda1 /mnt/hda1 ext3 defaults,noatime 1 2
# Dynamic entries below, identified by 'users' option
/dev/hda5 swap swap sw,pri=1 0 0
/dev/hdd1 /mnt/hdd1 ext3 noauto,users,exec 0 0
/dev/hdd2 swap swap sw,pri=1 0 0
/dev/hdd3 /mnt/hdd3 ext3 noauto,users,exec 0 0
/dev/cdrom /media/cdrom iso9660,udf noauto,users,exec,ro 0 0
/dev/fd0 /media/floppy vfat,ext2 noauto,users,exec,rw 0 0
```

Below is the menu.lst entry (that does not work)

```
title		Ubuntu 7.10, kernel 2.6.22-14-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=173d600a-f62c-4035-98d6-b9ad45717bea ro quiet splash
initrd		/boot/initrd.img-2.6.22-14-generic
quiet
```

---

### Post by pointone on 2008-03-04
If that fstab is from the system you have GRUB installed on, then your menu.lst needs to point to "root (hd1,0)".

(hd0,0) is /dev/hda1 on your system. (hd1,0) is /dev/hdb1.

You can't just switch menu.lst's around like that, especially between different versions of Ubuntu. The menu.lst you posted is looking for kernel version 2.6.22-14, which I'm certain is much later than the kernel available in Dapper.

I'd recommend simply reinstalling GRUB from scratch.

You only need one install of GRUB, really. No need to install GRUB on every single Linux system you have installed.

---

### Post by lizard_b on 2008-03-05
That menu.lst entry is the one trying to boot to the fresh install on hda1.  There is another entry for my dapper drake install on hdb1, which is perfectly functional.  Telling my bios to boot first to hdb, GRUB there loads, and can boot the kernel on hdb1.  It cannot boot the kernel located on hda1, which is the problem that I am trying to solve.  Alternatively, telling my bios to boot first to hda, GRUB there does not completely start.

---

### Post by logos34 on 2008-03-05
> **lizard_b said:**
> That menu.lst entry is the one trying to boot to the fresh install on hda1.  There is another entry for my dapper drake install on hdb1, which is perfectly functional.  Telling my bios to boot first to hdb, GRUB there loads, and can boot the kernel on hdb1.  It cannot boot the kernel located on hda1, which is the problem that I am trying to solve.  Alternatively, telling my bios to boot first to hda, GRUB there does not completely start.

Like the guy above said, you only need one grub--either add gutsy entry to dapper menu.lst and boot from hdb, or add dapper to gusty menu.lst and try reinstalling grub the the MBR of hda (set the bios to boot hda and then [follow this]("http://ubuntuforums.org/showthread.php?t=224351")).

---

### Post by lizard_b on 2008-03-05
> add gutsy entry to dapper menu.lst and boot from hdb, or add dapper to gusty menu.lst 

Is there a reason why doing both is not working?  Currently, the gusty menu.lst entry is on both hda and hdb.  Should trying to boot hda directly really not work because there is another copy of GRUB on hdb?

I will attempt the gentoo repair procedure in your link since that seems to have the closest symptoms to my pc.

---

### Post by logos34 on 2008-03-05
> **lizard_b said:**
> Is there a reason why doing both is not working?  Currently, the gusty menu.lst entry is on both hda and hdb.  Should trying to boot hda directly really not work because there is another copy of GRUB on hdb?

In theory you should be able to boot to either hda or b and have the option of gutsy or dapper kernel, you just need to get the root line correct and install grub to each drive's MBR pointing to the correct menu.lst. It's just that it's needlessly complicated that way.

If you're booting hdb (dapper), then the Gutsy entry in that menu.lst needs to be (as pointone said) '(hd1,0)'--i.e if gutsy is second in the Bios boot order:

> [QUOTE]title		Ubuntu 7.10, kernel 2.6.22-14-generic
root		(hd[COLOR="Red"]**1**[/COLOR],0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=173d600a-f62c-4035-98d6-b9ad45717bea ro quiet splash
initrd		/boot/initrd.img-2.6.22-14-generic
quiet[/QUOTE]

Similarly, if you're booting to hda (gutsy) and hdb is second in the bios order, then the dapper entry in the gutsy menu.lst needs to also read 'root (hd1,0)'

---

