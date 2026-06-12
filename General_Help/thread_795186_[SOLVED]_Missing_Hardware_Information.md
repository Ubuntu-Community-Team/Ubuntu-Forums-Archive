---
title: "[SOLVED] Missing Hardware Information"
date: 2008-05-15
forum: General Help
---

### Post by gibbylinks on 2008-05-15
Under Gutsy I had an icon in the control panel "Hardware Information" it's disappeared under Hardy, any ideas how to get it back ? 

I tried looking under "main menu" but couldn't see it.

Thanks

---

### Post by CarlAdam on 2008-05-16
It seems to be missing here to, and the old one isn't in the repos either, but there is two new ones:)

If you want something that looks like the old one then do this in a terminal:

sudo apt-get install gnome-device-manager

Or if you want a new fancy hardware info app with benchmarking functionality do this:

sudo apt-get install hardinfo

Or start synaptic and search for gnome-device-manager or hardinfo.

---

