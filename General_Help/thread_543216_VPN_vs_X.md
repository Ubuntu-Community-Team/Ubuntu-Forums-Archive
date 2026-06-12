---
title: "VPN vs X"
date: 2007-09-04
forum: General Help
---

### Post by hebetude on 2007-09-04
I've heard over and over that VNC is "way faster" than straight X or "normal ubuntu remote desktop".  But I'm not seeing that, my VPN seems to be very slow in fact its hard doing simple mouse oriented tasks.  However, X is very responsive it was refreshing that I could access programs across my network being fast.

To my question, have I improperly configured my VPN?  I know this is an unfair comparison, I need VPN access to my server so I can leave applications running without having to stay logged in.  I have tried TightVNC and Ultr@VNC set on LAN setting.  I'm not exactly sure what settings I have x11vnc running.  Let's say this is the settings I use, I'm 99% sure of it.  

/usr/bin/x11vnc -rfbauth /etc/x11vnc.pass -o /tmp/x11vnc.log -forever -bg rfbport 5900

I'm not using SSH tunneling or anything (very insecure!) and I don't notice a huge CPU usage on either side server or client less than 5%

---

### Post by cwaldbieser on 2007-09-05
> **hebetude said:**
> I've heard over and over that VPN is "way faster" than straight X or "normal ubuntu remote desktop".  But I'm not seeing that, my VPN seems to be very slow in fact its hard doing simple mouse oriented tasks.  However, X is very responsive it was refreshing that I could access programs across my network being fast.

To my question, have I improperly configured my VPN?  I know this is an unfair comparison, I need VPN access to my server so I can leave applications running without having to stay logged in.  I have tried TightVNC and Ultr@VNC set on LAN setting.  I'm not exactly sure what settings I have x11vnc running.  Let's say this is the settings I use, I'm 99% sure of it.  

/usr/bin/x11vnc -rfbauth /etc/x11vnc.pass -o /tmp/x11vnc.log -forever -bg rfbport 5900

I'm not using SSH tunneling or anything (very insecure!) and I don't notice a huge CPU usage on either side server or client less than 5%

I think you mean VNC instead of VPN-- that is something completly different.  You might want to try FreeNX.  It is supposed to be much faster than VNC.

---

### Post by hebetude on 2007-09-05
Fortunately several hours down that road and getting it to work, I find out their client doesn't work in vista.  And it really doesnt work in vista :X

---

### Post by chrono310 on 2007-09-05
I believe VNC is pretty slow because it's actually sending bitmaps (*.bmp, pretty big files) of the screen over the network... Are the applications that you need to leave running graphical? If they aren't you can ssh to the server and run them with:
```
nohup <command> &
```
and then logout to leave them running.

---

### Post by hebetude on 2007-09-05
> **chrono310 said:**
> I believe VNC is pretty slow because it's actually sending bitmaps (*.bmp, pretty big files) of the screen over the network... Are the applications that you need to leave running graphical? If they aren't you can ssh to the server and run them with:
```
nohup <command> &
```
and then logout to leave them running.

thanks, I did not know that.  I may soon be switching to non-graphical applications with this.  I was really disappointed I couldn't turn off the local display when its running xfce4/gdm

---

### Post by chrono310 on 2007-09-05
Oh yeah, you don't even need to run a window manager or desktop environment at all if all you run are non-graphical apps. Check out Ubuntu's Server edition; it's just like the others, but without an IDE or X or anything.

---

### Post by cwaldbieser on 2007-09-06
> **chrono310 said:**
> I believe VNC is pretty slow because it's actually sending bitmaps (*.bmp, pretty big files) of the screen over the network... Are the applications that you need to leave running graphical? If they aren't you can ssh to the server and run them with:
```
nohup <command> &
```
and then logout to leave them running.

Also check out GNU "screen".  This has the advantage that you can log out, log in again, and reattach to your screen session.

---

