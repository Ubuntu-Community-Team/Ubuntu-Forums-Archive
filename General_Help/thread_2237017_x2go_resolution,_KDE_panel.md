---
title: "x2go resolution, KDE panel"
date: 2014-07-30
forum: General Help
---

### Post by Untarnished_Truth on 2014-07-30
I have two machines running Ubuntu (Kubuntu 14.04).  I installed x2go-server on one of them, and x2go-client on the other. I successfully got a remote desktop on the client, no problemo.  But there's just one problem: the resolution of the remote desktop windows that appears on my client's monitor doesn't seem to obey the resolution I set .  The good part is that the remote desktop I get has a nice, high resolution -- except that it seems to cuts the lower ~10% of what is supposed to be my desktop, therefore I don't see my KDE panel.  While I can probably just anchor my panel to the top of the screen, that's just a temporary workaround and not a solution for me. 

Is there a way to solve this bottom-of-screen-is-cut problem in the remote desktop that I get, say by correcting the resolution problem?  

(I doubt the following info is relevant, but just in case it is, I use a 1680x1050 physical monitor on my server-PC, and my client has 1920x1080 monitor connected to it)

---

### Post by TheFu on 2014-07-30
Open a terminal on the remote machine (inside x2go) and change the settings using any of the X/Windows tools for this.  **xrandr -s 1920x1080** is probably the command you want, but any of the tools can be used - lxrandr, arandr, and I suspect KDE has one too.

BTW, I've seen this issue here with x2go, plus I switch between different x2go client machines with very different screen resolutions, so I'm always having to correct these settings.  I use LXDE and decided it was easier to move the panel to the top, since it was almost always hidden on the netbook (768p screen).

---

### Post by Untarnished_Truth on 2014-07-30
> **TheFu said:**
> Open a terminal on the remote machine (inside x2go) and change the settings using any of the X/Windows tools for this.  **xrandr -s 1920x1080** is probably the command you want, but any of the tools can be used - lxrandr, arandr, and I suspect KDE has one too.

BTW, I've seen this issue here with x2go, plus I switch between different x2go client machines with very different screen resolutions, so I'm always having to correct these settings.  I use LXDE and decided it was easier to move the panel to the top, since it was almost always hidden on the netbook (768p screen).

Great, this works!  xrandr -s 1920x1080 per se still hid my panel, but after playing with the possible resolutions, I ended up with xrandr -s 1600x900 -- a reasonable compromise. I might just move my panel up at some point in the future, but for now I'm very happy with this.  Thanks.

---

### Post by TheFu on 2014-07-30
Solved?  Please mark it so in the thread tools.

---

