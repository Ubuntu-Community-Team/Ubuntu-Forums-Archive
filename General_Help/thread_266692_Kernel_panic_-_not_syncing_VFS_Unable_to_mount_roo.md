---
title: "Kernel panic - not syncing: VFS: Unable to mount root fs on unknown-block(0,0)"
date: 2006-09-27
forum: General Help
---

### Post by SheeEttin on 2006-09-27
For some reason, I am unable to boot automatically with GRUB (Error 17), so I am forced to do it manually. This is not the problem (yet). The problem is that when I attempt to boot using the commands
```
root (hd0,0)
kernel /vmlinuz ro root=/dev/hda0
boot
```
the kernel loads, and then panics with the topic error. Two other messages I get immediately before the panic are:
```
VFS: Cannot open root device "hda0" or unknown-block(0,0)
Please append a correct "root=" boot option

```
Other topics I have read say to specify something about in initrd command, but I don't know if this is the problem, and if it is, I don't know what to specify.

I have only one hard drive, on it two partitions, the first e2fs, the second swap. I am also unable to boot from CD, for some reason, so that's out; even though the BIOS indicates it is booting from CD, GRUB loads. (GRUB then returns an Error 17.)

The OS is actually Kubuntu, but that shouldn't matter--should it?

---

### Post by kaplis on 2006-09-27
i had the kernel panic with RAM disk. maybe at the startup using GRUB menu run some RECOVERY mode and then update your system:-k

---

