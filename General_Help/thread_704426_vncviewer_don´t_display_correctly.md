---
title: "vncviewer don´t display correctly"
date: 2008-02-22
forum: General Help
---

### Post by jagem on 2008-02-22
Hi, i installed vnc4server and vnc4viewer in xubuntu. I run vncserver so it gives me remotely access to my computer, giving me desktop:1.
The problem is when i run vncviewer to verify it´s functioning correctly, it opens the connection but it only gives me a window with a terminal, without any window manager.
I tried vnc with ubuntu and it functions correctly; the difference is that instead of running vncserver (actually only vncviewer its installed)  i chequed the option in system>preferences>remote desktop that cames only in ubuntu. Any solutions? Thanks.

---

### Post by Beefeater on 2008-02-23
Edit the file
~/.vnc/xstartup
should do the trick.

---

### Post by u-foka on 2008-02-23
Hy!

The vnc4server act's as a new Xserver and start's only a terminal by default on it... you can start "xfwm4 &" then you got a window manager and then you can remain use the terminal becouse "&" tells bash to start the process in background....

If you want to control your current desktop session, you can use ubuntu's remote desktop function but it's really insecure...
If you want to acces your desktop session, I suggest you to use x11vnc... after you installed it, you can run x11vnc simply from your X session, or from an ssh shell... this way you may run vnc only when you need it :) It has many options, like -localhost to tunnel your vnc connection over ssh for best security, -display :0 for example to tell x11vnc whitch X session to connect when you run is outside X maybe from an ssh shell... -noxdammage to do not use the xdammage extension, what isn't works very well with compiz... -forever to keep x11vnc alive after a closed connection, this way you can add x11vnc to autostart...

So for a secure remote connection, you can run something like this on a remote box:
**ssh -L 5900:localhost:5900 username@your_target_box "x11vnc -noxdammage -localhost -display :0"**
to start a tunnelled vnc server, and you can connect it with **vncviewer localhost**
and if your local 5900 port is busy you can use **-L PORT:localhost:5900** and tell vncviewer the port too **vncviewer localhost:PORT**

---

### Post by jagem on 2008-02-25
Thanks, it worked perfectly.

---

