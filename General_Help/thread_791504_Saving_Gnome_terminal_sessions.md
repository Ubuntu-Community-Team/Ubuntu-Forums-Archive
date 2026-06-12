---
title: "Saving Gnome terminal sessions"
date: 2008-05-12
forum: General Help
---

### Post by Fortisunto on 2008-05-12
Hello

I have a general question i hope someone can answer for me. I am using default gnome login on Ubuntu 8.0.4 and i have set up 8 workspaces.  In each workspace i have approx 5 or 6 Terminal sessions open (ssh or telnet sessions to different servers) so approx 40 terminals open across all workspaces when logged in.

My question is, if i reboot (or pc gets powered off accidentally) i will lose all these terminal windows and have to start them all again - is there a way that i could either....

a) save my current session so that if i reboot it will remember to open terminal windows in each workspace as i had before (but not logged into each server)

or

b) even better (but probably will involve some kind of scripting?) have the same above - but will actually log into each server as well on startup.

I seem to remember getting something like this working years ago on another distribution but using KDE. Would be cool if i could get this working in Gnome.

Any suggestions gladly accepted :D

---

### Post by drs305 on 2008-05-12
System, Preferences, Sessions, Session Options has an option to save sessions when loggging out. I don't know if it will do all you are asking of it but it's worth trying.

---

### Post by Fortisunto on 2008-05-12
> **drs305 said:**
> System, Preferences, Sessions, Session Options has an option to save sessions when loggging out. I don't know if it will do all you are asking of it but it's worth trying.

Hey thanks allot for that - is very useful as can also remember all  application that are running as well.

In fact i was being stupid. I just done a reboot and it remembered my terminal sessions. I think when i done it before - it had crashed due to a driver issues. Its now fine. The autologins would be good on each terminal so i will have to play around find a way but still if anyone knows pls advise.

---

### Post by unutbu on 2008-05-12
You could set up automatic login through ssh by following the directions at 

[http://www.bluegum.com/Software/ssh-auth.html](http://www.bluegum.com/Software/ssh-auth.html)

You can also make a script that can be run at login that will launch a whole bunch of terminals:
```

#!/bin/bash
gnome-terminal --geometry 100x10+200+20 --command="ssh me@localhost" &
gnome-terminal --geometry 100x10+200+220 --command="ssh minime@localhost" &
gnome-terminal --geometry 100x10+200+420 --command="ssh you2@localhost" &
```

To get the terminals displayed in the right workspace is the job of your window manager (e.g. metacity, fvwm, etc.) or maybe Gnome. I only know how to do this through fvwm. Maybe someone here (or you) will figure out how to do it through Gnome.

---

