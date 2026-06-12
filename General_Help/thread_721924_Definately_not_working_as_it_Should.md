---
title: "Definately not working as it Should"
date: 2008-03-11
forum: General Help
---

### Post by Tomana on 2008-03-11
My crt display keeps going into some kind of sleep mode. Here's what's going on ...

After no activity for maybe 10 minutes or so the screen blanks, then in a few minutes it goes into
sleep mode. Someone said it was the Screensaver so I tried to open Screensaver 
and the computer did a log out. I logged in and turned off the Visual Effects and 
then was able to access the Screensaver window again. However, when I checked 
the Screensaver activate box and set the saver to start in 1 minute, nothing 
happened so I opened the screensaver window and the activate box was 
unchecked. I put a checkmark in the activate box, closed the window, re-opened
the window and the checkmark is gone again.

---

### Post by soldats on 2008-03-11
the screensaver app has bugs as far as im concerned. i dont use it personally but when i had it i had the same problem. i have since opted for manually editing the xorg.conf file and editing as i see fit. ive edited to "NEVER" turn the screen off but you can also set it turn off after a period of time you tell it to. as far as im concerned i dont trust the screensaver app as of yet. if your willing to read a little there may be some info here:
```
man xorg.conf
```
maybe under the ServerFlags section

---

### Post by Tomana on 2008-03-11
ok, I ran man xorg.conf and this is all it had:

xorg.conf(5)                                                      xorg.conf(5)

NAME
       xorg.conf - configuration File for Xorg X server

INTRODUCTION
       Xorg  supports several mechanisms for supplying/obtaining configuration
       and run-time parameters: command line options,  environment  variables,
       the   xorg.conf   configuration   file,  auto-detection,  and  fallback
       defaults.  When the same information is supplied in more than one  way,
       the  highest  precedence  mechanism is used.  The list of mechanisms is
       ordered from highest precedence to lowest.  Note that not  all  parame&#8208;
       ters  can  be  supplied  via  all  methods.  The available command line
       options and environment variables (and some defaults) are described  in
       the  Xserver(1)  and  Xorg(1)  manual  pages.   Most configuration file
       parameters, with their defaults, are described below.  Driver and  mod&#8208;
       ule  specific  configuration  parameters  are described in the relevant
       driver or module manual page.

DESCRIPTION
       Xorg uses a configuration file called xorg.conf for its initial  setup.
       This  configuration  file  is searched for in the following places when
       the server is started as a normal user:
Manual page Xorg.conf (5) Line 1

I need more help. I can use sudo nautilus but can't find the file

---

