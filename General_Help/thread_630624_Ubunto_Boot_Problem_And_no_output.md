---
title: "Ubunto Boot Problem *And no output"
date: 2007-12-03
forum: General Help
---

### Post by Guardian-Mage on 2007-12-03
I've been having a few problems with booting lately. First, Ubuntu is installed on an internal hard drive(80GB) on partition #2(#1 is 50gb Windows XP Partition). /home and /usr are located on an external USB Hard drive(250gb). Everything went fine for a while, but now I get boot problems.

I have changed my boot screen to one that I found on gnome-look. Some silver Ubuntu Splash screen, and I changed it using boot-up manager(Or start-up manager, not sure of the name). My resolution has also been changed with that utility. Now my boot up will get to "Checking Local File Systems" and stops. First it will just pause, than the USplash disappears leaving me with a EMPTY screen, only a cursor remaining. Normally when it does that, it says starting a maintenance shell. But not any more. So I restart my computer and try several more times. Nothing. So I restart again, go into grub and delete the quiet line by itself and in the kernel line. Now when It boots it displays a blue box below the boot screen progress bar that gives output. When it gets to the freezing point I see the line "Entering a maintenance shell, press CONTROL + D to exit". I leave it and it goes to a empty black screen with a cursor. So I restart again, change the same GRUB parameters, and try again. When it gets to the freezing point, I press CONTROL + D and it keeps going. It gets to the vary end, the Progress Bar is full, and the blue output box reads "Loading local boot scripts" or something similar. Than nothing. IT freezes for a while, than goes to an empty black screen with a cursor. CONTROL + D doesn't work. Nothing does. It seems to freeze at it loads GDM or something.

There, I tried to be as detailed as possible, please help, I need Ubuntu :popcorn:

---

### Post by mozkill on 2007-12-03
this is a known issue with the 64-bit version of Gutsy.  it seems like they will fix it soon.  check the Ubuntu Guide.

---

