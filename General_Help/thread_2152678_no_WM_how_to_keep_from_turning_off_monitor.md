---
title: "no WM how to keep from turning off monitor?"
date: 2013-06-08
forum: General Help
---

### Post by EKRboi on 2013-06-08
First let me give a little background of the setup I am running. Started with Ubuntu mini AMD64 13.04, and have only installed what was necessary to get XBMC running in standalone and emulators going. So nvidia drivers, emulators, xboxdrv for my wireless xbox controllers, power management, X11 etc... I am starting up XBMC in standalone with an upstart script and it will run for hours just sitting there or playing videos if I don't set any sleep or shutdown timer options in it. When using emulators it was sending xbox controller presses to both xbmc and the emulators so I could hear xbmc "moving" around in the background and it was causing other problems as well. so instead of calling the emu directly from XBMC I created a script to do it that would killall -STOP xbmc.bin then run the emulator and then after killall -CONT xbmc.bin. And this works great! even solved some issues with the rom collection browser in XBMC from freaking out and crashing sometimes when closing an emu. 

Now onto the last issue with this setup that I cannot seem to figure out. I have set consoleblank=0 in grub, I have added post-start exec setterm -blank 0 -powersave off line to all the /etc/init/tty* files.. I assume xbmc when running keeps whatever is causing my monitor (TV) to blank out at bay but because I -STOP it, it is not doing it. So when running an emu after about 10-15 minutes it blanks out my monitor until a keyboard button is pressed. I know a dirty fix would be to just make a script that loops and sends a key stroke every now and again and just call it from my emu launch script... but there has to be a config file somewhere that sets these timeout times that I can just 0 out, but I have had no luck in locating it.

obviously the upstart script uses xinit to start the xsesseion for XBMC... where would the config that deals with the xsessions power management be? I have poked around and have not found it!?!

SOLVED! check below @ post #5

---

### Post by realestateworld on 2013-06-08
[COLOR=#333333]One thing to try that *may*  work. Open nvidia-settings and go to the powermizer section. Choose  "Maximum Performance" in the drop-down, and you should see your  powermizer level jump to the fastest speed.[/COLOR][COLOR=#333333]
Once you've done that, try the video.[/COLOR][FONT=tahoma][COLOR=#333333]In the past, I've found that vsync doesn't work when the nvidia card is on the slowest powermizer setting.[/COLOR][/FONT]

---

### Post by EKRboi on 2013-06-08
thanks for the reply but I am not running full Ubuntu.. there is no desktop environment. I have loaded a base ubuntu system (loads to command line) then added only what I needed from there to get XBMC running.

---

### Post by JKyleOKC on 2013-06-08
It sounds as if xscreensaver might be cutting in and cutting off the monitor. Without a window manager and GUI for setting things, I'm not certain how to go about turning it off, but the starting point might be the /etc/X11 directory...

---

### Post by EKRboi on 2013-06-08
> **JKyleOKC said:**
> It sounds as if xscreensaver might be cutting in and cutting off the monitor. Without a window manager and GUI for setting things, I'm not certain how to go about turning it off, but the starting point might be the /etc/X11 directory...

well I feel kind of dumb.. I did not even have a xorg.conf so I am sure X was just loading defaults. I created one and added the following lines to it as well as removing the DPMS option from the "Monitor" section and am currently testing by letting an emu run Zelda while I am running around the house doing chores (honey do list)... fingers crossed!

```

Section "ServerFlags"
        Option "blank time" "0"
        Option "standby time" "0"
        Option "suspend time" "0"
        Option "off time" "0"
        Option "dpms" "false"
EndSection

```

EDIT: That did the trick.. talk about feeling like a total noob =/ while not new by any means to ubuntu or linux in general.. this is my first minimalistic installation. I have found in this adventure that it is the small things like this that you take for granted with a desktop environment.

---

### Post by JKyleOKC on 2013-06-08
Glad to have helped! Seems like it's always the small stuff that trips us up...

---

