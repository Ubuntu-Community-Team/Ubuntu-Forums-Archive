---
title: "Need help with Ubuntu 7.10 (Noob Questions)"
date: 2007-12-31
forum: General Help
---

### Post by LiNuXxToOthEMaX on 2007-12-31
I have a computer, with a NVIDIA GeForce 5200 FX GFX card with it, and when I clicked on Restricted drivers manager, it said enabled, rebooted and it was a black screen for 2 min and then it said "it can only boot in low-res mode" do i need to install different drivers, or what? I'm confused thanks!

---

### Post by LiNuXxToOthEMaX on 2007-12-31
supposedly that installs new drivers, someone suggested a program called Envy u think that would work on a older card?

---

### Post by nzadLithium on 2007-12-31
goto synaptic package manager 
system << admin << synaptic

type nvidia
or scroll to it

run nvidia-xconfig

restart see if it works
if it still isnt

find out whether it has installed nvidia-glx-legacy or nvidia-glx

whichever it has installed uninstall it, install the other one.

run nvidia-xconfig

reboot

hopefully its going now :S

---

