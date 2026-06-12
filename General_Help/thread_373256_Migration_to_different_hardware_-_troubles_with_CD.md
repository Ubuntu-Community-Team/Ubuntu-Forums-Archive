---
title: "Migration to different hardware - troubles with CD-ROM and USB"
date: 2007-03-01
forum: General Help
---

### Post by DoktorZ on 2007-03-01
Hello Everybody!

Here is my problem: I had Ubuntu 5.04 cleanly installed on Asus P4C800/i875P motherboard with P4 processor. Then I've upgraded to 5.10 and finally to 6.06 LTS. And then I've got new PC - Intel COre2 Duo E6400 on  a Intel motehrboard (965 chipset). Anyway I just hooked up new HDD (SATA) to the old PC and copied partitions with dd_rescue. Then I changed /dev/hda references in /etc/fstab and grub's map to /dev/sda (because it was how some live systems identified my HDD on a new system).

 And all went up quite well and working. But with single core, unfortunately and NO CD DRIVE (ATA) visible anywhere. So I've downloaded 2.6.20.1 from kernel.org, compiled it and installed. Now I have dual core support, everything works, BUT still no CD-ROM drive, and USB devices do not automount when inserted. Writing mount every time is fun, but I'd like to have an automount. And when system starts it says that some DEVPTS filesystem not supported...but there is no kernel option with DEVPTS support.

Thanks for help in advance!

---

### Post by DoktorZ on 2007-03-02
hello! anybody here????

---

### Post by dcstar on 2007-03-02
> **DoktorZ said:**
> hello! anybody here????

It is generally problematic moving an installed system to different hardware.

Too many things are detected and configured during installation, and it would be a massive waste to have all of that code in the normal startup of a Ubuntu system.

You may be able to kludge some sort of re-detect of your existing install, but it would probably be quicker to save your data and do a fresh install on your new hardware.

---

### Post by DoktorZ on 2007-03-05
> **dcstar said:**
> It is generally problematic moving an installed system to different hardware.

Too many things are detected and configured during installation, and it would be a massive waste to have all of that code in the normal startup of a Ubuntu system.

You may be able to kludge some sort of re-detect of your existing install, but it would probably be quicker to save your data and do a fresh install on your new hardware.

Hey! But the system is working perfectly! Audio, LAN, Video (I've got 800 FPS in bzflag!!!) - everything is ok, except for CDROM and USB auto mounter! 

I've installed there so much different software, some from sources, some are just binaries, some from rpms..etc. I'll spend weeks reconfiguring evertything on a fresh install!

So much for "humanity to others"...pfff. People nowadays do upgarde there hardware. Once a year or two - a major upgrade. Reinstalling from scratch every time is not user friendly!! :)

---

