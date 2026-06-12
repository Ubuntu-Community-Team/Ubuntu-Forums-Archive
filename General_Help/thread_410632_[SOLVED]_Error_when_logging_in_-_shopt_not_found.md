---
title: "[SOLVED] Error when logging in - shopt: not found"
date: 2007-04-16
forum: General Help
---

### Post by Co.Sinecure on 2007-04-16
Hi all,

I'm currently unable to log in to my normal Gnome session.
When I attempt to log in from gdm, it straight away logs me out and shows an error dialog stating my session didn't even last 10 seconds, and to check .xsession-errors, which contains:

> 
/etc/gdm/PreSession/Default: Registering your session with wtmp and utmp
/etc/gdm/PreSession/Default: running: /usr/X11R6/bin/sessreg -a -w /var/log/wtmp -u /var/run/utmp -x "/var/lib/gdm/:0.Xservers" -h "" -l ":0" "will"
/etc/gdm/Xsession: Beginning session setup...
/home/will/.bashrc: 13: shopt: not found
/etc/bash_completion: 44: Syntax error: Bad substitution


I can login with a failsafe session (which I'm in now), I can run shopt by itself. 
Upon logging into failsafe, I get a dialog box stating:

> 
There was an error starting the GNOME Settings Daemon.

Some things, such as themes, sounds, or background settings may not work correctly.

The last error message was:

Unable to determine the address of the message bus (try 'man dbus-launch' and 'man dbus-daemon' for help)

GNOME will still try to restart the Settings Daemon next time you log in.

So, I try running dbus-launch by itself. When I first tried:
> 
(gnome-settings-daemon:8080): GSwitchIt-WARNING **: Unable to connect to dbus: Unable to determine the address of the message bus (try 'man dbus-launch' and 'man dbus-daemon' for help)

** (gnome-settings-daemon:8080): CRITICAL **: dbus_g_connection_register_g_object: assertion `connection != NULL' failed

** (gnome-settings-daemon:8080): CRITICAL **: dbus_g_proxy_new_for_name: assertion `connection != NULL' failed

** (gnome-settings-daemon:8080): CRITICAL **: dbus_g_proxy_call: assertion `DBUS_IS_G_PROXY (proxy)' failed
Segmentation fault


after running shopt, dbus-launch outputs:

> 
DBUS_SESSION_BUS_ADDRESS='unix:abstract=/tmp/dbus-EmuozsRovD,guid=3af52246ac06d3d5ec38c9c1a2be2d00';
DBUS_SESSION_BUS_PID=8144;


Can anyone offer any sort of insight as to whats wrong with my system?
I had it up and running for 3 days or so, then when I restarted all this happened, so I'm not certain if it was an update I installed or what..
Tried comparing & reseting my .bashrc to what was in /etc/bash.bashrc, buut same problem.

Thanks in advance..


EDIT--
I commented out the shopt line in bashrc, so now the error just finishes with the "bad substitution" error.

The line in question is line 44 (line numbers added):
> 
39:  
40:  # Set a couple of useful vars
41:  #
42:  UNAME=$( uname -s )
43:  # strip OS type and version under Cygwin (e.g. CYGWIN_NT-5.1 => Cygwin)
44:  UNAME=${UNAME/CYGWIN_*/Cygwin}
45:  RELEASE=$( uname -r )
46:  


---

### Post by Co.Sinecure on 2007-04-16
Some related links I found...
[http://ubuntuforums.org/showthread.php?t=319596]("http://ubuntuforums.org/showthread.php?t=319596")
[https://launchpad.net/ubuntu/+source/gdm/+bug/60079]("https://launchpad.net/ubuntu/+source/gdm/+bug/60079")
[http://www.linuxforums.org/forum/ubuntu-help/91372-cant-log-after-hard-reset.html]("http://www.linuxforums.org/forum/ubuntu-help/91372-cant-log-after-hard-reset.html")

I may have a theory as to why it occured, when I get a chance to test I'll post results.

---

### Post by Co.Sinecure on 2007-04-17
So it was as I thought - I had created a sym link to .bashrc as .profile while trying to follow some other how-to. Once that was removed, everything worked again.

Can anyone explain why? Its all a learning expereince..

---

