---
title: "Fried Feisty Installation - No Kernels Will Boot"
date: 2007-06-03
forum: General Help
---

### Post by Mike_H on 2007-06-03
Here's the situation: I came home and waved my mouse like I usually do to bring up the password prompt (lock screen on Screensaver is on) and for some reason I get booted to a default Ubuntu desktop.  None of my programs were running (Beryl, F@H, Avant Window Navigator, etc. all gone). I figure someone must've been playing around and switched users and by some divine means somehow logged on to some other user (although no other users exist but my own).  I hit log out, but did not get kicked into the X Log in screen. I see the mouse, but it's completely black.  I reboot, and lo and behold my GRUB has been tampered with and my Windows XP install entry was deleted.  I boot into Ubuntu Kernel 2.6.20-16 and after about 5 seconds at the orange Splash Loading screen I get a couple hundreds of lines of errors spit at me.  I didn't even have time to glance at half of them.  I got a lot of errors eluding to "/bin/sh" and the first errors on the screen state "Cannot open kbd_mode".

This is strange because this is EVERY kernel, including the recovery ones.  After booting up a Feisty LiveCD I was able to edit the GRUB and get back into Windows (ugh, haven't used this in awhile).  I also backed up all of my important files onto an extra HDD, just in case.  Feisty is installed on it's own partition, so it wouldn't be too much trouble (except for the whole data/software installs/configuration loss thing) to reinstall it, but I'd like to recover it if I could. Any suggestions?

Oh, and also, I had my AMD 3800+ X2 overclocked at 2.4 GHz (up form 2.0 GHz) and it was running Folding @ Home at 100% both cores. I have now cleared the CMOS and everything is running at stock again. Still no luck booting up Feisty.

---

### Post by snobel on 2007-06-06
A couple of suggestions: Try editing one of the initrd entries in the grub menu to add .bak to the name (e.g. /initrd.img-2.6.20-16-generic.bak). If something did something nasty to your initial ramdisks, it may work to boot on the old copy. (This saved me the other day...)

If that fails, try booting a live cd and mount your root partition, then regenerate the initrd:

```
sudo -s
chroot <mount point>
update-initramfs -c -k 2.6.20-16-generic
```

You may get some errors but they should not be significant.
After that try booting again.

---

