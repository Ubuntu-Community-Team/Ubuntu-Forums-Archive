---
title: "[SOLVED] Grub - Booting Windows"
date: 2008-05-17
forum: General Help
---

### Post by bsg007 on 2008-05-17
My grub entry for Windows doesn't seem to work. Anyone know what it should look like?

```

Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0001ec94

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       23060   185229418+  83  Linux
/dev/sda2           23061       36702   109579365   83  Linux
/dev/sda3   *       36703       38725    16249747+   7  HPFS/NTFS
/dev/sda4           38726       38913     1510110    5  Extended
/dev/sda5           38726       38913     1510078+  82  Linux swap / Solaris

```


```

title           Ubuntu 8.04, kernel 2.6.24-16-generic
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.24-16-generic root=UUID=1c878197-5f4c-483a-b3f5-23aba73510d9 ro quiet splash
initrd          /boot/initrd.img-2.6.24-16-generic
quiet

title           Ubuntu 8.04, kernel 2.6.24-16-generic (recovery mode)
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.24-16-generic root=UUID=1c878197-5f4c-483a-b3f5-23aba73510d9 ro single
initrd          /boot/initrd.img-2.6.24-16-generic

title           Ubuntu 8.04, memtest86+
root            (hd0,0)
kernel          /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

title Microsoft Windows XP
root (hd0,1)
makeactive
savedefault
map (hd0) (hd1)
map (hd1) (hd0)
chainloader +1


```

---

### Post by meierfra. on 2008-05-17
Open menu.lst via

```
gksudo gedit /boot/grub/menu.lst
```

and replace the windows entry by

title Microsoft Windows XP
root (hd0,2)
makeactive
savedefault
chainloader +1

---

### Post by bsg007 on 2008-05-17
That worked. Thanks.

---

