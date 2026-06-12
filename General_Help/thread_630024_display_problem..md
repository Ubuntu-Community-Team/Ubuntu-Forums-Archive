---
title: "display problem."
date: 2007-12-02
forum: General Help
---

### Post by sYnOnYx on 2007-12-02
i searched already and couldnt find anything pertaining to my problem so here goes :

My ubuntu was running great for awhile now. but i recently got a widescreen monitor 1440x900 . the resolution 1280x1024 i was using is perfect but the screen appeared 1/2 inch below the top of the monitor. so i went in and changed the screen size, to the correct 1440x900. it said i need to restart before changes would take effect. i then restared the computer, and got a "signal out of range" error on my monitor and cannot get it to load up. i can get to the ctrl+alt+f1 screen though. 

anybody know a way i can get back to the old settings ??? and ill just adjust the screen through the monitor. all my display drivers are up to date aswell.

thanks in advance.

---

### Post by sYnOnYx on 2007-12-02
im also getting a "cannot load display" when i try to do anything in the terminal.

---

### Post by zvacet on 2007-12-03
Boot in recovery mode and run

```
dpkg-reconfigure xserver-xorg
```

---

