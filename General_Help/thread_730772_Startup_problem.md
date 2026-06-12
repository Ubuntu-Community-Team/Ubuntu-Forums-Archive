---
title: "Startup problem?"
date: 2008-03-21
forum: General Help
---

### Post by johan.dahl on 2008-03-21
When I boot Ubuntu, instead of the usual login-window, the xdmcp remote login-window appear. The one that normally appears when I choose options -> login via xdmcp in the usual login-window.

To login I now have to go into tty1 and then write
```

sudo killall gdm
startx

```

And then when I'm logged in, there is a few differences. The power off and reboot button has dissappeared in the quit-menu. And the gdmsetup has dissapeared from the system->preferences menu.

When i write:
```
sudo gdm
```
The remote-login-window appear again.

How can I get it back to normal?

---

### Post by justleen on 2008-03-21
logon to any x-session, and from a terminal type ```
 sudo gdmsetup
```
make any changes in there.

---

### Post by johan.dahl on 2008-03-21
I solved it by first switching to tty1.
Login.
Type:
```

sudo killall gdm
startx

```
Press Alt + F2 -> gnome-terminal -> Press Return
Type:
```

sudo gdm

```
Press Yes in the dialog.
Press Alt + F2 -> gnome-terminal -> Press Return
```

sudo gdmsetup

```
Security -> Configure X Server...
Choose Greeter instead of Chooser in Launch.

Now everything works fine. The cause of my problem was messing around in gdmsetup.

---

