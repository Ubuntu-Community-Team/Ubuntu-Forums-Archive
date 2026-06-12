---
title: "How to use desktop using Xorg on one GPU with two GPUs connected"
date: 2020-03-23
forum: General Help
---

### Post by brm512 on 2020-03-23
Hi

I'm trying to set up my system to use two GPUs (Maxwell Titan X and GTX 1060). I'm using NVIDIA X Server GUI (see image). I really only want to use the one GPU for display, but only the card in the first used PCIe (PCI1) slot outputs the desktop environment.
Also if the PCI1 card has no attached monitors, it also still does not output on the PCI4 card. I cannot swap cards around for air flow reasons.

I've tried fiddling with xorg.conf (deleting the device I don't want to use) slightly with no luck. I'm trying to use NVIDIA X Server GUI and got second GPU to use a new XScreen but it's only a black screen with the mouse cursor as an X symbol.

Any direction on how to set up the desktop to use the other XScreen? Any advice greatly appreciated.

---

