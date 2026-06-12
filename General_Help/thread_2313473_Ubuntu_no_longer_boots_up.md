---
title: "Ubuntu no longer boots up"
date: 2016-02-12
forum: General Help
---

### Post by starrtennis on 2016-02-12
[COLOR=#111111][FONT=Ubuntu]The wallpaper doesn't even load. The monitor indicates there is no input. There is some error on a black screen that disappears quickly, something like can't find dell sdd or something. It was working just 20 minutes ago. I installed some Mesa package, could it be a virus? I think Mesa has something to do with graphics. Maybe the drivers got messed up? I have two DVI outputs, I tried them both and neither work.[/FONT][/COLOR]

---

### Post by grahammechanical on 2016-02-12
Not enough information.

Hardware specification? Is there another OS on the machine? Is that loading correctly? Mesa is related to the open source video driver. Are you using the open source video driver or a proprietary video driver. How did you install this Mesa package? Do you see a motherboard splash screen? Do you get a Grub boot menu? Can you enter the Motherboard's BIOS/UEFI boot system.

From the little information that you have provided I would say that the first thing that you have to confirm is that you still have a working video adapter. Then, a working hard disk/SSD, whatever storage medium is used in that machine.

A lot has to happen before the wallpaper loads. Knowing if you can get to a login screen is useful information. If you can get to a login screen then the problem is unlikely to be with a video driver. So, where is this problem occurring? After the BIOS splash screen but before the Grub boot menu? Or after the boot menu but before the login screen? Or after the login screen?

Oh, and knowing which version of Ubuntu you have installed is also a useful bit of information.

Regards.

---

### Post by starrtennis on 2016-02-12
Dell inspiron 530. 2 Gb ram. ~3 Ghz processor multicore(?). I don't know much more than that, as I can't access the computer at this time. 64 bit. It's the only OS. I was using the default video driver for Ubuntu. I installed Mesa through sudo apt-get. What is a motherboard splash screen? I can get to grub if I hit crl+alt+delete it gives me the options of a safe boot, and also of a slightly older version of the os to boot. I can enter the BIOS. Is the video adapter the physical card inside the case, or the software that runs it? I have login disabled on the computer; it hits the main Ubuntu home page automatically, so I don't know if the login hits or not. That is, it used to until it broke. Ubuntu 14.04.3 amd64 desktop.

---

