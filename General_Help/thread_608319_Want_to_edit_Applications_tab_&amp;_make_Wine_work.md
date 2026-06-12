---
title: "Want to edit Applications tab &amp; make Wine work~"
date: 2007-11-09
forum: General Help
---

### Post by phreakshew on 2007-11-09
Hello all!  This is my first time running Wine so please bear with me.

I have been RTFM but I cannot find the answers to my questions which is why I'm here...

Running Ubuntu - Feisty 7.04 with Wine ver. 0.9.47. 

Downloaded and installed simple, silly game (Truck Dismount) for windows.

Installed correctly, but in order to run the game I have to open a terminal and type winefile, then find c:drive, and truckdismount.exe

Under the Applications tab in my menu bar there is: Wine - Programs - Truck Dismount - Truck Dismount & Truck Dismount (no sound).  

I can follow this path to play the game with no sound, but it hangs when I try the other one (with sound enabled).  Works fine if I open it from winefile in a terminal.  (There is no winefile listed under Applications tab)

So, I first tried to edit the Applications menu to make sure the path to the game was correct. Both of them point to: 
env WINEPREFIX="/home/guest/.wine" wine "C:\Program Files\Truck Dismount\truckdismount.exe"

Went to the .exe file itself and right clicked,  clicked properties, & made it open with wine.  That made it work for a couple times, then it started hanging on startup again, unless I open it through winefile.

Tried creating a new launcher for the game on the desktop, but it did not work.  Said it could not open program, needed .dat file.

My questions are:
How can I get the program to run from a launcher, either on the desktop or from the path listed in the Applications tab on my menu bar?

How can I add a winefile entry to the Applications tab?

Thatnk you very much for your time.

---

