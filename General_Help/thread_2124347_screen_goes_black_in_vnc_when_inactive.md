---
title: "screen goes black in vnc when inactive"
date: 2013-03-10
forum: General Help
---

### Post by catchman on 2013-03-10
hi,

When i'm using vnc, the screen goes black after an inactivity for around 2 seconds. If i move the mouse or press a key the screen goes back however this is very annoying.
I have KDE 4.10 on both systems, i'm tunneling the vnc through the ssh connection (*ssh -R5900:localhost:5900 myhost*) from server to my local computer.
i'm using x11vnc as a server and tight vnc as a client. 

I've tried different vnc clients (vinagre, real vnc, xvnc4viewer) but the issue remains.
Also, i've tried different settings to x11vnc server (-sb 0 -nonap -noxdamage etc) but nothing works for me.

There is an thread with the same issue, but doesn't seem to be resolved ([http://www.kubuntuforums.net/showthread.php?50181-krfb-_-vnc-client-screen-goes-black-after-a-few-seconds](http://www.kubuntuforums.net/showthread.php?50181-krfb-_-vnc-client-screen-goes-black-after-a-few-seconds))

Do any of you have some idea what can be causing this behavior?
thanks

---

