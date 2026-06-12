---
title: "Laptop does not register 'space' key at GRUB level and beyond"
date: 2022-05-14
forum: General Help
---

### Post by Peter_Brandon on 2022-05-14
I have a fairly new laptop that I've used lightly.  Periodically, it refuses to register the 'space' key after a reboot (nothing happens when I hit 'space').  This is evident when I try to enter the password to decrypt my hard disk.  But I've also tried the 'edit' screen in GRUB (where I choose my ubuntu kernel on bootup, and before the hard disk decryption) and cannot get a space key there either.  No space key renders the laptop close to unusable.

The problem used to go away after a reboot, but in the last few days I've rebooted as many as 10 times and the problem remains.  Today, I tried to see if the problem also occurs when I boot from a different copy of Ubuntu on a USB key.  The space key worked once I was in the USB version of Ubuntu.  More than that, when I rebooted the laptop without the USB, suddenly the space key is working--after many times not.  It's almost as if it learned the space key again after the USB  boot.

Any thoughts on what's going on here and what I might try to fix it?  Maybe rebuild grub?

---

### Post by GhX6GZMB on 2022-05-14
More likely a keyboard error... like dirt in the "space"-key switch.
Did you ever turn the keyboard upside down and see how much nastiness falls out?

---

### Post by Peter_Brandon on 2022-05-14
I've barely used the laptop.  Have tried to turn it over.  Absolutely nothing comes out.  The space bar has stopped working a couple dozen times at and only at boot.  It never starts to work when I try typing into a booted system, once it fails at boot.  But, I reboot and the space bar usually starts working again (except the most recent episode, when it only started working again after I booted from USB).  So, while a good idea, I doubt the problem is gunk in the keyboard.

---

