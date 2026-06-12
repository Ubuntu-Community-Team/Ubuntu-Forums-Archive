---
title: "VNC with dual monitors"
date: 2007-08-26
forum: General Help
---

### Post by DennisTT on 2007-08-26
Hi

I have Ubuntu working with 2 monitors as one big desktop.  I'm trying to access this computer through built-in VNC from another Windows computer but it doesn't seem to work.  The screen I see is attached.

Is there a way to fix this?

Thanks in advance.

---

### Post by DennisTT on 2007-10-02
Wondering if anybody has any ideas at all :)

---

### Post by bodhi.zazen on 2007-10-02
Do you have dual monitors on the windows client ?

Perhaps try a different vncserver with a smaller screen size ?

tightvnc [uwiki]VNCOverSSH[/uwiki] This is how to install tightvnc.

Perhaps :```
vncserver -geometry 1280x1024 -depth 24 :1
```

vnc4server as an alternate, although I find vnc4server to be slow ...

Or [uwiki]FreeNX[/uwiki]

---

### Post by dirtygreek on 2008-04-09
Has anyone found a solution to this? I have a similar issue.  I can see both monitors, but only most of the left monitor (cut off and black near the bottom) and only a little of the left side of the right monitor (most of it is cut off and black)

It appears to be showing me enough screen space, but maybe the vnc server isn't displaying everything even though it knows how wide to show the client?  I'm not really sure.  

I also usually either can't click anything or it's just so slow that I can't see that I'm clicking anything.

---

### Post by vraicovi on 2008-04-09
I have a similar issue with my setup.  I forget the screen resolution, as I'm not in front of it, but it's around (1920x2)x1080.  I'm seeing the full contents of both screens.

Luckily, I mostly connect from work where I have a a dual monitor setup.  Of course, I've been having sound issues and they seem to have stopped me from connecting remotely today.

it would be nice if someone came up with a VNC client similar to Apple's Remote Desktop, where you can choose to see both monitors or one of the individuals...

---

### Post by dirtygreek on 2008-04-09
Well, the "solution," at least for me, was to use x11vnc.  That made everything visible for me, but it still was doing something weird with the mouse.  The mouse was responding to the right screen when I moved it on the left screen, and it wasn't doing anything on the right screen.  x11vnc with the -xinerama and --xwarppointer options fixed that.  I guess that will only help if you have xinerama running.

So, basically, install x11vnc if you don't have it and use

x11vnc -xinerama -xwarppointer

Hope that helps someone.

---

