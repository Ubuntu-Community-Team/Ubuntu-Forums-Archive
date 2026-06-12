---
title: "Strange LIve CD Booting"
date: 2007-10-22
forum: General Help
---

### Post by Fred Doolie on 2007-10-22
I have two systems: A Dell Laptop and a Mega 180 Desktop.
Here's how the live CD boots on each:

Laptop:
Screen goes to what looks like 1024x768
Moving orange bar for a minute or so and CD loads away.
Boot finishes and all is cool. Screen is in proper 1280x800 mode.
System runs normally.

Destop:
Screen goes to 640x480. 
*HUGE* orange bar that moves back and forth for 15 minutes.
No CD activity....then a little....then none...
System loads SLOOOOOOOWLY. Screen actvity is SLOOOOW.
Boot finishes and everything looks good. Screen is in proper 1280x1024 mode.
System runs normally.


It looks like the system is trying to figure out what graphic card I have(?)
It's a regular NVidia GForce 440 MX. Any way to force the boot to start with that?  I tried safe graphic mode but get the same sequence.

---

### Post by Insightfill on 2007-10-22
I saw something similar on an iMac last year, and it turned out to be related to "dri" in the xorg.conf file.  I'm not sure if it's your problem, but it can't hurt to try:

[http://ubuntuforums.org/archive/index.php/t-462494.html](http://ubuntuforums.org/archive/index.php/t-462494.html)

I'm not sure how the steps will work from a LiveCD, however.  It may be able to make the change and just restart X, but not the whole machine.

---

### Post by Fred Doolie on 2007-10-22
Well, once it boots up all is well so any changes wouldn't be needed after that. A  full install works fine too so it's something that the live cd is doing or not doing. 
It's only a cold reboot from the live CD that is the problem and only on my desktop unit.

But thanks

---

### Post by Fred Doolie on 2007-10-23
Solved!

Hint:
After a LONG time of orange bar moving the screen changes to text and SLOOOWLY displays multiple I/O errors about fd0: and fd1:
I don't have any floppy devices!!! A lightbulb appears above my head. 

Solution:
Searched the BIOS and found some onboard devices. I disabled the onboard floppy controller (Device FDC).

It works fine now.

---

