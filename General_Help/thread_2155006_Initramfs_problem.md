---
title: "Initramfs problem"
date: 2013-06-16
forum: General Help
---

### Post by mohammad alsharqi on 2013-06-16
Hi
I,d faced a problem with boot of ubuntu 10.04 that it is initramfs 
i'd attached a picture for this problem 
how disolve it pleas??

---

### Post by Cheesehead on 2013-06-18
Here is what is happening:

During boot, the bootloader mounts your disk read-only, loads the kernel, loads "init" (PID #1), and launches init.
Then init creates the filesystem (/dev, /sys, etc), unmounts the disk, remounts the disk read/write at the correct places in the filesystem, and then cleverly hands off control (while running) to the /sbin/init in the mounted filesystem.

Your init cannot remount the disk read/write. It's failing to find /sbin/init (because it could not mount the disk), and it has nothing to handoff to. So it gives up.

Did you do a recent kernel upgrade? Is this a fresh install? Did you make and changes or upgrades before it happened?
Is /sbin/init really in the target drive?


Config: The failure to remount might be due to a bootloader config. Check that first.

Physical Settings: If you are using a media with a read-only jumper or write-protect tab, it may be in the wrong (read-only) position.

Hardware: The failure might be due to a flaky/dying boot media or controller. For example, if you are mounting from an SD card, the SD reader might be dying, or the card may be going bad.

Hardware: The failure might be due to RAM corruption, though that's unlikely. Run memtest.

---

### Post by mohammad alsharqi on 2013-06-18
How to check bootloader pls

---

