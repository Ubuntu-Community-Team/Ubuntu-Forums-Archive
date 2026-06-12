---
title: "[Ubuntu 15.04] Graphical problems after a fresh install"
date: 2015-08-13
forum: General Help
---

### Post by Planetouched on 2015-08-13
I've just changed my HDD for a SSD and decided to make a fresh install of Ubuntu 15.4 instead of cloning my HDD. 

 **My hardware: **
CPU AMD 64 bits 
GPU Nvidia GTX 460M, currently running on a version of the Nvidia drivers installed through Drivers. 

 I've been struggling to make Steam work, trying different versions of the Nvidia driver through Drivers, and it doesn't yet. 
It does appear on the launcher, display options when right-clicking on it, but no Steam window appear. It never asked my login/password.  I would have labelled it a Steam problem, but surprisingly Synaptic shows the same behaviour: it asks for password, displays some information at 1st launch, can be right-clicked on on the launcher, but no window. 

I can't use Synaptic for the moment and I'm not quite comfortable with that. All my other programs seem to run just fine for the moment, including Ubuntu Software Center.  More subtle, when creating a file in my desktop directory it won't appear on the Desktop. Conversely, when created on the desktop the file appears in the desktop directory. Odd. 

 When loading, Ubuntu displays "ACPI PCC probe failed", as a consequence - I think - of using Nvidia drivers, but it also did on my HDD and I had none of these other problems. 
 I will gladly produce any information that could help solving these issues! Thanks in advance! 

 **[Edit]** I've just tried Spring, the portable RTS. The lobby works just fine, but the game runs without displaying anything. I can hear it running, but no game window will show. For the records it perfectly worked on my HDD on Ubuntu 15.04 with Nvidia drivers. 

 **[Edit 2]** Same problem with VLC while using the Nouveau open-source drivers: I can hear the sound but no video will show.  **[Edit 3]** Still with the Nouveau drivers, when running TuxCard and clicking on the icon again in the Launcher the Desktop appears, in slightly tune-down colours. It seems to me it is slightly different from showing no window: I wonder if TuxCard's window wasn't transparent. When I close TuxCard, the Desktop come back to its normal, slightly brighter colours. Meanwhile, CherryTree, a similar text editor, runs fine.

---

### Post by Planetouched on 2015-08-13
And now, for seemingly no reason, Firefox fails me after a reboot (no window again). Chromium, however, still works.
I would be very grateful for any hint!

**[Edit]** Now this is interesting: Displays (aka unity-control-center) crashes. The log says:

> UnreportableReason
You have some obsolete package versions installed Please upgrade the following packages and check if the problem still occurs:
libblkud1, libmount1, libsmartcols1, libuuid1, mount, nautilus-data, util-linux, uuid-runtime

However, without Synaptic, it looks like a deadend.

---

### Post by Planetouched on 2015-08-14
Deus ex machina this morning!    Almost everything seems to work again: 

  - Firefox, Tuxcards, Vlc and most importantly Synaptic work normally. 
 - document created in the desktop folder can be seen on Desktop 

   However, 
 - Springlobby's window won't show, Spring doesn't run;
 - Steam still doesn't work. 

   What could have possibly solved most of the issues is a "better" (luckier? It seems so random, newer might not be best) choice of proprietary drivers (which is version 340.76 for me) + reboot, and/or a software update. I still have to solve issues about Steam and games. Maybe this is time to close this thread, since my next questions will certainly be more specific anyhow.

**[Edit]**
Nope.   I thought most issues were solved, but after a reboot they're definitely not. Icons are missing again on Desktop. Programs randomly won't show their windows. I had to reboot twice to make Firefox "work" (why is it even working the 2nd time?)  I'm running out of ideas and I'm still in dire need for help.

---

### Post by Planetouched on 2015-08-14
Well, I'm back to the nouveau open-source drivers. Everything seems to behave normally after a reboot. 

I might also have solved my Steam problem. If I understand correctly **Steam won't install on 15.04 **! 
There is a work-around though, and the answer provided here seems to work for me (didn't try any game yet but the Steam app is definitely running): 

  [http://askubuntu.com/questions/635851/error-in-installing-steam-on-ubuntu-15-04](http://askubuntu.com/questions/635851/error-in-installing-steam-on-ubuntu-15-04) 

 Still need to do some testing to see if everything is OK but moral is raising.

---

### Post by Planetouched on 2015-08-14
This time I might have solved my main problem. 

    Oddly enough, when installing, Ubuntu 15.04 decided I had a 2nd screen - which is false, I've never had 2 screens.    My missing windows must have appeared on this phantom screen. I've switched back to a 1 screen display and the windows that wouldn't display now do, without reboot. 

   The question is: why the **** did Ubuntu detect and install a 17" Micom Communications screen (never heard of this brand) when none existed. 

   I believe this thread can now be flagged "solved" and closed, thanks for watching.

---

