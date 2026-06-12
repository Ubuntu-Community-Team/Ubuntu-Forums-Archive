---
title: "Power Saving Options"
date: 2007-07-30
forum: General Help
---

### Post by charles909 on 2007-07-30
Hi All,

I wanted to make an Ubuntu (7.04) system running MythTV to help record all the shows I want to watch.  The system is totally dedicated to this and my one system is both a frontend and backend.  I have finally gotten everything working, but one thing is still missing.  I want it to be better at saving electricity, so for example, I want it to go on sleep mode when I am not watching TV and when I am not recording anything.  It should wake up when I go to watch TV or if it is time to record something.  Does anyone know how I can configure this?  I searched, but couldn't find anything relevant to this.

Here are the specs for this system:

eMachines T3612 (3.5Ghz Celeron D, 512mb ram, 120gb HD (SATA), 20gb HD (IDE), DVD Burner)
Hauppauge PVR150 w/ remote & IR blaster
Netgear Wireless
Motorola DCT2224 cable box
Ubuntu is installed on the 20gb HD

Thanks!

---

### Post by Paul S on 2007-07-30
Did you try Gnome Power Manager to set a hibernate or standby after a period of inactivity?

regards,

---

### Post by NilsE on 2007-07-30
I don't believe that you will be able to suspend or hibernate and wake up when an event on the PC happens since it will not be testing for events. ie. sleeping

You could however change things like when the screen goes to sleep, when the drive shuts down etc. in the Configuration editor or some of it in Power Manager itself. There are a whole bunch of options in gnome-power-manager section

---

### Post by charles909 on 2007-07-31
Thanks guys.  I will try gnome power manager.

---

### Post by chefele on 2007-08-03
FYI,  I believe the eMachines T3612 may have some BIOS bugs that might inhibit your ability to put the machine to sleep.

I have a T3612, and when booting Ubuntu it would complain about BIOS bugs, then run extremely slowly. The details about the problem & how I fixed it are in  [<this thread>]("http://ubuntuforums.org/showthread.php?t=476489&highlight=t3612")  Basically, to get the machine to run normally I had to add the boot parameter ACPI=off, which turns off power management. And of course with power management off, my machine won't sleep or power down without physically pressing the on/off button. 

So did you have to do the same thing?  If not, can you say if you did anything special to get the eMachines T3612 to boot normally?   Any tips would be appreciated!

---

