---
title: "A Couple Questions`"
date: 2008-04-26
forum: General Help
---

### Post by riverlethe on 2008-04-26
I just installed Ubuntu 8.04 with Wubi, and I'm very impressed.  Everything worked immediately, and it even downloaded and installed Nvidia drivers with little effort.

I have a couple quick questions to make Ubuntu look as good as Vista.

1. Is it possible to stop window tearing when I move a window?  This really bothers me after using Vista.

2. How do I get shadows under menus and windows?

---

### Post by HunterThomson on 2008-04-26
Ubuntu will look way better then Vi$ta once you enable desktop effects (compiz). Open Add/remove programs and search compiz and install a advanced compiz effects configuration tool, too really spice up your desktop.

---

### Post by riverlethe on 2008-04-26
I have "extra" desktop effects enabled, and I just installed the utility you recommended, but I can't find the two options I mentioned.  Can you give me a hint? :)

---

### Post by tamoneya on 2008-04-26
you should also take a look in restricted drivers.  It sounds like you are not using the correct driver for your graphics card and it is causing issues.
System->administration -> hardware drivers

---

### Post by riverlethe on 2008-04-26
I am using the "proprietary" driver, but it does not give a version number.

---

### Post by HunterThomson on 2008-04-26
Owe, so all is looking cool you just want the shadows? Ok, well there should be the option I don't know exactly where it is but I am sure the option is there somewhere. Look around, sorry I could not be more of a help.

---

### Post by riverlethe on 2008-04-26
All is not cool!  I have window tearing. :P

Edit: "Window decorations" are also enabled with a shadow radius of 9, but I have no shadow.

---

### Post by HunterThomson on 2008-04-26
I don't know what you mean exactly "window tarring". Try changing the effects with the windows to something ells. I know there are a lot of options.

---

### Post by HunterThomson on 2008-04-26
I have only used Linux for a month or so and I love it and would never go back to window$ Never Never Never.... But one thing I have found is that some stupid little things mite not work but all the important things and 99% of the non-important things work way better then in window$. With that said wait for some one with more experience to give you advice on this subject and don't take my word for it.

---

### Post by riverlethe on 2008-04-26
"Window tearing" is when windows appear to "break up" when you move them.  The same thing happens in games if you have a frame rate higher than the refresh rate of the display.  I believe it's a result of not having vertical sync on the desktop, as Vista appears to (I think the MacOS does as well, which is where MS got the idea. ;-)).

---

### Post by Person98 on 2008-04-26
what kind of graphics card do you have, if it is ATI there are alot of threads on how to get better preformance out of it with some minor tweaks, not so sure about nvidia, but getting it running to it's best should help stop the tearing, also you can add vsync using +vsync at the end of your modeline in your monitor sectoin of your xorg.conf

---

### Post by riverlethe on 2008-04-26
It's an 8800 640MB GTS.  For some reason, the display configuration window also seems to think my flat panel is 50 Hz...

---

### Post by Person98 on 2008-04-26
alright, if you want to add the vsync option might help you, just open up your Xorg file for editing 

sudo gedit /etc/X11/xorg.conf

then find: Section "Monitor"
there will be a line called modeline with a bunch of resolutions listed, at the end of it add +vsync

and then reboot x using ctrl alt backspace

---

### Post by riverlethe on 2008-04-26
I will try that when I boot back into Ubuntu.  Do you know how to see which version of the Nvidia drivers I have installed?

---

### Post by Person98 on 2008-04-26
oh yeah forgot to mention remember to always back up your .conf files before editing 

sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.backup

makes a copy with the new name if it breaks anything you can just copy the backup over the broken one.
As for driver version i am not totally sure but you should be good with the one you get when you go to the hardware drivers menu and enable the nvidia proprietary driver

---

### Post by riverlethe on 2008-04-26
There is no modeline.  It just says: 

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

---

### Post by riverlethe on 2008-04-27
Nobody knows?

---

### Post by Zorael on 2008-04-27
There should be an 'Nvidia settings' app in your Applications menu someplace? Else just run it from a run box (Alt+F2).
```
$ nvidia-settings
```
If it can't find it, you may have to install the nvidia-settings package.


Go through the tabs and check everything that has to do with vertical sync. Also, if running Compiz and you have ccsm installed (compizconfig-settings-manager), go into General Options, Display settings (or something similar). There should be a vertical sync option there.

I get slowdowns if I check Detect Framerate in there, so I just use the slider and put it at the refresh rate my monitor uses (flatscreen so 60hz).

---

