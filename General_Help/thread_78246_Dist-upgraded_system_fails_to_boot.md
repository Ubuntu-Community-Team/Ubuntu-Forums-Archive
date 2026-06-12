---
title: "Dist-upgraded system fails to boot"
date: 2005-10-18
forum: General Help
---

### Post by MacMasta on 2005-10-18
I just dist-upgraded my Hoary machine to Breezy, as per the BreezyUpgradeNotes on the Wiki.

The kernel spits the usual collection of things about finding stuff (the format seems to have changed, but it does seem to find things) and then fails with "cannot find /dev/root no such device or address", at which point it explodes nicely and drops me at the busybox prompt.

Help?

Thanks!

~Mac~

---

### Post by izmaelis on 2005-10-18
I think you should check your /etc/fstab file.

---

### Post by afonic on 2005-10-18
Have a loot at /boot/grub/menu.lst. Its one of stuff that gets updated after a new kernel installation (and during the upgrade of course).

It may load but if you have the root=/dev/yourlinuxharddisk option wrong in the kernel line it will look for / and not find it. Maybe you changed the boot priority of your hard disks or their connection?

---

### Post by MacMasta on 2005-10-19
Solved it.

Here's the problem:

For some reason, the Breezy Kernel decided the order of my hard drives should change.

So, hdm (my old root drive) became hda.

(Oddly enough, this drive has _always_ been first channel master; Hoary just decided to number them in reverse)

The solution turned out to be passing a "root" line to LILO, then editing /etc/fstab and /etc/lilo.conf to reflect the changes. Not too terrible.

Interesting factoid, though: in the process of figuring this all out, I installed Breezy from scratch; the Breezy install CD ordered my drives like Hoary did; IE, first channel master was hdm. However, the kernel that actually ended up on the hard drive ordered them in the more traditional fashion, with that drive as hda. 

This caused no end of weirdness; the install CD couldn't install a bootloader to save its life (more chroot magic fixed that; had to do it by hand), grub couldn't find the BIOS disks and was completely useless, etc.

I feel like a Gentoo user! (I used to be, for that matter)

Anyway, all is well; I hope this update helps anybody else in my position.

~Mac~

---

### Post by orac7000 on 2005-10-19
What would the command line parameters be for grub to fix this issue please?

---

