---
title: "dual boot debian with ubuntu - trouble"
date: 2007-01-01
forum: General Help
---

### Post by nix4me on 2007-01-01
Hi,

I am running ubuntu and I tried installing debian on a second hardrive.  Ubuntu is installed on hda and debian is installed on hdd.  For some reason, debian will not boot from grub.  Here is the main area of my /boot/grub/menu.lst:

```
## ## End Default Options ##

title		Ubuntu, kernel 2.6.17-10-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.17-10-generic root=/dev/hda1 ro quiet splash
initrd		/boot/initrd.img-2.6.17-10-generic
quiet
savedefault
boot

title		Ubuntu, kernel 2.6.17-10-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.17-10-generic root=/dev/hda1 ro single
initrd		/boot/initrd.img-2.6.17-10-generic
boot

title		Ubuntu, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
quiet
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/hdd1.
title		Debian (on /dev/hdd1)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.17-2-686 root=/dev/hdd1 ro
initrd		/boot/initrd.img-2.6.17-2-686
savedefault

```
The second drive should be hd(1,0) and the boot partition should be hdd1.

I have no idea why it wont boot.  Ant ideas?

nix4me

---

### Post by kidders on 2007-01-01
Hi there,

What messages do grub/debian give you before the boot fails.

---

### Post by nix4me on 2007-01-01
Grub says something like drive not available.

nix4me

---

### Post by kidders on 2007-01-01
Could you be more specific? Unfortunately, it's hard to diagnose an issue without an indication of what's causing it. :-(

---

### Post by nix4me on 2007-01-01
There are no more specifics.  When I select Debian from the grub boot menu, grub gives an error saying drive not available.

Nothing happens.

I think somehow things got messed up.  When I installed debian, i chose to install grub to the mbr.  It detected that ubuntu was already there.  When i rebooted, i got a grup error 17.  So i poped in the livecd and forced the mbr to be reloaded.  Now, ubuntu boots fine fron grub, but debian on the second harddrive will not boot.

nix4me

---

### Post by kidders on 2007-01-01
I was hoping for the exact error message. :confused:

In the meantime, it might be worth checking that Debian (ie not just Ubuntu) refers to the disk it is on as /dev/hdd, which is not necessarily the case. Also, I notice that you said Debian's **boot** partition is /dev/hdd1. Again, it's not necessarily the case that the boot and root partitions are one and the same.

These are both shots in the dark though, as I'm still not clear on what your error is, let alone what might be causing it, or how to fix it. The more information you can provide, the easier it is to identify your problem.

---

### Post by nix4me on 2007-01-01
The error is:

error 21  Selected disk does not exist

nix4me

---

### Post by kidders on 2007-01-01
Hmm...

Next time you reboot, it might be worth dropping to a grub console, and asking it about (hd1). It could be that (hd3) is the right label, for instance. The grub console will let you poke around your filesystems a bit, so you can satisfy yourself that the disk number is right.

---

### Post by Ramses de Norre on 2007-01-01
Shouldn't there be another line "boot" underneath "savedefault" ?

---

### Post by knobcottage on 2008-02-21
First of all, I am not a geek so I'll talk everyday speak.  Pardon me for that.  I' messed around with ubuntu and windows and debian over the xmas holidays and got error 21 a lot when I was installing to a usb drive.  I did it wrong often enough to see a similarity here.  Investigating the symptoms lead me to believe that somehow there is a bug, documented and discussed, can't remember where about GRUB installation on a second hard disc when it is not a usb installation.  My dual boot usb always wrote GRUB to the wrong drive and if I told it to write to the correct drive it wrote the wrong information.  3 hours later I gave in.  I tried looking for grub 21 error messages in the forums,  it took me ages, it took me ages but it turned out that there was no solution I could understand.  Probably does not help but at least you have a way to go?!  try error 21 grub on google...you'll find you are not alone!

....and the best and easiest solution I found again......
[http://www.hentzenwerke.com/wp/reconfiguring_the_mbr.htm](http://www.hentzenwerke.com/wp/reconfiguring_the_mbr.htm)

---

