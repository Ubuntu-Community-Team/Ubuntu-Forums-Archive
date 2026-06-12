---
title: "Problems using applications on VNC"
date: 2021-09-10
forum: General Help
---

### Post by bsh on 2021-09-10
Hi,
I have a lot of problems when using VNC. Some programs do not appear but they are starting up. Others do work but then when they do say, a popup window, that doesn't appear. For example, thunderbird starts and appears, but the popup window where it asks for my password doesn't appear.
Looking at the processes, I'm pretty sure the problem is that those apps try to show these popups or themselves on screen :0, whereas I'm using screen :1 with VNC. Sometimes I see dbus errors mentioning :0 too.
Is there a way to start applications on a specific screen? Is this a window manager thing? I'm using XFCE. 18.04 and 20.04

---

### Post by HermanAB on 2021-09-10
VNC is mostly a Windows thing.  On Linux systems, you will have better luck and better security with SSH.

---

### Post by scorp123 on 2021-09-11
> **bsh said:**
>  I'm pretty sure the problem is that those apps try to show these popups or themselves on screen :0

You are trying to run e.g. 2 x instances of XFCE (:0 and :1) at the same time? When you are in VNC on :1 please check your **DISPLAY=** environment variable, e.g.
```
env | grep DISPLAY
```

> **bsh said:**
>  Is there a way to start applications on a specific screen?
Yes, by setting the **DISPLAY** variable.

```
export DISPLAY=:0
xterm &
```

... should launch an instance of **"xterm"** on the physical X.org session (if you are authorized to even open applications on that screen). The problem is that it is easy to accidentally set that variable to an incorrect value which would cause the symptoms you describe.

While we're at it:  What settings do you have in your **~/.vnc/xstartup** file? Can you post it here (in CODE tags please!) or on a PasteBin site?

---

