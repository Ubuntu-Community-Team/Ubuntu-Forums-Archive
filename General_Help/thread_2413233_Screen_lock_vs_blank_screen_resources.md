---
title: "Screen lock vs blank screen resources"
date: 2019-02-22
forum: General Help
---

### Post by ProDigit on 2019-02-22
Hi!
I'm folding on my PC, and due to reasons of complexity, I have not yet found a way to fold on my GPUs on a headless system.

But I do want to reduce overhead on my main GPU.
It appears the desktop is using about 35MB of VRAM.

In Windows, I can also see how a desktop uses between 1 to 2% of a graphics card's resources; when set in performance mode, and more (up to 8% of 3D resources) when using aero.

I try not to run an OpenGL desktop and disable compton, because I don't use any screen effects.
Aim is to basically run the system as headless as possible, with still a functional GUI.


Now, I wonder, which setting uses the least GPU resources, when it's running by itself:
1- No screen modification (I'll just turn off my LCD).
2- Use a blank screen after a few minutes
3- Using the 'lock screen' system.
4- Disable Xscreensaver from LXQt settings' Autostart menu.

---

