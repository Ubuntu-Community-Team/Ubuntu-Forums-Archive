---
title: "What is wrong with this??"
date: 2008-06-03
forum: General Help
---

### Post by MasterNetra on 2008-06-03
I'm trying to make a script to start Oblivion's Launcher while disabling Wine's Debug writes. (For better performance) I tried doing it based off the instructions from here:
 [http://ubuntuforums.org/showthread.php?t=349764&highlight=Oblivion](http://ubuntuforums.org/showthread.php?t=349764&highlight=Oblivion)

I am not sure whats wrong with it. so here it is.
----------------------------------------------------------------
export WINEDEBUG=fixme-all,err-all,warn-all,trace-all

OBLIVION_DIR= env WINEPREFIX="/home/owner/.wine/" wine "C:\Program Files\Bethesda Softworks\Oblivion\

cd ${OBLIVION_DIR} wine OblivionLauncher.exe
----------------------------------------------------------------
Also I am using the latest version of wine and the script is saved as a .sh file.

---

### Post by agamotto on 2008-06-03
To be honest with you, I wouldn't waste my time trying to get Oblivion to run under Linux.  It is unstable enough under Windows when you try to user higher resolutions and turn on the good stuff.

---

### Post by MasterNetra on 2008-06-03
Funny thing is it got a Gold rating from Wine's AppDatabase..
I run it on low settings anyway for performance. More interested in gameplay then making the graphics as pretty as possible.

At anyrate the question is with the script. Figuring it out may help with future games/apps.

---

