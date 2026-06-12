---
title: "RAID1, drive 1 failed, no grub on drive 2"
date: 2007-06-19
forum: General Help
---

### Post by Akegata on 2007-06-19
I installed 7.04 a few weeks ago on two drives that I configured as mirrors through the installation process.
Due to lack of time (and plenty of laziness), I never actually tried out how good md works in case of a drive failure. Now I have no choice though, because the first drive died last night.

The problem is that there simply is no grub installed on drive 2. Why would it not be installed on the secondary drive when the drives are mirrored? How do I remedy this problem, can I get grub installed on the secondary drive through booting from a LiveCD or something?

---

### Post by kidders on 2007-06-20
Hi there,

Depending on what sort of RAID you set up & where you installed your bootloader, this is what you'd expect. For instance, if you were to create two partitions (each on a separate disk), use mdadm to make a RAID array out of them, and install Grub into the MBR of one ... all quite normal stuff ... your bootloader would only be in one place.

If you wanted to, I suppose you could install bootloaders on *all* your hard disks, although I don't often bother, personally. Especially on multi-boot systems, bootloaders can break for all sorts of reasons ... as you mentioned, a LiveCD is often the easiest solution.

---

