---
title: "A Better VNC?"
date: 2007-11-20
forum: General Help
---

### Post by dalhamir on 2007-11-20
Does anyone know an alternative to the normal VNC viewer packages that are on the repos?

Specifically I want something that will restrict 'fullscreen' mode to a single desktop. It seems like such a key feature I can't believe there isn't a viewer out there that is multi-desktop aware.

or maybe there's a way to do this with the packages I have now that are just non obvious to me....

Thanks

---

### Post by dalhamir on 2007-11-20
shameless bump. man these forums are busy!

---

### Post by bingoUV on 2007-11-20
What do you mean by multi-desktop? 

1. Multiple monitors? : I have only one monitor, so I don't know.

2. Multiple virtual desktops? : My vnc works fine(with Gnome and beryl, feisty) . It might be a window manager / desktop environment issue rather than vnc issue. Which window manager and desktop environment do you use?

---

### Post by dalhamir on 2007-11-20
Multiple virtual desktops. If I 'fullscreen' my VNC session on say, desktop 2, then switch to desktop 1, it still shows the fullscreened vnc session, If I minimize the VNC session I end up on desktop 1, so I'm sure that I really am switching.

I'm using a standard ubuntu 7.10 install with gnome and compiz

Thanks for the reply

---

### Post by bingoUV on 2007-11-21
Ok, now I understand. It is not that vnc does not understand multiple virtual desktops, but your window manager has made it sticky when you view it in fullscreen. 

If you are running metacity/beryl in gnome, you can try alt-right-click after full screen. That should let you select stickiness (always on the visible workspace). Other window managers should have a similar option, but I don't know how to set those.

---

