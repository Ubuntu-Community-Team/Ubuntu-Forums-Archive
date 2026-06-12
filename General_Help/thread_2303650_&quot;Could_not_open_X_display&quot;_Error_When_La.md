---
title: "&quot;Could not open X display&quot; Error When Launching Sudo GUI Program From Terminal"
date: 2015-11-20
forum: General Help
---

### Post by cobalt2 on 2015-11-20
When launching a sudo GUI program from terminal, I receive the following error:
```

** (gedit:3200): WARNING **: Could not open X display
No protocol specified
Failed to connect to Mir: Failed to connect to server socket: No such file or directory
Unable to init server: Could not connect: Connection refused

(gedit:3200): Gtk-WARNING **: cannot open display: :0

```
I get this error whether I use sudo, gksudo or gksu.

Distro is Lubuntu 15.10.

---

### Post by grahammechanical on 2015-11-20
> Failed to connect to Mir:

That is the reason. Mir should not be installed on Lubuntu. It is not installed by default on Ubuntu either. There is something about your Lubuntu system that is not default.

I can install on Ubuntu unity8-session-mir and I would get a login session that would be running on Mir and not the X server. In that situation I would expect a lot of default utilities and applications not to run and to produce that same error. For they are not native Mir applications.

---

### Post by cobalt2 on 2015-11-20
My installation doesn't look default because I restored my home folder from an Ubuntu backup including all the hidden folders. mir is *not* installed so there must be some config file referencing it. So what config file do I need to edit in order to remove any references to mir?

---

### Post by cobalt2 on 2015-11-23
Could anyone help me with this problem?

---

