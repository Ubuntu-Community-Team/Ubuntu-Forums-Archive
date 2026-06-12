---
title: "Ubuntu and variants - black screen after splash possible fix -help-"
date: 2013-11-22
forum: General Help
---

### Post by gordan-vrbanec-vepar on 2013-11-22
Ok, i already posted this type of thread but now i think i know what the problem is.

It's an older computer;

Intel Celeron (about 2 ghz), i think it supports pae (it should)...
512 MB RAM
80 GB HDD
VIA onboard graphics... <-- this is the problem obviously...

So before i tred adding "xforcevesa", "nomodeset" and all kinds of options to the boot but nothing helped.
I had "LXLE" installed but that was painfully broken and slow, CPU was always at 100% and meh... So i decided to try other ubuntu variants instead.

Then i realized, i installed LXLE on an older CRT monitor with installer only option, no live CD so the resolution was minimal by default, but i installed Lubuntu on my own newer LED monitor.
I tried Bodhi in Live CD (because it doesn't have any other option; which, a system that is designed for older computers should have, i mean, really...), and the screen was all jittery with lines all over and very choppy, nothing much could be seen so i couldn't install it.
The same happened to LXLE when i first booted to it.

Then i realized!

Ubuntu (and other distros that use that kernel) defaults to the maximum monitor resolution when booting. That's why nothing works when i try to run it on my LED monitor because the default resolution for that is 1920x1080 and VIA graphics just can't handle it.
That's why it was so jittery on LXLE. It defaulted to 1152x864 which is that CRT's monitor maximum resolution but the chip couldn't handle it.

How i "fixed" it was, i blindly clicked the mouse until i got a monitor resolution setup screen. The desktop was kind enough to stop jittering for a second to let me see where i'm clicking. The mouse wasn't jittery though...
I lowered the resolution to 1024x768, saved it, and everything was ok! I rebooted to make sure, and it booted to the saved resolution, no jitters, no lines, no glitches.


Now i need some help!
The new installation can't even boot there, and i can't even see the mouse.

Is there some way to force a resolution from the command line rescue mode?
Not just grub2's resolution, but actual OS resolution.

Is there a file i can edit and set the resolution from the command line with nano or something?
Because the rescue mode command line works.

I basically need to edit the settings manually instead of going to monitor settings and setting the resolution there. But that's basically what i need to do and hopefully that should work.

So, i'm a noob. Not a massive noob, but noob enough so i don't know where linux stores resolution settings and i can't find it on the net. Maybe no one needed it before.
Can anyone help me? What file do i need to edit to "set the resolution" of the OS? The equivalent of setting the resolution by clicking it in the GUI.
I hope i'm making sense. 

Anyway... Looking forward to some answers! :)

---

### Post by gordan-vrbanec-vepar on 2013-11-23
Please, i need to know how to change the resolution of the OS in the recovery mode.

---

