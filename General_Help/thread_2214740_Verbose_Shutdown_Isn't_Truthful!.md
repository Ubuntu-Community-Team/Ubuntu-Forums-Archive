---
title: "Verbose Shutdown Isn't Truthful!"
date: 2014-04-02
forum: General Help
---

### Post by ~zoey~ on 2014-04-02
I'm running ubuntu 12.04 with an Intel DG33TL motherboard, an Intel Core 2 Duo CPU processor, a Netgear network card, and an Intel G33x86/mmx/sse2 graphics card.  The system reboots OK, but it has not shutdown properly since it was installed.  It won't resume from suspend either.  I switched to verbose shutdown, but everything down the line shows OK.  The last four lines are;                          unmount/run/lock: not mounted
                                           unmount /run/shm: not mounted
                                           *will now halt
                                           [506.311109]  Power down
But the computer is still running; the light on the front is still on and I can hear the fans, so I have to hold in the power button to stop it.  I haven't a clue how to fix this, and I would appreciate any suggestions.  According to the searches that I have done, I am not alone with this problem.
                   Thanks :confused:

---

### Post by Jonor on 2014-04-03
Sometimes happens to me. Two routines that often help :
1. Make sure everything is up to date via a terminal :
 sudo apt-get update && sudo apt-get upgrade
2. Do the hard shutdown holding the power button down, turn the power supply unit's switch off, usually found at 
 the back of a desktop computer, turn the mains supply wall socket to the computer off (or pull the power supply cord out of the 
 back of the computer if this is more practical), wait a minute and reverse back through the last few steps to rebooting.
 Don't skip any of this as the mobo can still be powered even with the switch at the back off.
All this will provide the mobo with the sometimes needed completely cold restart.

---

### Post by ~zoey~ on 2014-04-03
> **Jonor said:**
> Sometimes happens to me. Two routines that often help :
1. Make sure everything is up to date via a terminal :
 sudo apt-get update && sudo apt-get upgrade
2. Do the hard shutdown holding the power button down, turn the power supply unit's switch off, usually found at 
 the back of a desktop computer, turn the mains supply wall socket to the computer off (or pull the power supply cord out of the 
 back of the computer if this is more practical), wait a minute and reverse back through the last few steps to rebooting.
 Don't skip any of this as the mobo can still be powered even with the switch at the back off.
All this will provide the mobo with the sometimes needed completely cold restart.

Thank you Jonor,  I tried it, but it didn't work.  It looks to me like ubuntu is shutting down properly, because I can hear the hard drive spin down, so maybe there is a glitch in the motherboard.  Do you think that it would help if I reset the bios?

---

### Post by Jonor on 2014-04-03
If the problem only started from the Ubuntu install i'd be inclined to favour the culprit being something more to do with the OS rather than the BIOS.
Sometimes the fans/lights have gone for up to 5 minutes before stopping on my box.
That lasted a month or two then stopped happening on Gnome Ubuntu 12.10 i think, never had the problem on Gnome Ubuntu 12.04 which is my current OS.
There in not much more that i can say.

If you want to reset the BIOS and the box was inherited from someone else, make a note of the current BIOS settings for reference,
make sure if the mobo default is for PS2 mouse and keyboard that they are available and make multiple backups of important stuff with file permissions set accordingly.
If it is just a plaything with little to loose, remove all mains power and pop out the CMOS button cell battery on the mobo for 5 minutes before replacing it.
Best of luck with that last option, it has sometimes worked very well as a last resort !

---

