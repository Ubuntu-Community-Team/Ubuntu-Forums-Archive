---
title: "GRUB won't go to newly installed Kubuntu 23.10"
date: 2024-04-27
forum: General Help
---

### Post by oygle on 2024-04-27
I have a Lenovo running Windows 10 with a SSD. Installed Kubuntu 23.10 on an EXTERNAL SSD attached to the Lenovo. The first time I attempted the install, there were fatal GRUB errors. Installed again and all seemed well.

But it either boot to Windows 10 or if I interupt the boot , it drops to a GRUB prompt. Can't get it to boot to Kubuntu, even if I drop to BIOS and force a boot to that device. Exit BIOS, then I see the GRUB prompt again.

Tried ```
ls
```

> (proc)(memdisk)(hd0)(hd0,gpt4)(hd0,gpt3)(hd0,gpt2)(hd0,gpt1) 

A ```
ls -l
``` showed those partitions as NTFS and FAT which is probably the Windows 10 SSD, not the external SSD with the fresh Kubuntu 23.10

---

### Post by oygle on 2024-04-27
Looked in the BIOS. The external SSD is connected via a Thunderbolt port. Oh, I had to enable any USB devices on that port. Rebooted and went into Kubuntu now. Now, can I get back and boot to Windows if need be ...hahaha

---

