---
title: "adding win to grub - help needed"
date: 2007-03-02
forum: General Help
---

### Post by f3nol on 2007-03-02
Hi everyone!

I've got Ubuntu and Win XP installed on 2 separate HDDs and so far switched beetwen them via BIOS, pressing Esc before booting. Can somebody help me to add windows to my grub and make my life bit easier?
Heres how my partitions are looking
```
Disk /dev/sda: 81.9 GB, 81964302336 bytes
255 heads, 63 sectors/track, 9964 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        5099    40957686    7  HPFS/NTFS
/dev/sda2            5100        9963    39070080    f  W95 Ext'd (LBA)
/dev/sda5            5100        8923    30716248+   7  HPFS/NTFS
/dev/sda6            8924        9963     8353768+   b  W95 FAT32

Disk /dev/hdc: 6448 MB, 6448619520 bytes
255 heads, 63 sectors/track, 784 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdc1   *           1         747     6000246   83  Linux
/dev/hdc2             748         784      297202+   5  Extended
/dev/hdc5             748         784      297171   82  Linux swap / Solaris

```

sda1 = winXP
hdc1 = Ubuntu

and my menu.lst

```
title		Ubuntu, kernel 2.6.17-11-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.17-11-generic root=/dev/hdc1 ro quiet splash
initrd		/boot/initrd.img-2.6.17-11-generic
quiet
savedefault
boot

title		Ubuntu, kernel 2.6.17-11-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.17-11-generic root=/dev/hdc1 ro single
initrd		/boot/initrd.img-2.6.17-11-generic
boot

title		Ubuntu, kernel 2.6.17-10-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.17-10-generic root=/dev/hdc1 ro quiet splash
initrd		/boot/initrd.img-2.6.17-10-generic
quiet
savedefault
boot

title		Ubuntu, kernel 2.6.17-10-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.17-10-generic root=/dev/hdc1 ro single
initrd		/boot/initrd.img-2.6.17-10-generic
boot

title		Ubuntu, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
quiet
boot

```

Thanks in advance for any help ):P

---

### Post by dcstar on 2007-03-02
> **f3nol said:**
> Hi everyone!

I've got Ubuntu and Win XP installed on 2 separate HDDs and so far switched beetwen them via BIOS, pressing Esc before booting. Can somebody help me to add windows to my grub and make my life bit easier?
Heres how my partitions are looking
```
Disk /dev/sda: 81.9 GB, 81964302336 bytes
255 heads, 63 sectors/track, 9964 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        5099    40957686    7  HPFS/NTFS
/dev/sda2            5100        9963    39070080    f  W95 Ext'd (LBA)
/dev/sda5            5100        8923    30716248+   7  HPFS/NTFS
/dev/sda6            8924        9963     8353768+   b  W95 FAT32

Disk /dev/hdc: 6448 MB, 6448619520 bytes
255 heads, 63 sectors/track, 784 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdc1   *           1         747     6000246   83  Linux
/dev/hdc2             748         784      297202+   5  Extended
/dev/hdc5             748         784      297171   82  Linux swap / Solaris

```

sda1 = winXP
hdc1 = Ubuntu
........
Thanks in advance for any help ):P

Here is the menu.lst code that boots Windows on my single drive system (on the first Partition - 0)

Your system will depend on how Grub identifies the drives - either (hd0,x) or (hd1,x) - where x is the partition number to boot (starting at 0).

Copy in the code and experiment to see what works for one partition, and if you get it going cut-and-paste for any others you want to boot.

```
# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title		Windows 95/98/Me
root		(hd0,0)
savedefault
makeactive
chainloader	+1
```

---

### Post by f3nol on 2007-03-03
Thanks dcstar, I'll try it as soon as I can.

---

