---
title: "Is it possible to disable app opening animation w/o disabling system-wide animation"
date: 2023-09-03
forum: General Help
---

### Post by vampzzz on 2023-09-03
So I'm using OS: Ubuntu 22.04 LTS with Xorg (Nvidia Drivers 535) and sometimes the app opening and minimizing animation is glitchy, especially with system apps like files and terminal. Now as a workaround, I have installed the compiz extension which changes the animation style and the glitchiness has disappeared, but, still I prefer not to have any app opening animations as it's much faster.


Having said that, I really like all the other animations of ubuntu and I don't wanna remove them by simply turning off animaions of accessibility settings or gnome tweaks. So if compiz extension can somehow modify the animations I'm pretty sure that should be possible, but I'm not being able to find proper resources for the same.


*Note these app animation issues are not there in wayland but there are certain other reason due to which I can't move to wayland yet.

---

### Post by dragonfly41 on 2023-09-03
One idea is to write scripts for selected apps to have animation disabled then restore animation (for all other apps) when app is closed .. but this ploy might be trickier when you want to have a custom mix of sets of enabled/disabled apps ..

<disable global animations> .. run app .. <enable global animations>.

[https://www.digitbin.com/how-to-disable-animations-in-ubuntu/](https://www.digitbin.com/how-to-disable-animations-in-ubuntu/)
.
There are multiple GUI's which you can leverage as containers for such simple UI automation

A simple but versatile launcher is Actiona. Or there is Albert. Or just a list of bash scripts.

---

