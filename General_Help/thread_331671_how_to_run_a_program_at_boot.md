---
title: "how to run a program at boot?"
date: 2007-01-04
forum: General Help
---

### Post by sdowney717 on 2007-01-04
I need to run martian_modem when ubuntu boots up.
How can I do this easily?
thanks

---

### Post by sdowney717 on 2007-01-04
system - preferences - sessions
click startup programs

---

### Post by lswb on 2007-01-05
You could put it in a few different places depending on your needs.:

In /etc/rc.local  to run as root before any users have logged in; You'll have edit this as root; use sudoedit or sudo (or gksudo) your_favorite_editor to edit this file. If this program initializes your modem or configures some kind of hardware, this is probably the best place. (Note, IIRC, should you for some reason login as "single user" or "recovery mode" then /etc/rc.local does NOT run)

As the previous poster noted, you could use (assuming Gnome) system->preferences->sessions->startup-programs and add the program there. However, it will not run for other users unless they add it also, and it will not run if Gnome doesn't start. (for instance if you set up your system to login to a console rather than graphical login like gnome or KDE) 

/etc/bash.bashrc will run it before any user .bashrc or shell logins,

or in your own ~/.bashrc to run only when YOU login.

---

