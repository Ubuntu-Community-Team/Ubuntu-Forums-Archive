---
title: "Running graphical apps remotely and keeping them running"
date: 2006-08-04
forum: General Help
---

### Post by Face1 on 2006-08-04
I have an ubuntu server and I'd like to be able to run graphical apps on it remotely via ssh (ie: azureus).  I'd be accessing it from another linux computer.  However, because of the nature of apps like azureus (i obviously want it to stay running), I need to allow it to persist when I close the remote connection.  Of course, I also need to be able to access the application again when I connect again.  If I was working with a command-line textual application I could use screen, but I don't think it is relevant here.  How can I do this?

---

### Post by it.henrik on 2006-08-05
there are web-plugins for aszureus that gves you full control over it via http .. but I do not think you can pull off what you want to do with ssh :/

try VNC .. with vnc you can exit your session and log back in again where you left.

---

### Post by NiN on 2006-08-05
You could do things like this with freeNX.
It has a feature to detach a session (just like screen does for the cli).

Drawback: It needs a clientside program.

[http://freenx.berlios.de/download.php](http://freenx.berlios.de/download.php)

---

