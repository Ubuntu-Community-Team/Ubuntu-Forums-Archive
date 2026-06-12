---
title: "Widgets vanish when I'm running VNC"
date: 2022-03-20
forum: General Help
---

### Post by goemonburo on 2022-03-20
Hi, everything is fine when I'm NOT running VNC but when I run VNC, I have no (hope I'm using the right term) widgets in my windows -- no way to minimize, maximize, drag, resize, etc, or even close.  It's like the entire "frame" of the window is gone and I can only use the app as it shows up...sometimes in a tiny page that's too small to use.  Right click has no effect.  I suspect that it's because of the "startxfce4" but I don't know how to get that to match what I normally see when I start X.  I've tried playing around with other .vnc/xstartup files and always get the gray screen of death. 

I am using Lubuntu 20.04LTS in both.  Xvnc version TightVNC-1.3.10. 

Here's the .vnc/xstartup file:

```
#!/bin/bash
xrdb $HOME/.Xresources
startxfce4 &
```

---

### Post by HermanAB on 2022-03-20
The window manager crashed - it manages the outer frame resizing dragging etc.

That said, why do you use VNC?  It is mostly a Windows thing and us the favorite way to get your machine hacked.

If you work Linux to Linux or Mac to Linux, just use Ssh.

---

### Post by guiverc on 2022-03-20
> **goemonburo said:**
> Hi, everything is fine when I'm NOT running VNC but when I run VNC, I have no (hope I'm using the right term) widgets in my windows -- no way to minimize, maximize, drag, resize, etc, or even close.  It's like the entire "frame" of the window is gone and I can only use the app as it shows up...sometimes in a tiny page that's too small to use.  Right click has no effect.  I suspect that it's because of the "startxfce4" but I don't know how to get that to match what I normally see when I start X.  I've tried playing around with other .vnc/xstartup files and always get the gray screen of death. 

I am using Lubuntu 20.04LTS in both.  Xvnc version TightVNC-1.3.10. 

Here's the .vnc/xstartup file:

```
#!/bin/bash
xrdb $HOME/.Xresources
startxfce4 &
```

I'm confused;   you mention Lubuntu which uses the LXQt desktop, but instead use `startxfce4` to start a Xfce4/Xubuntu desktop?

I'd have expected a `startlxqt` there - given that's the Lubuntu/LXQt command; have I missed something?

---

### Post by goemonburo on 2022-03-20
@guiverc YES!  You have exactly what I'm curious/confused about myself.  The reason this is as above is that it's literally the ONLY thing that's worked after dozens of tries and scouring the web.  What I would like is for my VNC session to "look and feel" like it does when I boot up locally...but it's totally different.  Different background, different icons, no window handlers, etc.  It has a little mouse in the background instead of the default purple-blue wireframe hummingbird...all that.  I am sure that it's looking in the wrong place for these simple things when it starts up X, but I don't know how to get it to use the same config script.  And the various things I've tried have resulted in a gray screen.

I did try the "startlxqt" but it gray screened me too.  Any other things I can try?  I'm trying for Lubuntu, not Xubuntu if that's germane.

---

### Post by goemonburo on 2022-03-20
I don't think you understand what I'm trying to do, @HermanAB.  My question is about the VNC xstartup.  If you can help with that, great.  SSH is for logging into a system and doesn't offer an xwindows desktop environment, though in a pinch I've pulled remote programs into a local session with the -X flag.  If I'm misunderstanding, please let me know, I'd be grateful to know of the "better" way to do it.  But I want to set up a VNC server and then log in from various systems (windows, mac, linux) while I'm away and have it ready to go.

---

### Post by HermanAB on 2022-03-21
The thing is, if you run Linux or Mac as your local machine, then you already have a proper desktop, so there is not much point in overwriting it all with a slow remote one.  Just launch the remote applications you want over ssh.  It is much faster and secure and reliable.

---

