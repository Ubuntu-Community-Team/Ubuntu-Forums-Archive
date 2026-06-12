---
title: "Relationship among: vino, vinagre, and other vnc apps?"
date: 2008-04-13
forum: General Help
---

### Post by yang on 2008-04-13
I know bits and pieces of information, but could someone with more comprehensive understanding describe what's the relationship among: vino, vinagre, realvnc, tightvnc, xvnc4viewer, xvncviewer, xtightvncviewer, etc.?

From Google queries, the only two VNC programs that I believe are in widespread use are realvnc and tightvnc, of which the latter appears to be more advanced. For xvncviewer and xvnc4viewer: what projects do these come from/belong to? The xvncviewer apt description says it includes techniques from TightVNC - so is it from RealVNC? Then what about xvnc4viewer? Which one is recommended? I know Ubuntu's answer for 8.04 is Vinagre. Where did that come from? It has a barren website - is it yet another VNC viewer? Does it have advantages over the current ones that compelled Ubuntu to crown it as the new default?

As for vino, the only info I can find on it is from [http://www.gnome.org/~markmc/remote-desktop-2.html](http://www.gnome.org/~markmc/remote-desktop-2.html) (and remote-desktop.html). How do these compare with the RealVNC and TightVNC servers?

Lastly: I know that VNC is more general and cross-platform than NX, e.g., one can run VNC servers on Windows, whereas it's probably more difficult to do the same with an NX server. But for Linux to Linux remote desktop use, is there any effort on making NX as prominent a part of Ubuntu's remote desktop tools as VNC and rdesktop?

(I began down this path on my quest for a setup where I can actually copy and paste at least text between the cilent and server - I still don't have an answer for this, though I've previously posted on these forums.)

Thanks for any clarifications!

---

### Post by ryanhaigh on 2008-04-14
Vino allows remote access to the current session (where you are actually logged in) the various others will create a new session when you start the vnc connection. Personally I use tightvnc as the connections I use it on are often limited in terms of bandwidth.

Vinagre is basically a nicer interface for managing remote connections, I don't know if it handles other protocols besides vnc but it allows you to save connections/bookmark them. Im not sure what backend vinagre uses (whether it supports tightvnc options).

As far as NX goes I have no idea but you could check out the launchpad page for it perhaps.

---

### Post by yang on 2008-04-14
Are you sure the current session feature is introduced by vino? I've been connecting to the current session for many years using other vnc apps.

FWIW, I also seem to get better performance with TightVNC, and I'm not on a slow network (everything is on a university network), which makes me wonder why it's not the default.

As for vinagre, do you mean it's the same as tsclient?

---

### Post by ryanhaigh on 2008-04-14
Im sure it is possible to configure the other vnc servers to connect to the active session but the default behaviour under linux is to create a new one, under windows it can of course not create a new one because you cannot have multiple users logged in/active at the same time.

Yes vinagre bears some similarity in that it allows you to connect using a graphical tool but it is also more integrated than tsclient (which quite obviously just calls the vncviewer/rdesktop)with a nice interface and useful features, here is a review of version 0.3 [http://www.phoronix.com/scan.php?page=article&item=839&num=1](http://www.phoronix.com/scan.php?page=article&item=839&num=1)

Hopefully they will include rdesktop support at some point.

---

