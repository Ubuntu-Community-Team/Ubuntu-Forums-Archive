---
title: "Cannot Login (Black Screen)"
date: 2005-10-22
forum: General Help
---

### Post by laissezfaire on 2005-10-22
Hi I am a linux newbie and I just wanted to install the latest Kubuntu on my new Laptop. Unfortunately, all I get after the installation is a black screen after about 2 minutes of a seemingly normal booting process. 
How can I correct this problem?

My video card is an ATI x700 and the monitor's native screen resolution is 1200x800

---

### Post by mlomker on 2005-10-22
Ctrl-Alt-F2

**sudo dpkg-reconfigure xserver-xorg** and try a different driver for now, perhaps vesa.

---

