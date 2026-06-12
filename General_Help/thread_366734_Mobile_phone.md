---
title: "Mobile phone"
date: 2007-02-21
forum: General Help
---

### Post by zapper on 2007-02-21
Hi,
I have a samsung X700 cellphone which I connected with my computer. The machine is detecting the device as is shown by dmesg and ```
lsusb -v

  iProduct                2 SAMSUNG Mobile USB Modem


```
However I do not know where and how to mount it.. what file system to use etc. Or how to copy file from and to the device. Please help...

Thank you.

---

### Post by taurus on 2007-02-21
What's the output of this command from a terminal?

```
sudo fdisk -l
```

---

### Post by zapper on 2007-02-21
Disk /dev/hda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1               1        1950    15663343+  83  Linux
/dev/hda2            1951        9696    62219745   83  Linux
/dev/hda3            9697        9729      265072+  82  Linux swap / Solaris
/dev/hda4            9730        9730           0+  83  Linux

---

