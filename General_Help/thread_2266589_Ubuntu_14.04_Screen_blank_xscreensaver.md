---
title: "Ubuntu 14.04 Screen blank xscreensaver"
date: 2015-02-24
forum: General Help
---

### Post by greg73 on 2015-02-24
Hiya all, I have looked everywhere on here to make sure this has not already been asked. I could not find anything specifically like this... I found a couple similar and checked but made no difference.

I have Ubuntu 14.04 on a laptop Samsung RV511 and have installed xscreensaver. (My previous older laptop worked fine) yes, I have  removed gnome-screensaver.... What i am finding now is instead of the screensaver starting all i am getting is a black screen showing the curser arrow.... If i go into xscreensaver and then click on one of the screensavers it runs fine in show .... but does not seem to want to run when screensaver should start.

Any help would be greatly appreciated. thank you in advance :)
Greg

---

### Post by ajgreeny on 2015-02-24
How is xscreensaver started in normal use; what command do you have in the startup-applications list?  You need **xscreensaver -no-splash** as the command so try that if you have something else.

Which specific screensaver are you using in the xscreensaver listing, as I have found that on a previous machine some of those theoretically available in the list would not run but crash the computer.

---

### Post by greg73 on 2015-02-25
Hello ajgreeny, thank you for replying :). I have used it before when had 14.04 on another laptop and yes I know there is some that will not work specifically "pacman" is one that comes to mind. i only have it alternating between some that i do know work and have used with success before.... in startup i have name: xscreensaver  Command: xscreensaver -no-splash

As to the ones i have active or ticked they are; Anemotaxis, blaster, boxed, ccurve, celtic, drift, endgame, epicycle, euler2d, flame, galaxy, gears, glcells, glknots, glsnake, grav, helix, hilbert, jigsaw, kaleidescope, maze, molecule, noof, penetrate, pinion, pipes, polyhedra, pong, rorschach, sproingies, squiral, starwars surfaces, xrayswarm, xspirograph

Thank you for assisting me in this :).

---

### Post by ajgreeny on 2015-02-25
Are you sure you have the **xscreensaver-gl-extra** package installed?  Most of the screensavers you list are in that package which is not installed by default.

---

### Post by greg73 on 2015-02-25
ummmm very good question......not sure if i have or have not.... is there a simple way i can tell???

---

### Post by ajgreeny on 2015-02-25
> **greg73 said:**
> ummmm very good question......not sure if i have or have not.... is there a simple way i can tell???
Look in software-center, assuming that will tell you (I never use it) or better in my opinion, synaptic, and use the search by "Name" only button for any packages.

Or just try to install it in terminal and you will be told if it is already installed.

---

### Post by greg73 on 2015-02-26
Hello ajgreenym  i have checked, yes, it is installed...

---

### Post by ajgreeny on 2015-02-26
In that case I have no idea other than questioning whether your graphics are good enough to run gl applications.  What graphic card do you have or is this an integrated GPU on the processor?  Do you suffer any other graphics glitches?

---

### Post by greg73 on 2015-02-27
i wondered that too.... but this laptop is actually a lot higher spec than my last laptop yet it run fine on that one.... and as said originally... if go into preview it runs them fine..... it just will not when the screensaver is run naturally after 10 minutes... but i thank you for your assistance and time ajgreeny :) as to other graphic gliches... no none it is the standard graphics which comes with the samsung rv511

---

### Post by greg73 on 2015-02-28
ok have solved it and worked out what the problem was.... in the end... so simple.....in System Settings > Brightness and Lock > Turn screen off when inactive   set to never

---

### Post by ajgreeny on 2015-03-01
Ah yes!

That light-locker setting catches a lot of people out; I should have thought about it, but totally forgot.
I always disable light-locker on my system as one of the first things I do; to me it is more annoying than useful, and I prefer to see all my photos randomly displayed as my screensaver.

It's surprising how many pictures suddenly appear and remind me of a great time or holiday!

---

