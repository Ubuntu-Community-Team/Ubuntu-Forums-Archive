---
title: "AppImage broken after upgrade to 21.10"
date: 2021-11-17
forum: General Help
---

### Post by barrymmm on 2021-11-17
Just upgraded from 20.04 to 21.10 and I notice that AppImage doesn't work properly. FreeCAD doesn't work but BalenaEtcher does. I can see the splash screen so it looks like FreeCAD is starting up but nothing happens after that. 
AppImage issue or Ubuntu?

---

### Post by TheFu on 2021-11-18
If 1 appimage program doesn't work, that's very different than 50 appimage programs not working.  It is likely the developer of the package has assumed some underlying libraries exist which have been updated.  Their appimage package either needs to include those libraries too or migrate to the newer libraries provided by 21.10.

I think 21.10 Ubuntu changed from Gnome3 to Gnome4 and likely switched from GTK+ 3.x to GTK+ 4.x libraries. That's a major difference.  In the short term, you might look into manually loading the GTK+ 3.x libraries - assuming those are the symbols being reported as unavailable.  Best to run the appimage from a shell to see all the output - not by clicking in any menu.

This is not an Ubuntu issue.  Contact the appimage package team for each program that doesn't work.

---

### Post by barrymmm on 2021-11-19
I have a 50/50 mix of working and not working:
Working: Balena Etcher & Super Slicer
Not Working: FreeCAD & Idea Maker
Both of the "not working" programs do the same thing - show the splash screen and then nothing. I tried a couple of different versions of FreeCAD and both still behave exactly the same. It may be a library thing but I don't know where to even start troubleshooting this. 
Has anyone else experienced this or am I on my own here?

---

### Post by TheFu on 2021-11-19
Open a terminal and run the AppImage directly.

What errors are shown?

Send those errors to the team that made the appimage along with your current ubuntu release and kernel.

Wait. Hope.  Pray.

---

### Post by monkeybrain20122 on 2021-11-19
Just delete their configuration files and run again. If you "upgrade" chances are you got left over configurations that no longer works. Some Appimages might assume certain system lib versions so they won't work. Download a newer version and try again in that case.

---

### Post by barrymmm on 2021-11-21
Ran FreeCAD from terminal and got the following:

> libGL error: MESA-LOADER: failed to open radeonsi: /usr/lib/dri/radeonsi_dri.so: cannot open shared object file: No such file or directory (search paths /usr/lib/x86_64-linux-gnu/dri:\$${ORIGIN}/dri:/usr/lib/dri, suffix _dri)
libGL error: failed to load driver: radeonsi
libGL error: MESA-LOADER: failed to open radeonsi: /usr/lib/dri/radeonsi_dri.so: cannot open shared object file: No such file or directory (search paths /usr/lib/x86_64-linux-gnu/dri:\$${ORIGIN}/dri:/usr/lib/dri, suffix _dri)
libGL error: failed to load driver: radeonsi
libGL error: MESA-LOADER: failed to open swrast: /usr/lib/dri/swrast_dri.so: cannot open shared object file: No such file or directory (search paths /usr/lib/x86_64-linux-gnu/dri:\$${ORIGIN}/dri:/usr/lib/dri, suffix _dri)
libGL error: failed to load driver: swrast
/tmp/.mount_FreeCAdmCavf/AppRun: line 41:  7974 Aborted                 (core dumped) ${MAIN} "$@"


Ran IdeaMaker from terminal and got the following:

> ideamaker.real: error while loading shared libraries: liblber-2.4.so.2: cannot open shared object file: No such file or directory


To be honest this is way over my head. Looks like some kinda issue with my GPU and / or libraries.

---

### Post by monkeybrain20122 on 2021-11-21
Are you on Wayland?

Also see this [https://forum.freecadweb.org/viewtopic.php?style=5&t=62932](https://forum.freecadweb.org/viewtopic.php?style=5&t=62932)

---

### Post by TheFu on 2021-11-22
> **barrymmm said:**
> Ran FreeCAD from terminal and got the following:
 
To be honest this is way over my head. Looks like some kinda issue with my GPU and / or libraries.

It is missing dependencies.  If you don't have an ATI Radeo GPU, then it is worse since something had determined, incorrectly, that you should have DRM libraries for Radeon.

It looks exactly like my first post suggested.  Send the errors to the appimage project and wait, hope, .... they will actually take action.  That's the "correct" answer.  You could search out where those exact libraries are supposed to be provided (the package) and attempt to install them. Pay attention to the revision for the libs. You'll want to be close. If your system already has a library that is close, you might be able to create a symlink with the name the appimage seeks to the version your system has.

---

