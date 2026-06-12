---
title: "Kubuntu doesn't boot anymore!"
date: 2007-02-19
forum: General Help
---

### Post by Tosa on 2007-02-19
Edgy+KDE were working just fine for a couple of days... Then it froze on shut down and I switched the computer off. On the next boot bios complained that keyboard was not present. That happened with Dapper too, after a crash, on reboot my usb keyboard wasn't detected. Fortunately, I have my old PS/2 keyboard that solved the problem in Dapper.
But not in Edgy... The Kubuntu splash screen would show up, but the progress bar wouldn't show any progress. After some 10-15 seconds of nothing happening I get the black screen saying:

[B]/bin/sh: can't access tty; job control turned off
(initramfs)[/B]

I have no idea what is going on... Help!

---

### Post by alyoung on 2007-02-19
Sounds like a hardware issue, possibly motherboard-based, but it would be better to get a second opinion.

---

### Post by Tosa on 2007-02-19
Thanks, maybe you're right.
But maybe I wasn't clear enough...
The problem with keyboard in Dapper was happening only after a crash shutdown. And it was only with usb keyboard. I would connect PS/2 and boot would continue normally, and usb keyboard would start functioning too... But now, I get stuck with both keyboards working!

---

### Post by bettlebrox on 2007-02-19
Did you upgrade to a new kernel recently? Have you added or removed any partitions recently?

---

### Post by Tosa on 2007-02-19
Yes. I've tried booting in recovery mode and with previous kernels but got the same message... No I didn't make any changes to HD.

---

### Post by mgmiller on 2007-02-19
Try looking in your BIOS for an entry about "legacy USB" or some similar statement.  If it's enabled, disable it.  If its disabled, try enabling it.  Also, if you have any PCI cards in the system, try removing them all and then rebooting.  If it works, try adding them back in 1 at a time.  I have a USB/Firewire card that causes similar problems for me.  I get all kinds of error messages about starting RAID problems and other hardware issues, but the errors are all wrong.  It's a PCI bus mastering issue for me.

---

### Post by Tosa on 2007-02-19
Thanks, I've turned off legacy usb support, but no luck. I've removed pci cards and no luck either. Still stuck with the same message:
[B]/bin/sh: can't access tty; job control turned off
(initramfs)[/B]_
I haven't mentioned it before, but windows are working fine, including usb keyboard (I've been in windows since the problem appeared).

---

### Post by bettlebrox on 2007-02-20
Usually that means there is a problem the ramdisk. It's used to load modules (drivers). Maybe it got corrupted when the power went out? U could try booting with the live disk and see if you can reinstall the kernel.

---

### Post by Tosa on 2007-02-21
I think now everything is screwed up.
I did what was suggested here [https://launchpad.net/ubuntu/+source/initramfs-tools/+bug/67256](https://launchpad.net/ubuntu/+source/initramfs-tools/+bug/67256)
but after reboot all I got is ***Grub ERROR 15* **and a frozen computer.
I suppose that  *sudo update-grub* messed it up.

So, I've put in Edgy CD and was going to install it again. I've been doing that with windows all the time (one of the reasons I've switched to Linux)... But when it came to partitioning, Linux partition was reported as ext2, and I'm sure it was ext3. The best part is that it said the **27 GB partition has 431 GB** of occupied space!
Anyway, I clicked continue, and very soon the installer reported that it can't continue...
What are my options now?

---

