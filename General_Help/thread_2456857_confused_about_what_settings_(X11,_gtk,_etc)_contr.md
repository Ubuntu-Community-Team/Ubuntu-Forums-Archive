---
title: "confused about what settings (X11, gtk, etc) control what"
date: 2021-01-20
forum: General Help
---

### Post by riverhawk on 2021-01-20
Hi everyone, I'm trying to fix my mouse. I am using Xubuntu, which has Xfce4 as a window manager on X11.

What settings control the mouse? For example, I am running across Gtk2 & Gtk3, but I don't understand how this fits with Xfce. Are input device settings controlled by Gtk or X11 settings.

Thanks for any clarifications!

---

### Post by Keith_Helms on 2021-01-20
Go into Settings Manager or the Settings menu and select Mouse and Touchpad.

---

### Post by riverhawk on 2021-01-20
Thanks, but I've tried all the settings available. I did just upgrade, so there may be more available. But I'd still like to know how gtk fits in with xfce.

---

### Post by Keith_Helms on 2021-01-20
What is it the mouse is doing that you want to change or fix?

GTK is a toolkit for creating GUI applications.  XFCE was written using GTK libraries and methods.

---

### Post by riverhawk on 2021-01-21
Thanks about explaining how GTK libraries are used in XFCE.

For the mouse, a lot of different issues. Upgrading to 20.04 seems to have helped solve about half. Right now the main issues are menus flying up and down too fast, click to close one tab on a browser and several close, which I think somehow multiple clicks are being sent, and then also very poor text selection where I try to highlight a selection and it is dropped, or can't highlight what I want to.

Might be problems in a recent kernel and will go away in the future.

---

### Post by Impavidus on 2021-01-21
The xev tool can tell you exactly what button presses, wheel scrolls and movements are detected. If you get double presses when you click once, it may be a hardware problem, although it may be possible to fix it in software by merging closely separated presses into one. I never tried that.

---

### Post by riverhawk on 2021-01-21
Thank you Impavidus, the xev tool is very cool!

So, I hate to say this, but I went out and bought a new mouse and that was the problem. I will say I expected, if a mouse failed, it would stop clicking. In this case, the mouse failed and it was sending multiple signals per click, which is something I didn't expect. So, although I feel foolish, I will console myself with this thought.

Thanks again!

---

