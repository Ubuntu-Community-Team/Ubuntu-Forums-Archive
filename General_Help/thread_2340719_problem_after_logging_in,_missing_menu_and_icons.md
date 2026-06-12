---
title: "problem after logging in, missing menu and icons"
date: 2016-10-21
forum: General Help
---

### Post by tigi on 2016-10-21
I have a problem i don't even know how to search help for.
On my desktop I have running xubuntu for long time (i think it was distribution 14.10) with auto-updates disabled.
This morning i have decided to apply all security updates from the update GUI menu of xubuntu (without typing anything on any terminal window).
The update process appear to run normally and after a few minutes it asked me to reboot. I did it.
After restart, i get the normal log-in view (see attachment Xubuntu_Log_in_screen.jpg).
After loogging in, i see the desktop background theme, without any icon or menu.
The mouse pointer symbol appears normally and i can move it.
I tried to right-click, and nothing happens (no menu).
I tried to move the pointer to all the sides of the screen, hold for some time, click while the pointer is pushed to a side, and got no effect.
So i cannot do (almost) anything (no terminal, etc), with the exception of typing cntrl-alt-backspace, which takes me back to the log-in screen.

Any help ?

 tigi

---

### Post by tigi on 2016-10-21
i have also tried to change the settings of my monitor (working directly on the flat screen) to see if there was a menu or icon outside the visbe area and i have not found any. So it is not a problem of adjusting to the size of the monitor.

---

### Post by tigi on 2016-10-21
inspired by:   [https://ubuntuforums.org/showthread.php?t=2245002&highlight=log+missing+menu](https://ubuntuforums.org/showthread.php?t=2245002&highlight=log+missing+menu)
 
 at the login screen key combo ctl+alt+F1 , got a terminal console; 
 i logged in as user "amministratore".  It returns:
 
 Welcome to Ubuntu 14.04.5 LTS
 ...
 
 WARNING: Security updates for your current Hardware Enablement Stack ended on 2016-08-04:
  * [http://wiki.ubuntu.com/1404_HWE_EOL](http://wiki.ubuntu.com/1404_HWE_EOL)
 
 ...
 
 
 
I can do 
   ls -al .Xauthority
and get:
 -rw------- 1 amministratore amministratore [...]

---

### Post by tigi on 2016-10-21
On the terminal console, i type:

$ sudo apt-get update
$ sudo apt-get upgrade

reboot. same problem (no improvement).

$ startxfce4

...
Fatal server error:
(EE) Server is already active for display 0
 If this server is no longer running, remove /tmp/.X0-lock
    and start again.
    
So i type:
$ sudo rm /tmp/.X0-lock

$ sudo poweroff

Restart, no improvement.

---

### Post by tigi on 2016-10-21
i have tried also the solution of this thread:  [https://ubuntuforums.org/showthread.php?t=2331661](https://ubuntuforums.org/showthread.php?t=2331661)

 but still no effect.

---

### Post by tigi on 2016-10-22
i have re-installed Xubuntu , reformatting the HDD

---

