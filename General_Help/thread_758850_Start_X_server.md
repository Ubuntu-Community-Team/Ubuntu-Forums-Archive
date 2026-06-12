---
title: "Start X server"
date: 2008-04-18
forum: General Help
---

### Post by LasseNC on 2008-04-18
Hello forum! 

I was trying to optimize WorldofWarcraft and went through the troubleshooting guide that said 

```
 /etc/init.d/gdm stop          # this will shutdown your X Server!
```

And now I can't start up in graphical mode.

It shows a blue screen that reads that it started to start it 6 times in 90 seconds.

How do I start this again?

Kind regards, Lasse

---

### Post by TeoBigusGeekus on 2008-04-18
Can you type anything? If so, try
```
startx
```

If that doesn't work, try
```
sudo dpkg-reconfigure xserver-xorg
```
to reconfigure your gui.

---

### Post by aktiwers on 2008-04-18
```
sudo /etc/init.d/gdm stop 
```
```
sudo killall gdm
```

```
sudo /etc/init.d/gdm start
```
or
```
startx
```

Does that not work?

---

### Post by LasseNC on 2008-04-18
Running the startx command opened the graphical user interface and logged me in as a temp user.

When trying to log out of  the temp user the system crashed.

After reboot, I get same error, will try the other suggested commands

---

### Post by aktiwers on 2008-04-18
Hey are you trying to install the official Nvidia drivers?

---

### Post by LasseNC on 2008-04-18
When running

 ```
sudo /etc/init.d/gdm start
```

It just tries a number of times and show the blue screen again. 

When starting with 

```
startx
```

I get an error message that reads "User switcher has ended unexpectedly" 

And then I have the option of "Don't reload" and "Reload" pushing reload does not work.

---

### Post by LasseNC on 2008-04-18
> **aktiwers said:**
> Hey are you trying to install the official Nvidia drivers?

I run ATI

---

### Post by LasseNC on 2008-04-18
Problem solved. Semi. 

Ran ```
sudo dpkg-reconfigure xserver-xorg
```

Went through the guide without knowing anything, after that I started xserver using:

```
sudo /etc/init.d/gdm start
```

I am now able to see the graphics as earlier. But now when I booted it up, I get this error

"Internal error

failed to initialize HAL!"

And system freezes when pushing the shutdown button.

Reason for shutting down xserver in the first place was because of lag in WoW.

---

### Post by TeoBigusGeekus on 2008-04-18
[http://ubuntuforums.org/showthread.php?t=291130]("http://ubuntuforums.org/showthread.php?t=291130")

---

### Post by LasseNC on 2008-04-18
Don't have the HAL issue any longer, thanks for the help, everything seems normal now! 

Thanks for the very quick help!

---

### Post by LasseNC on 2008-04-19
After I reconfigured my  gui, all games (RtCW: ET is one) lags and all textures are weird looking. 

Are there any automatic configuration that can detect better settings or something like that?

Update:

Running this guide: [http://www.freesoftwaremagazine.com/columns/how_to_fix_your_computers_graphics_with_dpkg-reconfigure](http://www.freesoftwaremagazine.com/columns/how_to_fix_your_computers_graphics_with_dpkg-reconfigure)

I changed to the fgrlx driver instead of ati, game now crashes on startup.

> 
***********************************************************
 You are using software Mesa (no hardware acceleration)!   
 Driver DLL used: libGL.so.1
 If this is intentional, add
       "+set r_allowSoftwareGL 1"
 to the command line when starting the game.
***********************************************************
...WARNING: could not set the given mode (4)
Initializing OpenGL display
...setting mode 3: 640 480
Using XFree86-VidModeExtension Version 2.2
XF86DGA Mouse (Version 2.0) initialized
XFree86-VidModeExtension Activated at 640x480
Received signal 11, exiting...


So OpenGL does no longer work?

Update:

Returned to the ati driver, the messed up graphics and lag persists in RtCW:ET

---

