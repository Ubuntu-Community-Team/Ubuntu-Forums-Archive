---
title: "Unable to start XGL session"
date: 2007-02-08
forum: General Help
---

### Post by Loonux on 2007-02-08
I followed the guide on the WIKI to install Beryl and XGL. Everything went well and it was actually working for a day. But its just stopped working and i dont know why?

When i go to start my XGL session I just get a brown/black screen with the crosshair pointer (im sure you know the one i mean). It sits there for about 5 minutes before going back to the login screen. I can start my normal KDE session fine though.

My /usr/local/bin/startxgl.sh file contains the following;

```
Xgl -fullscreen :1 -ac -br -accel glx:pbuffer -accel xv:pbuffer &
sleep 4
export DISPLAY=:1
exec startkde

```

and my /usr/share/xsessions/xgl.dektop file:

```
[Desktop Entry]
Encoding=UTF-8
Name=Xgl
Exec=/usr/bin/startxgl.sh
Comment=Start an Xgl Session
Icon=
Type=Application

```

But it just doesn't work. If I do fglrxinfo i get

```
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI Mobility Radeon X1400 Generic
OpenGL version string: 2.0.6011 (8.28.8)

```

and for the life of me i cannot work out what has changed and why the system wont log in to the XGL session.

Can anyone help/ Im using kubuntu 6.10 on a Dell 6400 laptop.

Any suggestions most appreciated

Thanks

---

### Post by Loonux on 2007-02-09
Is there any way to uninstall then and start again?
dont really want to keep having to format all the time :(

---

