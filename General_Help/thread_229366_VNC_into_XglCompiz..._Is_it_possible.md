---
title: "VNC into Xgl/Compiz... Is it possible?"
date: 2006-08-04
forum: General Help
---

### Post by nothing on 2006-08-04
I've been trying for about a week to VNC into my box that has Xgl/Compiz running on it to no avail... Xgl/Compiz works flawlessly locally and I can VNC into this box, just no Xgl/Compiz... Even though it seems like this is not possible to me, there has to be a way to do it...

Running Dapper...

My Xgl/Compiz setup:

Using quinstorms' repositories

Edited gdm.conf:

 [servers]
# Override display 1 to use Xgl (DISPLAY 1 IMPORTANT FOR ATI FGLRX). 
1=Xgl 

[server-Xgl] 
name=Xgl server 
command=/usr/bin/Xgl :1 -fullscreen -ac -accel glx:pbuffer -accel xv:pbuffer
flexible=true

gdm.conf-custom

#0=Standard
1=Standard

GdmXserverTimeout=50

Using startcompiz script to start compiz
#!/bin/sh
killall gnome-window-decorator
wait

gnome-window-decorator &
compiz --replace gconf &


Just wondering if anyone has attempted or succeeded at this...

---

