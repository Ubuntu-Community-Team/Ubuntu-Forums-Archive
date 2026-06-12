---
title: "[SOLVED] Wubi doesn't run on Dell XPS M1330"
date: 2008-06-14
forum: General Help
---

### Post by shaunconn on 2008-06-14
Hi

Wubi 8.04 seems to install OK, but the boot drops to the dreaded initramfs prompt.  I am getting the "...upper memory..." message some others have seen..

So far I have:

ran chkdsk /r - no change
tried irqpoll, pnpbios=off - no change
upgraded to the latest grub4dos - no change

I assume this is something bios related, since if I hit insert whilst booting I get:

"Warning:MBR total sectors is greater than BIOS" followed by
"Open (128,4) /ubuntu/install/boot/grub/default failure"

If I try one of the other boot items (ACPI) I get:
"PnP BIOS caused fatal error".

I can boot from an external ubuntu drive on the machine OK, so is it the Dell M1330 bios?  

Is anybody using the M1330 and Wubi - with bios A09?

Regards
Shaun

---

### Post by Unixus on 2008-06-24
Same problem on Dell Latitude D630
Might it be a problem with Dell's Utility partition hidden at the front of the hard disk?
Problem is I can't get rid of it as I'm not allowed to make any partition changes... weird company rules...

---

### Post by ago on 2008-06-24
please try wubi 8.04.1 and report whether it fixes your problems
see the sticky thread for more info

---

### Post by Unixus on 2008-06-30
Thx for that [FONT="Arial Black"]ago[/FONT]! 
I downloaded the Ubuntu 8.04 daily build and used the Wubi 8.04.1 installer and it installed without any problems this time.

Ubuntu 8.04.1 Daily build:
[http://cdimage.ubuntu.com/hardy/daily-live/current/](http://cdimage.ubuntu.com/hardy/daily-live/current/)

Wubi 8.04.1:
[http://wubi-installer.org/devel/minefield/Wubi-8.04.1-rev503.exe](http://wubi-installer.org/devel/minefield/Wubi-8.04.1-rev503.exe)

Or have a look in [FONT="Arial Black"]ago's[/FONT] previous thread:
[http://ubuntuforums.org/showthread.php?t=835987](http://ubuntuforums.org/showthread.php?t=835987)

---

