---
title: "Freezes on boot with GRUB_ in upper left corner"
date: 2006-12-31
forum: General Help
---

### Post by david.rahrer on 2006-12-31
I'm dead in the water here and would greatly appreciate some help.

I've been running Edgy for about 2 months now with no real problems.  I'm new to Linux on the desktop so I need some help with this.  The only significant thing I did today was create a backport of GAIM using prevu and install it.  That seemed to go fine, but after I rebooted instead of getting the GRUB menu, I get a frozen black screen with GRUB_ in the upper left corner.  I have no idea how installing that could have affected the boot.

I'm downloading an Edgy LiveCD right now, but I'm not entirely sure how to use that to gain access to my damaged install.  I've seen some posts about GrubEd and Super Grub, but I've never had to do this before.  Could someone give me a basic idea of what I need to do to gain access to my HD install and what I should try first to see what's wrong?  I'm bummed out right now as you can imagine :(

Additional info: I have a dual boot with XP (which still works).  GRUB is installed on the Ubuntu root partition, not in MBR, so if I need to reinstall GRUB,  I need to know how to put it there.

Thanks for any help at all.

---

### Post by romainb on 2007-01-10
Same problem here, except after a fresh install to an external usb hd. I tried installing GRUB to /dev/sdb (MBR of my extern. hd) and /dev/sdb5 (logical partition where I installed ubuntu): everytime I make an attempt to boot any of those from the windows boot loader, I get a "GRUB_" screen that hangs there, freezing my computer. Also tried changing the startup order in my BIOS to USB first, but it just shows a blinking dash screen, then quickly something along the lines of "no bootable partition" (don't remember exactly) and starts up windows.
I already did a (working) install of kubuntu (6.06) a while ago and have since replaced my hard drive, and I was hoping to install (k)ubuntu (6.10) on my old hard drive which is now set up as an external USB.
ANY help is greatly appreciated as googling this problem didn't yield much results,
Thank you,
R.B. ](*,)

---

### Post by david.rahrer on 2007-01-11
I forgot to update the thread.  I used a LiveCD (Alternate) of Edgy and used the recover option on boot.  I then selected to reinstall GRUB and filled in the root/boot extended partition where Ubuntu is installed.  When I booted again from the hard drive, it worked normally except it did a fsck and repaired something I think.  It's worked fine since.  I found little help on this for some  reason.  Good luck.

---

