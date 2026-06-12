---
title: "unity launcher for mono program on a removable drive gets deleted"
date: 2013-12-03
forum: General Help
---

### Post by rclocher3 on 2013-12-03
Hi all,

I have a program that runs under mono.  It doesn't require installation, and I intend to run it from a USB flash drive formatted as FAT16 or FAT32.  There's no simple way to launch the program: I have to fire up either Nautilus or a terminal, navigate to the subfolder on the flash drive, and then either double-click on the .exe or type "mono ./programname.exe".  If I fire it up from Nautilus a mono terminal opens along with the program.  This is clumsy and annoying, so yesterday I created a launcher for the program and dragged it to the Unity toolbar.  I clicked the launcher, and the program launched without the annoying terminal window this time, great!  I shut down the program, turned off the computer, pocketed the USB flash drive, and went to bed.

This morning I fired up the computer and plugged in the USB flash drive, and went to launch the program---but my unity launcher is gone.  There must be some process that polices launchers and deletes any that refer to removable media that isn't present.  Ugh.

So what can I do?  Can I configure the system to stop policing my unity launchers?  Can I write a script to reinstall the launcher when the correct USB flash drive is mounted?  I can't guarantee that the USB flash drive will be present at startup.

- Rob

My background: I've only been running Linux and Ubuntu for a couple years, but I've been around computers for a long time.  I spent four years as a software engineer on various platforms.  I spent some time in the early nineties on Unix workstations, so I'm comfortable on the command line.  I'm relearning shell scripting as I go.

---

### Post by stinkeye on 2013-12-03
Maybe have the **Exec=** line in the .desktop point to a script on your local drive which 
then runs the application.

eg script
```
#!/bin/bash

cd /path/to/usbDrive
[COLOR="#696969"]<run command>[/COLOR]
```

---

### Post by rclocher3 on 2013-12-04
That's a sensible work-around, thanks!

- Rob

---

