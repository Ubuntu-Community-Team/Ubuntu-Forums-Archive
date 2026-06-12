---
title: "adding additional linux boot entry into grub menu.lst"
date: 2008-05-20
forum: General Help
---

### Post by armandli on 2008-05-20
i am trying to add a newly installed fedora into my ubuntu grub boot list (after changing ubuntu grub as the main grub bootloader), but i'm facing some problems. my first try is basically copying the fedora 9's grub boot item into ubuntu grub menu.lst. it looks somthing like this:

```

title Fedora (2.6.25-14.fc9.i686)
	root (hd0,5)
	kernel /boot/vmlinuz-2.6.25-14.fc9.i686 ro root=UUID=7a94bc7e-9e15-4a06-ba25-57e2e1f95e11
	initrd /boot/initrd-2.6.25-14.fc9.i686.img

```

it doesn't work. the error message is:

> 
cannot open root device UUID=some serial


so second try, i changed it to:

```

title Fedora (2.6.25-14.fc9.i686)
	root (hd0,5)
	kernel /boot/vmlinuz-2.6.25-14.fc9.i686 ro root=/dev/sda6
	initrd /boot/initrd-2.6.25-14.fc9.i686.img

```

same error

third try, i removed the ro, still fails with same error

help :(

---

### Post by plucky on 2008-05-20
> cannot open root device UUID=some serial 

Boot into Ubuntu,

Open a terminal ```
sudo fdisk -l
``` that is lowercase L no a 1,and ```
ls -l /dev/disk/by-uuid
``` again a lowercase L not a 1.

Post back to forum.

---

### Post by armandli on 2008-05-21
here are the results of fdisk -l (note i lied, my fedora partition is in sda4, not sda7)

```

Disk /dev/sda: 100.0 GB, 100030242816 bytes
255 heads, 63 sectors/track, 12161 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0004f4f0

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        5392    43311208+   7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sda2            5393        8003    20972857+   7  HPFS/NTFS
/dev/sda3            8004       10810    22547227+   5  Extended
/dev/sda4           10811       12161    10851907+  83  Linux
/dev/sda5            9114        9635     4192933+  82  Linux swap / Solaris
/dev/sda6            9636       10810     9438156   83  Linux
/dev/sda7            8004        9113     8916012   83  Linux

```

here is the result from ls -l /dev/disk/by-uuid

```

total 0
lrwxrwxrwx 1 root root 10 2008-05-19 15:22 00f8a48d-5569-4473-bf60-66bc650a01c1 -> ../../sda5
lrwxrwxrwx 1 root root 10 2008-05-19 15:22 21E79ABB2CEB08A4 -> ../../sda2
lrwxrwxrwx 1 root root 10 2008-05-19 15:22 701C64311C63F090 -> ../../sda1
lrwxrwxrwx 1 root root 10 2008-05-19 15:22 75199422-9b98-402e-b437-c54a4569bd6c -> ../../sda6
lrwxrwxrwx 1 root root 10 2008-05-19 15:22 7a94bc7e-9e15-4a06-ba25-57e2e1f95e11 -> ../../sda4
lrwxrwxrwx 1 root root 10 2008-05-19 15:22 f49d29c8-366d-4a18-a155-c6f1ab3c437e -> ../../sda7

```

though the uuid does match the one i have posted previously for sda4...

---

### Post by plucky on 2008-05-21
> my fedora partition is in sda4


```
title Fedora (2.6.25-14.fc9.i686)
	[color=red]root (hd0,3)[/color]
	kernel /boot/vmlinuz-2.6.25-14.fc9.i686 ro root=UUID=7a94bc7e-9e15-4a06-ba25-57e2e1f95e11
	initrd /boot/initrd-2.6.25-14.fc9.i686.img
```

If your Fedora partition is on sda4 then the **root (hd0,5)** needs to be changed as highlighted above.

Good Luck

---

### Post by nooby on 2008-06-27
delete my post

---

