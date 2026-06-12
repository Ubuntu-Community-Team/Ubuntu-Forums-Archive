---
title: "Boot install failed"
date: 2012-11-24
forum: General Help
---

### Post by asb3 on 2012-11-24
I've installed ubuntu on a new machine.  I have an asus P8z77-v LK motherboard, an intel 240G ssd, and a 2T hard drive.
When I installed ubuntu 12.10 from a DVD on the ssd, I got a "boot installation failed" error.  I then rebooted from the DVD and ran boot-repair, which appeared to be successful.   When I try to boot, it fails and prints
error: no such device: 79ff1c1a-d5b0-4264-699a-f113dcfd190b

Any suggestions?

---

### Post by asb3 on 2012-11-24
I posted this thread to the wrong forum.  Would a mod please move it to the Absolute Beginners forum.

---

### Post by beboylips on 2012-11-25
During installation, make sure you install Ubuntu on your primary hard drive (I'm guessing it's the SSD). Also try reinstalling the bootloader:

Restart from the Live DVD.
Select Try Ubuntu.
Open terminal

```

sudo grub-install /dev/sda

```

-Beboy

P.S. Reinstall the bootloader first, see what happens then.

---

### Post by asb3 on 2012-11-25
What determines which is the "primary hard  drive"?

---

### Post by asb3 on 2012-11-25
I disconnected the hard drive and successfully reinstalled ubuntu on the ssd.  I then reconnected the ssd and the machine booted correctly.

---

### Post by YannBuntu on 2012-11-26
Hi
Please the Thread tools to mark it [SOLVED]

---

