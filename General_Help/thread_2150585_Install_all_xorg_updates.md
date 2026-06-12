---
title: "Install all xorg updates?"
date: 2013-06-01
forum: General Help
---

### Post by craga2013 on 2013-06-01
Hello
I'm currently using ubuntu 13.04 and recently got a nvidia gpu. 
I've found that the easiest way for me to install the driver is to use the xorg-edgers ppa and it works really well. However, I also get another bunch of updates from them including touchpad drivers, amd drivers, nouveau drivers and some stuff i've not even heard of like buffer management and cirrus. 

Is it safe to install these updates? especially after installing the nvidia driver? I dont wana mess anything up.

If its not safe, is there a way to hide the updates?

Thank You :)

---

### Post by tgalati4 on 2013-06-01
Linux Mint hides xorg and kernel updates (classifying them as Level 4 and 5 severity), unless you manually override that setting.  This keeps a working system working and lessens the chance of major breakage.  I don't know how to do this in Ubuntu, except "pin" the package in Synaptic and that will keep the current package level for pinned packages.  You may still get update notifications, but they just won't apply to pinned packages.

Only apply xorg updates if you have a second, working computer connected to the network so you can research problems if they happen.  When you break video, it's hard to fix without a second computer.  Proprietary drivers tend to break with kernel updates since these drivers are hooked into the kernel and need to be reinstalled with each kernel update.  Sometimes this process is automatic through the post-installation configuration script, but sometimes it fails and you are left with no video.

Proceed with caution.

---

