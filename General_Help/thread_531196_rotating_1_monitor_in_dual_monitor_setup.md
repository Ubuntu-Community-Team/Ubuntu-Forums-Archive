---
title: "rotating 1 monitor in dual monitor setup"
date: 2007-08-21
forum: General Help
---

### Post by pietro1984 on 2007-08-21
hi
I have an nvidia fx5600 working with 2 monitors with the latest nvidia drivers and the latest ubuntu release.
Dual monitor is working great but now 1 want to rotate 1 monitor 90° and leave the other monitor as is.
I've googled and searched on many pages and always found how to rotate both monitors bot nowhere how to rotate only one monitor.   So my question is it possible and how is done?

---

### Post by A3sthetix on 2007-08-21
That's a tricky one. I think the easiest solution would be to use a separate gfx card for each (if you have 2). Rotate the monitor and adjust using that particular graphics card's interface.

---

### Post by mdoyle on 2007-08-23
In for any other way to do this besides adding another peice of hardware.

---

### Post by mdoyle on 2007-08-23
Apparently it's going to be standard in a newer beta version (not one that is released as far as I can tell, at least it's not available on mine) of Gutsy.

[https://wiki.ubuntu.com/DisplayConfigGTK](https://wiki.ubuntu.com/DisplayConfigGTK)

---

### Post by pietro1984 on 2007-08-24
I tried this DisplayConfigGTK but when I install it the nvidia drivers get disabled, witch I don't like..
also there is the option to rotate an indivual monitor but when I click on it I only have 1 rotation option: normal... perhaps I'm doing something wrong.

---

### Post by mdoyle on 2007-08-24
You have the option for rotating each monitor? On mine I don't. Did you install anything or was it already there? Maybe I need an update.

Edit: Just did some updates but my Orientation option is grayed out. I'm gonna jump in the xorg.conf file and look around, maybe I can enable it somehow.

---

### Post by mdoyle on 2007-08-24
Got it working. I went into my xorg.conf file, found the monitor I wanted rotated (identified it in the nvidia-settings manager), then added:

Option "RandRRotation" "On"
Option "Rotate" "CW"

(put CCW if you want to go the other way)

Into the Monitor section of the specific monitor I wanted rotated.

---

