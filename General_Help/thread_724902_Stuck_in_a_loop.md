---
title: "Stuck in a loop"
date: 2008-03-15
forum: General Help
---

### Post by heiowge on 2008-03-15
Last night I installed Ubuntu using wubi - those of you without knowing just how messed up my laptop situation is note the following:

Sony Vaio FX 702 (about 6 years old)
256MB RAM
20GB hd
Athlon 1400+
Broken DVD/CDRW
Broken Battery (won't run except on AC)
Enet

Cannot boot from USB, or any external CD / HD.  Only option - install in XP using wubi.  Installed Ubuntu 7.04 feisty (for reasons of RAM).

Install went very smoothly, took a while but that was expected.  Installed several extra packages (mostly updates and things like Frozen Bubble!)

This morning the system crashed.  It locked up and refused to close a window.  So I (being a linux newbie and knowing that ctrl-alt-del didn't work in linux, and being p***ed at the kids for constant pestering) did the unthinkable and pulled the power cable out.  The machine shut down.

I gave it a minute, plugged in and booted up.

All was well.  I got the sony screen then the option to load xp or ubuntu.  I chose the latter.

Next it loaded the sony screen then the option screen again.

No matter what I choose, or let it choose for itself, or whether or not I use the options in the help menu, it just keeps doing the same loop.

I can't even restore xp as it needs a startup disc and my cd is bust.

Any help?

I can get into the bios, but it doesn't seem to help any.

---

### Post by heiowge on 2008-03-15
bump

---

### Post by ugm6hr on 2008-03-15
I cannot see how a crash within Ubuntu could damage the XP installation as well.

It is possible that GRUB (the bootloader that gives you the XP / Ubuntu options has become corrupted.

Or your HD has come to its last legs.

I would suggest you try booting with a LiveCD to see if you can still see your partitions and files on the HD.

Puppy is a good choice: [http://www.puppylinux.org/user/viewpage.php?page_id=1](http://www.puppylinux.org/user/viewpage.php?page_id=1)

If you can, then at least you should be able to recover your files if things get worse.

Then use the appropriate HD diagnostic tool to check your HD: [http://www.ultimatebootcd.com/](http://www.ultimatebootcd.com/)

If it all checks out, then I suspect a reinstallation of GRUB should do the trick (SuperGrub Disk on ultimatebootcd).

---

### Post by heiowge on 2008-03-15
Good suggestions, but I can't do that without a CD drive.  Any suggestions?  I've got a floppy drive or can connect external drives, just can't boot from them.

---

### Post by danwood76 on 2008-03-15
buy a new CD drive, you dont have much hope in repairing your PC without it.
either that or a new laptop :)

---

### Post by strabes on 2008-03-15
Yeah, you're kind of out of luck if you can't boot from anything and neither grub option works. You really need a working CD drive these days.

---

### Post by ugm6hr on 2008-03-15
> **heiowge said:**
> Good suggestions, but I can't do that without a CD drive.  Any suggestions?  I've got a floppy drive or can connect external drives, just can't boot from them.

Sorry - thought you meant your XP CD was bust.  My fault for not reading carefully.

But without access to any OS, and no device available to boot from, you are a little stuck.

Can you boot from ethernet?

But honestly, the easiest thing would be to pay for a new CD drive.

---

### Post by heiowge on 2008-03-15
Cash is a major problem at the moment - unemployed!  So no new laptop and no new CD drive (only ones I've seen for my make and model in excess of $700!  That's more than the laptop's worth!

I already have an external DVDRW drive, but my bios won't let me boot from it.

Tried the network boot option - there is such an option in the bios, but I couldn't get it to work (too much the newbie!) other than through wubi - and that requires xp to run.

---

### Post by ugm6hr on 2008-03-16
So - to summarise:

No current OS
No working CD drive
Cannot boot from any USB device
Can boot from ethernet
Can boot from floppy

In that case, this might work:

Install Linux from boot floppies / internet (e.g. Debian):
[http://www.debian.org/distrib/netinst](http://www.debian.org/distrib/netinst)

Then install Ubuntu from ethernet within Debian:
[http://lubi.sourceforge.net/unetbootin.html](http://lubi.sourceforge.net/unetbootin.html)

---

### Post by heiowge on 2008-03-25
Finally had a chance to do it, but no joy.  Couldn't get it to work.

I think the laptop is just plain bust.  Still, got my wife to let me dual boot the XP machine with Gutsy!  So all is not lost.

Cheers for the help.

---

### Post by ugm6hr on 2008-03-26
> **heiowge said:**
> Finally had a chance to do it, but no joy.  Couldn't get it to work.

I think the laptop is just plain bust.  Still, got my wife to let me dual boot the XP machine with Gutsy!  So all is not lost.

Cheers for the help.

In case anyone else has a presumed similar problem, this is another option:
[http://ubuntuforums.org/showthread.php?p=3956118#post3956118](http://ubuntuforums.org/showthread.php?p=3956118#post3956118)

Sorry your laptop is past hope :(

---

