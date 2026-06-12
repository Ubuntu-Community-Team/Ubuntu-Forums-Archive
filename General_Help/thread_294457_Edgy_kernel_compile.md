---
title: "Edgy kernel compile"
date: 2006-11-06
forum: General Help
---

### Post by JeffElkins on 2006-11-06
I'm trying to resolve a problem with mounting an 60GB Photo iPod under Edgy; multiple IO errors...

the iPodLinux wiki gave this advice:

```

 #fdisk /dev/sda (or whichever device ipod should be)
  Unable to read /dev/sda
 #dmesg | grep sda
  sda: I/O error: dev 00:00, sector 78126040 (or something along these
lines)

To fix this, you will have to recompile your kernel without EFI support.
When building the kernel, set CONFIG_EFI_PARTITION=n.
```

I downloaded the kernel sources and recompiled,using the config*generic parameters from /boot, but am butting heads with initrd; VFS kernel panic when I reboot. I installed yaird, and built a new image, but no joy. Do I even _need_ an initrd image? I'm not running SCSI drives or anything exotic. I'd appreciate any help in resolving this.

Thanks!

---

