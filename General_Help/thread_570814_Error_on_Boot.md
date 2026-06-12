---
title: "Error on Boot"
date: 2007-10-08
forum: General Help
---

### Post by rabbit69ca on 2007-10-08
When I boot up my desktop running Fawn. I get this error. 



Your session only lasted less than 10 seconds.  If you have not logged out yourself, this could mean that there is some installation problem or that you may be out of diskspace.  Try logging in with one of the failsafe sessions to see if you can fix this problem.


/etc/gdm/PreSession/Default: Registering your session with wtmp and utmp
/etc/gdm/PreSession/Default: running: /usr/X11R6/bin/sessreg -a -w /var/log/wtmp -u /var/run/utmp -x "/var/lib/gdm/:0.Xservers" -h "" -l ":0" "ian"
/etc/gdm/Xsession: Beginning session setup...
SESSION_MANAGER=local/ianlinux:/tmp/.ICE-unix/5545
Window manager warning: "" found in configuration database is not a valid value for keybinding "toggle_shaded"

** (gnome-session:5545): WARNING **: Host name lookup failure on localhost.
Initializing gnome-mount extension
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device

(update-notifier:5634): GnomeUI-WARNING **: While connecting to session manager:
IO error occured opening connection.
Session management error: IO error occured opening connection


I click OK on the error, and I get loged out. 

Now I have NOIDEA what I did to FUBAR this thing... 

Any Ideas?

---

### Post by rabbit69ca on 2007-10-08
Ttt

---

### Post by Sef on 2007-10-09
See this [thread]("http://ubuntuforums.org/showthread.php?p=1762954").

---

