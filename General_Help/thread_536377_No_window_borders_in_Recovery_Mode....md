---
title: "No window borders in Recovery Mode..."
date: 2007-08-27
forum: General Help
---

### Post by upthelum on 2007-08-27
Is this normal, perhaps a security thing? 
I cant drag windows round the screen and cant view the taskbar to choose between windows that way. I'm trying to set up basic web pages using Apache2 but when booted normally i have a permissions issue using Thunar. I tried to change some folder permissions in Terminal but it didn't seem to have an effect so i thought i would have ownership in Recovery Mode but get this window problem.

---

### Post by apetresc on 2007-08-27
When you login using GDM or KDM, check the Session menu and see what it's set to. Make sure it's not set to Xgl or anything like that. Manually set it to Gnome/KDE if you have to. What's probably happening is that it's trying to boot in Xgl, but can't because compositing isn't usable in recovery mode, so it just doesn't use any window manager at all (hence no borders).

Let us know if this helps :)

---

