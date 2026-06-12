---
title: "nautilus fata error"
date: 2008-06-16
forum: General Help
---

### Post by sandipg on 2008-06-16
Hi,
When I log in, I get an error saying :

'Nautilus cannot be used now due to an unexpected error from Bonobo when attempting to register the file manager view server' (Im running Hardy). 

Another error pops up saying: 

'The panel encountered a fatal error: could not register with the bonobo-activation server (error code:3) and will exit. It may be automatically restarted.'  

I did modify the /etc/profile.d file as I wanted to preconfigure my shell to some specific environment variables (I was trying to set up FiveRuns rm-install rails production stack). 

Any ideas? Im completely flustered as I'm somewhat of a Linux noob.

---

### Post by geirha on 2008-06-16
When you log in graphically, warnings and errors will be logged to a file called ~/.xsession-errors . See if there's any indication in there why bonobo fails, or paste its content here.

---

### Post by sandipg on 2008-06-17
Here is my xsession-errors log:

```
/etc/gdm/Xsession: Beginning session setup...
/home/sandip/.profile: 22: source: not found
/home/sandip/.profile: 23: source: not found
/home/sandip/.profile: 24: source: not found
Setting IM through im-switch for locale=en_US.
Start IM through /etc/X11/xinit/xinput.d/all_ALL linked to /etc/X11/xinit/xinput.d/default.

** (seahorse-agent:5530): CRITICAL **: gpg_options_init: assertion `engine && engine->version && engine->file_name && (g_str_has_prefix (engine->version, GPG_VERSION_PREFIX1) || g_str_has_prefix (engine->version, GPG_VERSION_PREFIX2))' failed
SESSION_MANAGER=local/sandip-desktop:/tmp/.ICE-unix/5530
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
Window manager warning: Failed to read saved session file /home/sandip/.metacity/sessions/default0.ms: Failed to open file '/home/sandip/.metacity/sessions/default0.ms': No such file or directory


Tracker version 0.6.6 Copyright (c) 2005-2007 by Jamie McCracken (jamiemcc@gnome.org)

This program is free software and comes without any warranty.
It is licensed under version 2 or later of the General Public License which can be viewed at http://www.gnu.org/licenses/gpl.txt

Initialising tracker...
Could not set idle IO priority...attempting best effort 7 priority
11
starting HAL detection for ac adaptors...none found
Throttle level is 0
evolution-alarm-notify-Message: Setting timeout for 70858 1213747200 1213676342
evolution-alarm-notify-Message:  Wed Jun 18 05:30:00 2008

evolution-alarm-notify-Message:  Tue Jun 17 09:49:02 2008


(evolution-alarm-notify:5663): Bonobo-Activation-CRITICAL **: bonobo_activation_query: assertion `ac != NULL' failed

(evolution-alarm-notify:5663): libecal-WARNING **: e-cal.c:1016: Unable to query for calendar factories

(evolution-alarm-notify:5663): Bonobo-Activation-CRITICAL **: bonobo_activation_query: assertion `ac != NULL' failed

(evolution-alarm-notify:5663): libecal-WARNING **: e-cal.c:1016: Unable to query for calendar factories

(evolution-alarm-notify:5663): Bonobo-Activation-CRITICAL **: bonobo_activation_query: assertion `ac != NULL' failed

(evolution-alarm-notify:5663): libecal-WARNING **: e-cal.c:1016: Unable to query for calendar factories

(evolution-alarm-notify:5663): Bonobo-Activation-CRITICAL **: bonobo_activation_query: assertion `ac != NULL' failed

(evolution-alarm-notify:5663): libecal-WARNING **: e-cal.c:1016: Unable to query for calendar factories

(evolution-alarm-notify:5663): evolution-alarm-notify-WARNING **: Could not create the alarm notify service factory, maybe it's already running...
nm-applet: symbol lookup error: /usr/lib/libxml2.so.2: undefined symbol: gzopen64
Traceback (most recent call last):
  File "/usr/bin/jockey-gtk", line 23, in <module>
    import gtk, gtk.glade, gobject, pynotify
ImportError: /usr/lib/libxml2.so.2: undefined symbol: gzopen64
XIO:  fatal IO error 0 (Success) on X server ":0.0"

      after 12 requests (12 known processed) with 0 events remaining.

x-session-manager: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.0.
```

I've tried reinstalling libbonobo2 and nautilus, killall bonobo-activation-server followed by restarting nautilus...nothing works. 

I am at my wits end.

---

