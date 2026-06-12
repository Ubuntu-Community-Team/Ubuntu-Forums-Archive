---
title: "nvidia binary drivers -- no display"
date: 2005-10-28
forum: General Help
---

### Post by jargoone on 2005-10-28
Hi all-

Ubuntu n00b here, but very familiar with Linux in general.

I just built a system around a Shuttle SN85G4v2, which has an nForce3 chipset.  The video card is an nVidia FX5200.  I installed Breezy, added all the repositories, and installed nvidia-glx.  I ran "nvidia-glx-config enable", and when X restarts, I get nothing.  My LCD blanks out and goes into suspend.  I've tried Ctrl-Alt plus and minus, and also tried to switch over to another virtual console -- nothing.  When I disable the driver from single user mode, everything works fine again.

The only thing changed in my xorg.conf by nvidia-glx-config is the name of the driver.  I don't see any obvious problems.  Can anyone help?

---

### Post by budluva04 on 2005-10-28
did you change your xorg.conf under Display look for "nv" and change to "nvidia"

give that a try

---

