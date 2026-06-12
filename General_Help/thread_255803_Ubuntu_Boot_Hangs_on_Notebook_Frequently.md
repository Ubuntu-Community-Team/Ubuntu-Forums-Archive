---
title: "Ubuntu Boot Hangs on Notebook Frequently"
date: 2006-09-12
forum: General Help
---

### Post by nullmind on 2006-09-12
We would like to start off by thanking everyone in the Ubuntu community for providing so much support to new users. I've been using Ubuntu for about 1 year now and have solved almost every issue I've ever had by asking around. I've been spreading Ubuntu like wildfire to everyone I know as a replacement for Windows XP when possible (for general school work and web development)

This post may seem a big long, but the reason for this is because the problems that have occured seem to be very hard to pin down.

My girlfriend and I installed Ubuntu Dapper Drake 6.06 on her notebook. The notebook in question has the following specs:

**CPU: **Turion 64 X2 ("dual core" x86-64)
**Memory: **1Gb (333MHz DDR SDRAM)
**Video: **GeForce 7700 (256Mb dedicated)

The bus used for the hard-drive is a SCSI interface mapping everything to /dev/sda, /dev/sda1, etc... (I'm unsure if that matters)

**The problem** is during the boot process ONLY. The system appears stable and works fine if it's booted. During the boot process it will hang on one either *Preparing Restricted Drivers*, *Loading Hardware Drivers*, or *Configuring Network Interface*. Attempting to CTRL+C to cancel these operations has no effect (even if you attept to do it immediately on the network interface configuration one) and hints that the system is either deadlocked or something.

This happens during the boot process MOST of the time, although randomly it will work and continue to boot fine. Once the system is up it runs stable. She has the Broadcom wireless working fine with the bcm43xx-fwcutter solution. Graphics aren't accelerated yet (glxinfo reports no support for anything) because she has yet to complicate the issue with the nvidia drivers or glx. (the overall goal is to run compiz!)

If the system is restarted this happens again. If the system hibernates it hibernates fine but may hang again on boot time.

Sound works perfectly and we have installed many packages and applications that have no problem.

A part of us has a feeling that there is some kind of IRQ conflict. Her BIOS is very useless and provides no configuration or information of any kind besides the boot sequence, and I know little about this type of configuration in Ubuntu/Linux.

If anyone **has any information** please let me know. We tried blacklisting the **agpgart** but it didn't help.

Be sure to message me on gtalk/jabber (**nullmind@gmail.com**) or **nullsmind** via AIM.

Thanks for your time,
Kris and Allie

---

### Post by nullmind on 2006-09-12
Bump?

---

### Post by peabody on 2006-09-13
Can you switch Virtual terminals via Alt+[F1-F5]?  If so it may be due to some weird type of timeout that's taking forever.  If not, your kernel is probably locking up due to badly supported hardware.  I wish I could offer better advice than that.

---

### Post by nullmind on 2006-09-20
We fixed this (so far) by adding the **noapic** option in the kernel boot command-line with GRUB. So far -- so good.

Cheers,
Kris

---

### Post by jbennet on 2006-09-20
my ancient thinkpad does this too i used to usenoapic and the irqpoll option but it turns out now that was due to the BIOS having a bad ACPI subsystem - a flash with the newest version fixed this.

---

