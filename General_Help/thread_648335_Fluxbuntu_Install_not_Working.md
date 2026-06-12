---
title: "Fluxbuntu Install not Working"
date: 2007-12-23
forum: General Help
---

### Post by peterpancreas on 2007-12-23
Hi everyone, I'm trying to install Fluxbuntu on a pc that also has Ubuntu on it.  I've downloaded the iso, burned it and set my bios to boot from the cdrom drive first, but it's not booting from the disk.  (just in case you're wondering, I've burned two discs from two different computer downloads, with the same results both times).

After getting into Ubuntu and accessing the cdrom from there, I can't tell what to do.  There's an install folder with initrd.gz and vmlinux in it, but Ubuntu won't let me expand initrd.gz.  Does anyone have any experience with how to get this installed, or any other tips?

I just had an idea that I'm going to try, I'll plop the cdrom into another computer and see if it boots from the disk.  If it does then it's the first computers startup process that's bad.

Thanks,
Stephan

edit- looks like the fluxbuntu install cd is booting up fine on the other computer.  Is there a good way to find out what's wrong with my bios settings, keeping the install cd from booting up?  I've told it to boot from the cd drive first, but it's not doing that.

---

### Post by andrewcmcardle on 2007-12-24
I got the same errors, i gave up eventually
You could possibly copy vmlinux and initrd.gz to your hard drive, then tell your boot loader to boot them from your hard drive. Other than that i don't know.

---

