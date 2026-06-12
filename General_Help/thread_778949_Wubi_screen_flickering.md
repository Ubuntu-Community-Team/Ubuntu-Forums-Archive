---
title: "Wubi screen flickering"
date: 2008-05-02
forum: General Help
---

### Post by wilsonq77 on 2008-05-02
I have tried to load Ubuntu within Windows Xp sp2, several times and each time Wubi goes well though the first screen (i.e. the choose language etc. one)and all is fine.   When I hit install I get a rapdly flickering orange screen which I cannot read.  I have tried all of the ctrl-alt-+ options and the best I can get is some jagged lines.  The VGA signal is a bunch of vetical lines of zibberish.
I have a Geforce 7900 with the latest drive installed. Windows resolution is 1920x1200. I have also verified the iso. I have 4gb of RAM and over 100gb of empty disk space.  And I am puzzled?  Anyone know an answer, please???

---

### Post by ago on 2008-05-02
Did you try to press ESC at boot and select the Safe Graphic Mode?

---

### Post by wilsonq77 on 2008-05-02
I did that.  I can get to the tty and the kernel is there.  But, because I can't see the Wubi pages I can't answer the questions about partitioning etc.  So only the kernel loads.  There is no desktop etc.  No graphic gui in sight.

It is odd that I can see the logo and the first page (the language page) then once I try to install the screen corruption is so bad it is unreadable. I could be that Ubuntu takes over at that point and there is a driver issue.  I tried to get the new driver to load but sh could not find the file from Nvidia.

I may have to resort to the old way to load.

---

### Post by ago on 2008-05-03
Try the Live CD, in theory there should be no difference though

---

### Post by wilsonq77 on 2008-05-03
I tried the Live CD first and that is when the problem first popped up.  The load off my hard drive was the first step in finding a solution, inspired by the sticky up there.  It was a test to see if the CD was really good even though I checked it with the CD-based check.

Even when I got the kernel to load all I can access is the TTY and ash. Since I can't see the questions on the remaining Wubi screens I can't answer the questions and it seems all that loads is the kernel.  No GUI at all.


See the screen corruption thread too.  We both have the same issue.

---

### Post by wilsonq77 on 2008-05-03
Okay, I worked out a partial solution.  Thanks to AGO and the sticky up there.

I downloaded a new Wubi 8.04 to its own folder on the C: drive.  I moved the iso to that folder and ran Wubi.exe and it started.
On the first boot you have to get to that esc key really fast.  Otherwise the loader get going and all the choices that pop up on the boot menu are normal or recovery mode.  If you get to the esc fast, ASAP (emphases needed) then you get the menu with "safe graphics mode".  For some reason Wubi will default to manual.  Click the "install" icon on the desktop and fill in the stuff.  At the partitioner you need to add a / and /usr and a swap into the empty space and after about 5 minutes of making mistakes you get running.

The screen coruption is still there in normal mode.  I'll try to get new drivers loaded as time permits.

But hey, if you use "safe graphics mode" she all works :)

---

