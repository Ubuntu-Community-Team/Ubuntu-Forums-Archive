---
title: "Menu Bar vanished from Gnome"
date: 2007-01-17
forum: General Help
---

### Post by oozydigg on 2007-01-17
On 6.10 my computer sometimes freezes up when I come back from hibernate.  Usually the screen displays a bunch of red lines.  I usually try to restart gnome using ctrl-alt-bksp, and if that doesn't work I reboot using RSEIUB.  

Today when the computer restarted the menu bar, the shutdown button, the drawer, and all my custom applications launchers were gone.  Both panels(at the top and bottom) looked very empty!

I have an ATI 9800 Pro card, but I'm just using the driver that installed from the live-cd.  I have NOT installed the proprietary driver.

What is going on?  I have had this happen before.  It was fixed with a restart, but not this time.  Is there any way I can get gnome back to the way it was before without redoing everything?

Thanks

---

### Post by awthomp on 2007-12-31
I'm experiencing the same problems oozydigg expressed.  With me, however, I have an NVidia 8500GT graphics card.  The menu bar is gone (sporadically), my desktop wallpaper is gone, and when I can actually click on the menu bar, the enabling of Compiz fails.

I did not change anything on my machine.  Rather, I turned it off, left it off for about two weeks, and turned it back on to experience these problems.

Thanks in advance for the help!

---

### Post by dhruv.bansal on 2008-06-26
Sometimes my panels disappear or become blank and even restarting GNOME (CTRL + ALT + BACKSPACE) doesn't work.

The fix I've found is to restart the process "gnome-terminal".  Likely, this process is already running so you'll have to kill it before you can restart it.  You can find it in System -> Administration -> System Monitor and kill it there and restart it by activating a termainl (Applications -> Accessories -> Terminal) and typing "gnome-terminal &" (make sure to include the trailing ampersand!).  My panels usually pop up at this point and I can close the terminal and continue working.  (You can also kill the process inside the terminal -- just type "ps aux | grep gnome-terminal" and find the PID of the gnome-terminal process and then type "kill -9 [PID]").

Not sure if this solves awthomp's problem with the wallpaper and Compiz (I've never been able to get Compiz to work with my proprietary graphics cards...).

---

