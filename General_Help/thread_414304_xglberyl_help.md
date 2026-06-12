---
title: "xgl/beryl help"
date: 2007-04-19
forum: General Help
---

### Post by cptjaben on 2007-04-19
I recent;y had a problem where some of my icons were missing, mainly the shutdown and restart icons. I followed [this guide]("http://ubuntuforums.org/showthread.php?t=244662&page=3#24"), hoping it would fix the problem. I edited my /etc/X11/gdm/gdm.conf-custom so that it looks like this:

```
[daemon]
GdmXserverTimeout=35

[security]

[xdmcp]

[gui]

[greeter]

[chooser]

[debug]

[servers]
0=inactive
1=Xgl

[server-Xgl]
name=Xgl
command=/usr/bin/Xgl -fullscreen :1 -audit 0 -ac -br -accel glx:pbuffer -accel xv:pbuffer
chooser=false
handled=true
flexible=true
priority=0
```

and my  xglstartup script to this:

```
#!/bin/sh
Xgl :1 -fullscreen -ac -accel xv:pbuffer -accel glx:pbuffer &
DISPLAY=:1
exec dbus-launch --exit-with-session gnome-session
```
 It did fix the problem, but it also broke my xgl/beryl and now my computer runs incredibly slow and lags out when anything graphic related happens. Is there a way I can fix the problem by reverting back to my old settings? I used [this guide]("http://wiki.beryl-project.org/wiki/Install_Beryl_on_Ubuntu_Edgy_with_XGL_and_ATI") to install beryl/xgl originally. Thanks

---

