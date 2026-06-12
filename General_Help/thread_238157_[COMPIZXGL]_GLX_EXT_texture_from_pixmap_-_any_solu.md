---
title: "[COMPIZ/XGL] GLX_EXT_texture_from_pixmap - any solution?"
date: 2006-08-17
forum: General Help
---

### Post by Ushiiin on 2006-08-17
I would like to know how to solve the error stated below, when attempting to run "compiz --replace".
I've currently got an Nvidia-card, which is fully installed and set up, and it's confirmed that xgl is up and running, and driver is set to nvidia in xorg.conf. All are the newest versions. I've tried both the latest official nvidia-driver, which fully compiled, installed, and worked, but gave the error below, too, and the one found at the official ubuntu repositories.
I don't want to know hooow many nights I've spent trying to solve this, I would be forever grateful to the one who helps me out.

compiz.real: GLX_EXT_texture_from_pixmap is missing
compiz.real: Failed to manage screen: 0
compiz.real: No managable screens found on display :0.0

EDIT: I've got the latest Mesa libraries, too, I think, the libcairo2 that became available today (and phucked up all the fonts but whatever), and the beerorkid and its related repositories.

---

### Post by christhemonkey on 2006-08-17
That glx extension has not been written into either nvidia's or ati's proprietry driver.
Unfortunately :(

But you can use mesa rendering to workaround until they do.
Im sure theres a howto about that sort of thing around here somewhere...

---

### Post by Ushiiin on 2006-08-17
> **christhemonkey said:**
> That glx extension has not been written into either nvidia's or ati's proprietry driver.
Unfortunately :(

But you can use mesa rendering to workaround until they do.
Im sure theres a howto about that sort of thing around here somewhere...

Tell me when you find it =D=D=D=D=D=DD=D=D=D=DD==D=D=D=D:D:D:D:DD=D=D=D=D=:D

---

