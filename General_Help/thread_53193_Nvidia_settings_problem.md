---
title: "Nvidia settings problem"
date: 2005-07-30
forum: General Help
---

### Post by grofaz on 2005-07-30
I'm using the synaptic nvidia driver package and I always have to open nvida-settings manually at end of boot up for my setings to take effect. Is there a way to correct that ? Also is there a way to test the driver to make sure everything is working properly ? Thanks!

---

### Post by pr00f 0f d3f on 2005-07-30
if you mean your nvidia display settings, you can edit them in your /etx/X11/xorg.conf file (see the [Nvidia README](ftp://download.nvidia.com/XFree86/Linux-x86/1.0-7667/README.txt) for details)

as for testing the driver, open a console and run glxgears -- if it shows the fps as more than 500 (probably way more), they're working fine.

---

### Post by jerrykenny on 2005-07-30
Grofaz,

The first indication everything is working properly is the nvidia splashscreen on starting x,       second good one is to open a terminal and type glxgears . . . with a good card they should be just whizzing along.

Dont know why you have to configure nvidia every time,  have you set the defaultdepth to 16 or 24 in /etc/X11/xorg.conf ?     I take it the driver here does say nvidia, and that Load DRI is hashed out ?

---

### Post by grofaz on 2005-07-30
OK. Edited xorg.conf so that DRI is hashed out. Color depth is 24 bit. Isn't there a 32 bit option like Windows?

At any rate, I rebooted to test and it didn't fix the problem. Isn't there something else needs to be hashed out besides DRI? Seem to recall there is but don't remember what.

---

### Post by grofaz on 2005-07-30
Read the Nvidia readme and it doesn't really offer anything new as far as configuring the xorg.conf file. Ran glxgears and I'm getting mid 900's fps. But does that tell me anything about how well 3D Acceleration is working? The reason I ask is cedega hardware tests variously pass or fail my Nvidia card. I have a hunch it's cedega needs the tuning and not my card.

---

