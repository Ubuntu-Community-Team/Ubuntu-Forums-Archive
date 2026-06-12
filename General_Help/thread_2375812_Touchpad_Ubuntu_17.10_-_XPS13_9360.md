---
title: "Touchpad Ubuntu 17.10 - XPS13 9360"
date: 2017-10-27
forum: General Help
---

### Post by biz122 on 2017-10-27
Hey,

I am running an XPS13 9360, and the touchpad precision used to be incredible in 16.10 and 17.04 out of the box.

Since I uppgraded to 17.10, it is a **completely** different story. It jerks around, the acceleration is awkward and I miss everything that I try to click on....

What happened? Is there some secret DELL-PPA I need to consult, or have quality control failed at Canonical? Anyone else feel the same pain, on the same hardware?

Regards

---

### Post by biz122 on 2017-11-16
Ok, so it turned out that **Wayland** (which is default in 17.10)  has poor touchpad support (or something)...

I logged in using **Xorg** and ran:

> sudo apt install xserver-xorg-input-synaptics

The configuration files for the touchpad is still present in 17.10 for Xorg - But equivalent configs for Wayland is missing or poorly put together... Which is unfortunate...

Anyway, I hope this helped someone out there.

---

### Post by olevaar on 2017-11-19
Thanks for this. It was driving me nuts. I've got a Synaptics TM3204-001, and had the same issues with Wayland. 

The problem was particularly bad when the cursor hovered over menus, toolbars, the dock, window edges, buttons etc. 
Just moving it around the desktop was fine. With Xorg and the xserver-xorg-input-synaptics installed, everything is now fine with the touchpad.

---

