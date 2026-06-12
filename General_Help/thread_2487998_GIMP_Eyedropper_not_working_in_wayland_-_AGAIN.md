---
title: "GIMP Eyedropper not working in wayland - AGAIN"
date: 2023-06-20
forum: General Help
---

### Post by corradoventu on 2023-06-20
GIMP 2.10.34-1 eyedropper on Wayland does not work outside gimp window.
[https://bugs.launchpad.net/ubuntu/+source/gimp/+bug/2024317](https://bugs.launchpad.net/ubuntu/+source/gimp/+bug/2024317)
Problem was not present with GIMP 2.10.30-1build1 on Ubuntu 22.04
but has reappeared in Ubuntu 23.04 and 23.10
Note: eyedropper is different from color picker, color picker picks color from gimp image, eyedropper should pick color from anywhere on your screen.

---

### Post by Holger_Gehrke on 2023-06-20
I am using GiMP 2.10.30-1build1 on XUbuntu 22.04 on X11 and the eyedropper (from the color selection form) doesn't work here either. I suppose since it's a function that needs to be implemented differently depending on whether the program runs on X11 or Wayland it's going to flip and flop between working on either or not a few more times before they find a solution ...
The obvious workaround is to make a screenshot, open that in GiMP and pick a color from the screenshot.

Holger

---

### Post by corradoventu on 2023-06-21
So if you have an account on launchpad please note your problem on my bug. thanks.

---

