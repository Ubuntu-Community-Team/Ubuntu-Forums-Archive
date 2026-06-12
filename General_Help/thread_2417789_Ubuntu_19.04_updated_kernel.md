---
title: "Ubuntu 19.04 updated kernel"
date: 2019-04-27
forum: General Help
---

### Post by jcmorris99 on 2019-04-27
Is there an updated version of 19.04? What I mean is there one that has the latest updates installed. Mostly looking for kernel. Ubuntu 18.10 installs fine and updated to 4.18 has no issues, going to the release 19.04 kernel 5 hates my computer as it goes into a loading loop. It starts doing 1 of 5 services and then just restarts after the 5 of 5. I tried Fedora 30 as well and there kernel 5 will load, but system gets kernel errors and sleep, shut down or restart will just hang. Going to 29 with 4.18 it's all good again. I'm for now using Ubuntu 18.10 with no issues and have no problems with it, I'm just trying them out for now by swapping a new 128 SSD in just to test. I have tried booting with onboard graphics, disabled sound card and disabled network. I've reset BIOS to defaults and updated. Using 3 different USB drives and even tried a 500 gig spindle hard drive, all ends the same. Thanks

Chris

---

### Post by Dennis N on 2019-04-27
A new install or upgrade to Ubuntu 19.04 still has the 4.18 kernel installed as a boot option. Use the Advanced Options at the grub menu. 

To check (shows output after my recent upgrade to 19.04):
```
dmn@Sydney-VM:/boot$ ls
config-4.18.0-17-generic      memtest86+.elf
config-5.0.0-13-generic       memtest86+_multiboot.bin
grub                          System.map-4.18.0-17-generic
initrd.img-4.18.0-17-generic  System.map-5.0.0-13-generic
initrd.img-5.0.0-13-generic   vmlinuz-4.18.0-17-generic
memtest86+.bin                vmlinuz-5.0.0-13-generic

```

Software updater tool will at some point try to update the 5.00-13 kernel. The autoremove would then remove the 4.18. You would need to determine how best to prevent that before allowing the kernel to upgrade. Ask if you need some suggestions.

Just thinking that if you are using the 4.18 kernel when you update, Software updater with autoremove would not remove the kernel in use. That would still allow new one to be installed for testing. Simple.

---

### Post by similar2 on 2019-04-27
Enabling "Proposed updates" will give you more options:

[https://wiki.ubuntu.com/Testing/EnableProposed](https://wiki.ubuntu.com/Testing/EnableProposed)

As of writing, the latest proposed kernel update in Ubuntu Disco is 5.0.0.14.15

---

### Post by jcmorris99 on 2019-04-29
Thank you all for the info I learned something. I'm going to try and load 19.04 on a new ssd and then boot 4.18 or .19 and then update the system and see what I get. I'll follow up when done. Thanks again.

---

### Post by antonivanov1 on 2019-05-26
Mine 19.04 kernel 5 is also unusable, and I have i7 CPU and 8Gb of RAM.

---

