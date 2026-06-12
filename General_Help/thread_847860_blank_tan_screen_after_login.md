---
title: "blank tan screen after login"
date: 2008-07-02
forum: General Help
---

### Post by jsprenkl on 2008-07-02
Good evening all.

I have an ubuntu 8.04 system. It worked fine. I did the recommended updates and I believe they completed. After that the power failed. Now I'm stuck. After I login the screen goes to a tan color, it plays the login sound, and stops. 

Any suggestions would be appreciated.

possible causes:
* power failure
* xorg driver update

hardware
64 bit intel q6600 on gigabyte motherboard
nvidia 8800
flat panel connected via vga cable

selecting gnome or gnome failsafe session does nothing.
failsafe xterm works. I tried 'sudo metacity --replace &'
this gets me better decorated xterm that I can move around.
ps aux shows gdm is running. I don't see compiz.

I tried renaming ~/.compiz
I tried reinstalling compiz and the nvidia drivers.

It's running vesa driver now.

.xsession-errors content:

gdm[5666]: DEBUG: Attempting to parse key string: daemon/Greeter=/usr/lib/gdm/gdmlogin
gdm[5666]: DEBUG: Attempting to parse key string: daemon/PreSessionScriptDir=/etc/gdm/PreSession/
gdm[5666]: DEBUG: Forking extra process: /etc/gdm/PreSession/Default
gdm[5667]: DEBUG: Attempting to parse key string: xdmcp/Enable=false
gdm[5667]: DEBUG: Attempting to parse key string: daemon/ServAuthDir=/var/lib/gdm
gdm[5667]: DEBUG: Attempting to parse key string: daemon/RootPath=/sbin:/usr/sbin:/bin:/usr/bin
gdm[5666]: DEBUG: Attempting to parse key string: daemon/DefaultPath=/bin:/usr/bin
gdm[5666]: DEBUG: Attempting to parse key string: daemon/BaseXsession=/etc/gdm/Xsession
gdm[5666]: DEBUG: Running /etc/gdm/Xsession /usr/bin/gnome-session for jay on :0
/etc/gdm/Xsession: Beginning session setup...
Setting IM through im-switch for locale=en_US.
Start IM through /etc/X11/xinit/xinput.d/all_ALL linked to /etc/X11/xinit/xinput.d/default.
SESSION_MANAGER=local/jay-desktop:/tmp/.ICE-unix/5666
ALSA lib control.c:909:(snd_ctl_open_noupdate) Invalid CTL front:0
ALSA lib control.c:909:(snd_ctl_open_noupdate) Invalid CTL front:0
Shutdown failed or nothing to shut down.
xrdb:  "*Label.background" on line 220 overrides entry on line 150
xrdb:  "*Text.background" on line 226 overrides entry on line 191
xrdb:  "*Label.foreground" on line 232 overrides entry on line 151
xrdb:  "*Text.foreground" on line 238 overrides entry on line 192
Checking for Xgl: not present. 
No whitelisted driver found
aborting and using fallback: /usr/bin/metacity 
Window manager warning: Failed to read saved session file /home/jay/.metacity/sessions/default0.ms: Failed to open file '/home/jay/.metacity/sessions/default0.ms': No such file or directory

** (gnome-session:5666): WARNING **: Host name lookup failure on localhost.


Tracker version 0.6.6 Copyright (c) 2005-2007 by Jamie McCracken (jamiemcc@gnome.org)

This program is free software and comes without any warranty.
It is licensed under version 2 or later of the General Public License which can be viewed at [http://www.gnu.org/licenses/gpl.txt](http://www.gnu.org/licenses/gpl.txt)

Initialising tracker...
Could not set idle IO priority...attempting best effort 7 priority
starting HAL detection for ac adaptors...none found
11
Throttle level is 0
gnome-session: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.0.
bluetooth-applet: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.0.
tracker-applet: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.0.
Window manager warning: Fatal IO error 11 (Resource temporarily unavailable) on display ':0.0'.

---

### Post by jsprenkl on 2008-07-03
found it.

what probably happened is when I uninstalled evolution I removed something else necessary for the gnome window manager. I reinstalled the package 'gnome' and got it working.

---

### Post by chrisccoulson on 2008-07-03
I'm glad you've solved it. Could you mark your thread as '[SOLVED]' by using the 'Thread Tools' dropdown towards the top right-hand side of the thread.

Thanks

---

