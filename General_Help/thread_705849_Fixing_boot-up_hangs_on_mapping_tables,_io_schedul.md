---
title: "Fixing boot-up hangs on mapping tables, io scheduler, or checking initramfs"
date: 2008-02-23
forum: General Help
---

### Post by DingsBumps on 2008-02-23
My boot used to hang on "Mapping tables up to 1200000000@10000000". If I disabled quiet in the boot options, it would hang on either "io scheduler cfq registered (default)" or "checking if image is initramfs". 

I went through a lot of trouble and found a lot of answers. People suggested putting in many combinations of 
```
noapic
noacpi
acpi=off
nosplash
acpi=no

```
and many more. None of them worked for me. If you are reading this, it may be worthwhile to try putting those into your boot options. However, what did it for me was disabling USB keyboard and USB mouse support in my mobo's bios. All that means is that I now can't use my kb and mouse before the OS loads, for example to select a boot option in grub. 

If your boot is hanging on any of the lines I mentioned before, take a minute and try disable some form of USB support in your mobo, because that was the simple solution to my (seemingly) very complicated problem.

---

