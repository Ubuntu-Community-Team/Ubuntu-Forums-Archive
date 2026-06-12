---
title: "nvidia 660M driver only works after running fsck"
date: 2013-01-28
forum: General Help
---

### Post by magnet18 on 2013-01-28
I'm running ubuntu 12.04 64 bit on an ASUS G75 EFI based system. after install the resolution was off, so i installed the most recent nvidia drivers

now, whenever i boot, i get an error message 

"The system is running in low-graphics mode

your screen, graphics card, and input device settings could not be detected correctly. You will need to configure these yourself"

If i hit ok here, i'm given 4 options, the first is automatically selected but it's irrelevant because I can't click on either ok or exit

if i instead boot into ubuntu recovery mode, and then failsafe graphics, it runs-

"
fsck from util-linux 2-20-1
fsck from util-linux 2-20-1
dosfsck 3.0.12, 29 oct 2011, FAT32, LFN
/dev/sdb5: Superblock last mount time is in the future.
   (by less than a day, probably due to the hardware clock being incorrectly set) FIXED.
/dev/sdb5: Superblock last mount time is in the future.
   (by less than a day, probably due to the hardware clock being incorrectly set) FIXED.
/dev/sdb5: clean, 275248/5980160 files, 1529967/23898112 blocks
/dev/sdb1: 94 files, 12261/110352 clusters
"

and if i shut down after that runs, it reboots just fine, nvidia drivers load and everything is dandy, until i shut down again, and the entire process repeats

i checked and my system clock is set correctly, and i tried both the most stable and most recent drivers, no avail

if anyone knows what's going on and how to fix it, it would be much appreciated

Thanks!
rob

---

### Post by magnet18 on 2013-01-28
nevermind

I shut down last night and gave up
booted this morning and it worked fine
apparently it fixed itself

---

### Post by magnet18 on 2013-01-30
It, apparently, did not fix itself

So I've been watching this problem for a couple days, and I really can't find what exactly triggers it.
Sometimes, I power on and boot up no problem.
Other times, it boot up and get the error described above.
Each time, booting up in failsafex mode, and then shutting down fixes it, although sometimes the next time I boot up I'll be in a command prompt, no desktop.
Typing startx brings up the desktop, but no cinnamon interface.
When this happens, sudo reboot always fixes it, and as far as I can remember it never gets the graphics error when rebooting after not having a desktop.

Its almost certainly the graphics card.

I don't know how much of that is useful, and I feel like I need a flowchart to explain it. :P

In short, it happens somewhat randomly, and I have yet to find a solution online.
It's more of an annoyance than a major problem, because I can do the shutdown/reboot/shutdown/reboot again procedure in under a minute, but it's still really annoying, and represents a system problem.

Any ideas anyone?

---

### Post by magnet18 on 2013-02-04
i can now verify that it always always happens after shutting down windows

anyone have any ideas?

---

### Post by magnet18 on 2013-02-05
weeeellllll then
to conclude this monologue
i gave up trying to solve the problem, and settled on adding touch /forcefsck to the /etc/rc.local file

costs .5 seconds of boot time, but whatever

---

