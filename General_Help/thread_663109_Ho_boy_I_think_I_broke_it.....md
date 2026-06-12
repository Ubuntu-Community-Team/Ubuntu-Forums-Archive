---
title: "Ho boy I think I broke it...."
date: 2008-01-09
forum: General Help
---

### Post by VitaminH on 2008-01-09
Good evening!

Ho boy I'm not sure what I've done here but I don't know if this is a hardware defect from the manufacturer or if something is messed up on the software side so here goes.  Pardon my slight linux/hardware illiteracy, I've been a Mac user for years and generated an interest in Linux some time ago while fooling in the terminal on OS X and finally when my imac died here at home I replaced it with a HP AMD 64 Pavilion m9000z PC with plans of running ubuntu.  I got it, with Vista preinstalled (it IS as bad as everyone says, it was AWFUL) and immediately partitioned the HD and slapped ubuntu on there.  I installed 7.10 i386 and had it up and running just fine.  My troubles began with the wireless card randomly dying after a certain amount of use, I reseated the card inside the machine (which is about the extent of my abilities to fix hardware) and it seemed to help, but the problem popped up again.  I've been working on that, but that is for another post...

This morning I was surfing the web before work when the whole system seemed to lock up.  I couldn't close Firefox, the clock was no longer running and CTRL-ALT-DEL did nothing.  I hit the power button to reboot and then got the message "DISK BOOT FAILURE, INSERT SYSTEM DISK AND PRESS ENTER"


So i just shut it down and left it all day, came home tonight to the same thing.  I popped in the 7.10 DVD and told it to off the DVD and got the following

(initramfs) [     25.468000] ata1: SRST failed (errno=-19)
[     60.468000] ata1:SRST failed (errno =-19)
[     60.468000] ata1:reset failed, giving up


then nothing.........

It appears my Hard Drive is....dead?  I just bought the dang thing!  HP didnt even give me restore CDs as they had a partition on the HD with the backup data.  I suppose I should have burned that to a DVD.  Sigh...

Anyway, is this an ubuntu problem or a straight up hardware problem?  I'm lost.  Thanks for the help!

---

### Post by -grubby on 2008-01-09
probably a hardware problem but you could try reinstalling ubuntu (perhaps the filesystem is corrupted) 
PS: ctrl-alt-del does nothing in linux. you can press ctrl-alt-backspace to restart the XSERVER (which restarts the "layer" of which the input and output devices (like the mouse, graphics card, keyboard, etc..) and it fixes problems with the GUI (which might actually save you if your system freezes up again (if you ever get it installed counting on the fact that the filesystem isn't corrupted)

---

### Post by SeanTater on 2008-01-09
If you did not add or remove or otherwise change that hard drive, I would point to the hardware. However, before condemning it to the wastebasket, if you have the technological wherewithal, you might try:

1) Attaching it's data cable to another slot on the motherboard, if it's available
2) Removing any drives on the same cable
3) Booting the hard drive in another computer

If there are any other OS's on that hard drive, try booting them. If none of the above works, you might have a 3.5 inch brick.

---

### Post by VitaminH on 2008-01-10
Hello again,

Thanks much for the fast responses.  The problem with even trying to install to a new system is that when I tried to boot to the CD it never would and just gave me those SRST failed errors...


As far as what Sean said:

1) I'll try attaching the cable to another slot, I would be less than thrilled with HP if they sent me a motherboard with bad connections out of the box, and would be requesting a replacement.
2)It's the only drive in the machine, let alone on that cable.
3)I've got no other computers other than the laptop i'm tying this on and I sadly don't have a firewire enclosure or anything to slap it into to test it out.  

As far as booting to another OS, Vista is/was on another partition of the HD but I can't tell it to boot that because I don't even get to that initial screen on startup where you select which OS you want to boot to.  I get the HP logo (which says Push F11 for system recovery...but i've tapped it repeatedly while it starts and nothing comes of it) and I get right to the "DISK BOOT FAILURE, INSERT SYSTEM DISK AND PRESS ENTER"

I can't start the machine up at all.  

I suppose I should call HP.  Sigh.  I'm about ready to send the whole dang thing back and just go buy a cheap linux machine at walmart to mess around with.

---

