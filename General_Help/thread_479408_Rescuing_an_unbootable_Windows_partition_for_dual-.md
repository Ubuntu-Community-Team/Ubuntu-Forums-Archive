---
title: "Rescuing an unbootable Windows partition for dual-boot"
date: 2007-06-20
forum: General Help
---

### Post by Zedison on 2007-06-20
So here's the story: After installing Ubuntu for the first time on a drive that was formatted with a single Windows XP NTFS partition, Windows became unbootable. GRUB was automatically set up with a boot option, but when I use it, it says "starting up..." and does absolutely nothing afterwards. No disk activity, no error messages, no nothing.
Others have said that using Windows Recovery Console's "fixmbr" command worked for them, but when I try it, it just kills GRUB, leaving me with a screen that says "disk boot error, press ctrl+alt+del to restart" and a peculiar four-color text pattern shaped oddly like the Windows logo. This is also what happens when I attempt to reinstall Windows.

The partition is still quite readable. The data is still there, it just won't boot. During the resizing process, I got an error warning, which I'm told is a rare but idiotic bug wherein the partition is somehow mounted while also being adjusted, resulting in an improper setup which can cause this situation.

To provide a little better basis for troubleshooting, here's the contents of GRUB's menu.lst file:
```
title		Ubuntu, kernel 2.6.20-16-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=8992b4c3-0537-4546-9543-e2ebb8c814f1 ro quiet splash
initrd		/boot/initrd.img-2.6.20-16-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-16-generic (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=8992b4c3-0537-4546-9543-e2ebb8c814f1 ro single
initrd		/boot/initrd.img-2.6.20-16-generic

title		Ubuntu, kernel 2.6.20-15-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=8992b4c3-0537-4546-9543-e2ebb8c814f1 ro quiet splash
initrd		/boot/initrd.img-2.6.20-15-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-15-generic (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=8992b4c3-0537-4546-9543-e2ebb8c814f1 ro single
initrd		/boot/initrd.img-2.6.20-15-generic

title		Ubuntu, memtest86+
root		(hd0,1)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Windows NT/2000/XP (loader)
root		(hd0,0)
savedefault
makeactive
chainloader	+1

```

And here's the result of fdisk -l:
```

Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       22403   179952066    7  HPFS/NTFS
/dev/sda2           22404       38535   129580290   83  Linux
/dev/sda3           38536       38913     3036285    5  Extended
/dev/sda5           38536       38913     3036253+  82  Linux swap / Solaris
```

---

### Post by Twigathy on 2007-07-03
I'm currently having the same problem. I've got /boot on /dev/sda1 and windows on /dev/sda2, my grub menu.lst's windows entry is:

```

title WinXP Pro SP2
rootnoverify (hd0, 1)
savedefault
makeactive
chainloader +1

```

...but when booting windows seems to get to "Starting up..." and then does nothing at all.

Help very much appreciated

Twig

---

