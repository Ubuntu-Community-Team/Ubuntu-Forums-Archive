---
title: "Please help, still having startup problems"
date: 2006-09-14
forum: General Help
---

### Post by mikesena on 2006-09-14
Hi, 

I previously posted about an error in my system, where GDM would not start.  The suggestion was made that I install KDM so I could login.  This worked perfectly, a sudo apt-get install kdm, followed by sudo kdm had me up and running.  However, I REALLY want to go back to GDM.  I have problems that appear when I use kdm, theme errors and others, because its not meant to go with ubuntu.

I have tried NUMEROUS times to install gdm.  I did a sudo apt-get install gdm, reinstall, remove, upgrade, everything.

It's not creating any config files.  my /etc/gdm/gdm.conf is blank, probably why it no longer works at all.  how are these created?  I heard about gdmsetup, but when i run that it comes up with this:```
meo@meo-laptop:~$ gdmsetup

(gdmsetup:6362): Gdk-WARNING **: locale not supported by Xlib

(gdmsetup:6362): Gdk-WARNING **: cannot set locale modifiers
  Failed to connect to socket, sleep 1 second and retry
  Trying failed command again.  Try 2 of 5.
  Failed to connect to socket, sleep 1 second and retry
  Trying failed command again.  Try 3 of 5.
  Failed to connect to socket, sleep 1 second and retry
  Trying failed command again.  Try 4 of 5.
  Failed to connect to socket, sleep 1 second and retry
  Trying failed command again.  Try 5 of 5.
  Command failed 5 times, aborting.
Could not access GDM configuration file.
```Both my gdm.conf and gdm.conf-custom files are blank.  Can anyone please help?

---

### Post by DoctorMO on 2006-09-14
Remove gdm, remove the /etc/gdm directory, install gdm.

I hope this helps.

---

### Post by Sammi on 2007-01-11
I wasn't able to login via GDM too.Got this error "Authorication Failed".

Solved it by changing my password so it only contained letters from the [english alphabet]("http://en.wikipedia.org/wiki/English_alphabet"). Somehow GDM didn't like a letter I was using from the [danish alphabet]("http://en.wikipedia.org/wiki/Danish_alphabet").

---

