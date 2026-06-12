---
title: "How to install Win 2000 Pro as a second operating system to Linux"
date: 2007-08-06
forum: General Help
---

### Post by Mirm on 2007-08-06
Linux is great in many ways. Unless you view your computer as a source of entertainment and communication, and nothing else. I need an operating system that works with my familys needs. Linux has become more of chore.. 

I would like to keep Linux for some of the great applications it does have, but have windows, real windows, not a windows emulator, run as well for, well, everything else. What's the best way to go about making this happen, in laymans terms please,?  And is this even possible?

Yes, I tried Googling it but I kept getting Microsoft telling me how to uninstall linux and replace it with windows. That's Plan B.

---

### Post by merlinus on 2007-08-06
Windows likes to be the first partition on the disk.  You can use gparted live cd ([http://gparted.sourceforge.net/](http://gparted.sourceforge.net/)) to partition your drive, copy the linux partition to the second one, and install windows on the first.

You will then have to reinstall grub, but that is easy.  And you will be able to select between ubuntu and windows on startup.

-merlin

---

