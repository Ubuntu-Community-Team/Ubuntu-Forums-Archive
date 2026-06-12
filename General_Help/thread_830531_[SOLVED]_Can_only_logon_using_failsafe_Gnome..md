---
title: "[SOLVED] Can only logon using failsafe Gnome."
date: 2008-06-15
forum: General Help
---

### Post by CaKiwi on 2008-06-15
I installed Unbuntu 8.04 using wubi. If I try to logon using "Run XClient script" or "Gnome" I get the logon music, followed by the drum roll and get back to to the logon screen. I logon with no problems if I set the session to "failsafe Gnome".

Any thoughts?

---

### Post by prince_niceguy on 2008-06-16
login into the failsafe terminal and run the following commands.. it will reset your setting...then you should be able to login...

```
rm -rf .gnome .gnome2 .gconf .gconfd .metacity
```

---

### Post by CaKiwi on 2008-06-17
Thanks for the response, prince_niceguy but I folllowed your instructions and it did not help. I did not have a .gnome file/directory but I removed the others. When I logged on again (using failsafe gnome) the files I removed had been recreated. Is there a log somewhere which would tell us what the problem is?

Here is a listing of the files.

ian@ian-desktop:~$ ls -l .gnome2
total 20
drwx------ 2 ian ian 4096 2008-06-16 21:30 accels
drwx------ 2 ian ian 4096 2008-06-16 21:30 keyrings
drwxr-xr-x 2 ian ian 4096 2008-06-16 21:30 nautilus-scripts
drwx------ 3 ian ian 4096 2008-06-16 21:30 panel2.d
drwxr-xr-x 4 ian ian 4096 2008-06-16 21:30 share
ian@ian-desktop:~$ ls -l .gconf
total 8
drwx------ 6 ian ian 4096 2008-06-16 21:30 apps
drwx------ 3 ian ian 4096 2008-06-16 21:30 desktop
ian@ian-desktop:~$ ls -l .gconfd
total 80
-rwx------ 1 ian ian 76358 2008-06-16 21:32 saved_state
ian@ian-desktop:~$ ls -l .metacity/
total 4
drwx------ 2 ian ian 4096 2008-06-16 21:30 sessions
ian@ian-desktop:~$

---

### Post by prince_niceguy on 2008-06-17
the error would be in the xsession-errors or something of those kind in your home directory. you can publish that...

---

### Post by CaKiwi on 2008-06-17
Here is part of the .xsession-errors file

** (nautilus:5615): WARNING **: Unable to add monitor: Not supported
Starting gtk-window-decorator
/usr/bin/compiz.real (video) - Warn: No 8 bit GLX pixmap format, disabling YV12 image format
I/O warning : failed to load external entity "/home/ian/.compiz/session/default0"
x-session-manager: Fatal IO error 104 (Connection reset by peer) on X server :0.0.
gnome-settings-daemon: Fatal IO error 104 (Connection reset by peer) on X server :0.0.
[1213677006,000,xklavier.c : xkl_engine_start_listen/]    The backend does not require manual layout management - but it is provided by the applicationXIO:  fatal IO error 0 (Success) on X server ":0.0"^M
      after 12 requests (12 known processed) with 0 events remaining.^M
gnome-screensaver: Fatal IO error 104 (Connection reset by peer) on X server :0.0.
nautilus: Fatal IO error 104 (Connection reset by peer) on X server :0.0.
XIO:  fatal IO error 11 (Resource temporarily unavailable) on X server ":0.0"^M
      after 3822 requests (3796 known processed) with 0 events remaining.^M
GConf backend: There is an unsupported value at path /apps/compiz/plugins/scale/allscreens/options/initiate_edge. Settings from this path won't be read. Try to remove that value so that operation can continue properly.
bluetooth-applet: Fatal IO error 104 (Connection reset by peer) on X server :0.0.
update-notifier: Fatal IO error 104 (Connection reset by peer) on X server :0.0.
evolution-alarm-notify: Fatal IO error 104 (Connection reset by peer) on X server :0.0.
tracker-applet: Fatal IO error 104 (Connection reset by peer) on X server :0.0.
nm-applet: Fatal IO error 104 (Connection reset by peer) on X server :0.0.
applet.py: Fatal IO error 104 (Connection reset by peer) on X server :0.0.
gtk-window-decorator: Fatal IO error 104 (Connection reset by peer) on X server :0.0.

---

### Post by CaKiwi on 2008-06-21
I am still having this problem. Does anyone have any suggestions?

---

### Post by avtolle on 2008-06-21
Don't know if this will help, but try from the terminal```
gksudo displayconfig-gtk
```and try to configure the display and graphics card from there.

---

### Post by avtolle on 2008-06-21
[https://wiki.ubuntu.com/WubiGuide#head-47448c7ce144e88d6ee1a0c5aa37a215fec00d86](https://wiki.ubuntu.com/WubiGuide#head-47448c7ce144e88d6ee1a0c5aa37a215fec00d86) I suspect you have seen this, and is why you are logging in to the failsafe session. As you will note, the suggestion is to then try to configure the graphics, etc., from there, and that's the purpose of the command I posted earlier. Good luck

---

### Post by CaKiwi on 2008-06-21
I tried using

gksudo displayconfig-gtk

I fooled around changing things but nothing seemed to help. I changed the resolution to be the same as Windows sees it (1024x768 ) but after I made the change the resolution went to 640x480 and now that is the only option showing in the resolution selection and I can't change back.

Any assistance would be greatly appreciated

---

### Post by CaKiwi on 2008-06-21
I gave up trying to fix the screen resolution problem and just re-installed ubuntu. I still have the original problem where I can only login using failsafe Gnome. I tried enabling automatic login and setting the default login to failsafe Gnome but it did not help

---

### Post by CaKiwi on 2008-06-22
I stumbled onto a solution to this problem. I went to System->Administration->Hardware drivers and installed the proprietary driver for my ATI Radeon XPRESS 200 video card. I can now login using the Gnome session but I would really prefer to use an open driver. Does anyone know how I can accomplish this?

---

### Post by prince_niceguy on 2008-06-23
The card you have might not be supported by the open source drivers. You can check that... if it is not then the closed source driver from ATI is the best bet for you...

---

### Post by podness on 2008-09-21
> **prince_niceguy said:**
> login into the failsafe terminal and run the following commands.. it will reset your setting...then you should be able to login...

```
rm -rf .gnome .gnome2 .gconf .gconfd .metacity
```

You should have said this will restore all my desktop environment.. now
all the hard of work of design I put into this.. is gone :(

and the problem isn't solved. I get this problem too
that's stupid. All worked soooo well for me..

I wanted to log on windows once and didn't choose on GRUB windows on time
so when ubuntu just started up, I used alt+ctrl+del

I don't see why would I get this xterm bulls**t. running gnome-seesion
did help me out only to run gnome on command.. I couldn't make it so gnome is loaded by default again... maaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaan

Now installing all over again :/

---

### Post by podness on 2008-09-23
Heya I found a solution that actually works:

[http://ubuntuforums.org/showpost.php?p=5841400&postcount=6](http://ubuntuforums.org/showpost.php?p=5841400&postcount=6)

Good luck!

---

