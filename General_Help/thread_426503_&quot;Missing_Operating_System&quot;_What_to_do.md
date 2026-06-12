---
title: "&quot;Missing Operating System&quot;? What to do?"
date: 2007-04-28
forum: General Help
---

### Post by Vinze on 2007-04-28
Hey, I followed [this guide](http://www.debuntu.org/how-to-install-ubuntu-linux-on-usb-bar) to install Ubuntu on my USB bar. Now I try to boot from it and I get the message "Missing Operating System". How can I fix this?

Thanks in advance.

---

### Post by fwojciec on 2007-04-28
Most likely Grub is misconfigured.

If you edit /boot/grub/menu.lst (on the USB stick, I guess) at the botom of the file you'll see a bunch of entries for Ubuntu Feisty, the second line under the title of each grub entry you'll find something that looks like this:

> root		(hd0,1)

This defines where the image that needs to be loaded is located.  Ubuntu installer notoriously misconfigures Grub when an unusual combination of drives is present on my system, for example.

In either case the first number in (hd0,1), or the zero in my example, points to the device number (first one on your system is "0", the second one is "1", etc.)  The second number refers to the number of the partition where the image is located (so the first partition, usually boot partition, is 0 and so on).

Basically you have to correct those numbers so that they point to the correct device/partition combination - what these are you'll have to figure out yourself - I've never installed linux on a USB stick, so I don't know how that works.

You can do a bit of trial and error while booting (you can edit boot entries from Grub at boot) - they won't be saved, but at least you should be able to figure out what the device/partition combination that works is.

The number which is incorrect is most likely the device number.

Or I'm completely wrong and the problem has to do with something else ;)

---

### Post by Vinze on 2007-04-28
> **fwojciec said:**
> Most likely Grub is misconfigured.

If you edit /boot/grub/menu.lst (on the USB stick, I guess) at the botom of the file you'll see a bunch of entries for Ubuntu Feisty, the second line under the title of each grub entry you'll find something that looks like this:



This defines where the image that needs to be loaded is located.  Ubuntu installer notoriously misconfigures Grub when an unusual combination of drives is present on my system, for example.

In either case the first number in (hd0,1), or the zero in my example, points to the device number (first one on your system is "0", the second one is "1", etc.)  The second number refers to the number of the partition where the image is located (so the first partition, usually boot partition, is 0 and so on).

Basically you have to correct those numbers so that they point to the correct device/partition combination - what these are you'll have to figure out yourself - I've never installed linux on a USB stick, so I don't know how that works.

You can do a bit of trial and error while booting (you can edit boot entries from Grub at boot) - they won't be saved, but at least you should be able to figure out what the device/partition combination that works is.

The number which is incorrect is most likely the device number.

Or I'm completely wrong and the problem has to do with something else ;)

Well, as far as I am aware, Grub doesn't even load...

---

### Post by fwojciec on 2007-04-28
Like I said, I've never tried installing Ubuntu on a USB drive, so I'm probably not much help.  The guide you linked in your first post has a troubleshooting section - did you try to do what it says there?

---

### Post by Vinze on 2007-04-28
> **fwojciec said:**
> Like I said, I've never tried installing Ubuntu on a USB drive, so I'm probably not much help.  The guide you linked in your first post has a troubleshooting section - did you try to do what it says there?

D'oh! Stupid that I didn't check there, that looks like it could just be the solution! I'll keep you updated.

---

### Post by loatswil on 2007-07-19
I am seeing this happen when attempting to boot off USB on a Latitude D810 but it works fine on an Optiplex 745. Same USB stick but different results. Of course the Latitude is a bit older but it claims to support booting from USB. I have updated the BIOS with no luck...

---

### Post by Vinze on 2007-07-19
> **Vinze said:**
> D'oh! Stupid that I didn't check there, that looks like it could just be the solution! I'll keep you updated.

Guess I didn't what I said I would do... Totally forgot. 

Anyway, I think I was trying to get Ubuntu Feisty to work, but it has a bug so it wouldn't have worked anyway. I do know the troubleshooting section did help me a few times, but I believe that was another error message.

Anyway, I finally managed to get Ubuntu Feisty (sort of) working from my USB drive (documented [here](http://xubuntublog.wordpress.com/2007/06/17/ubuntu-feisty-on-your-usb-drive-finally/)) and later Xubuntu (documented [here](http://xubuntublog.wordpress.com/2007/07/03/xubuntu-feisty-now-from-usb-drive/)). Hope it's of any help to anyone.

---

