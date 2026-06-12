---
title: "incorrect screen size"
date: 2017-08-25
forum: General Help
---

### Post by zedi on 2017-08-25
I would like to know why my NEW monitor L**G Electronics LG IPS FULLHD 27"** is recognised correctly by Nvidia driver but Display detects a **Goldstar Company LTD 22"**. 
Command: xrandr | grep connected tells me: 
VGA-0 connected primary 1920x1080+0+0 (normal left inverted right x axis y axis) 480mm x 270mm

But my screen size is around***600mm x 340mm***(not***480mm x 270mm**). Measured by ruler.
So it's not near the truth. Not even close.
I connected monitor with HDMI but `Display` still showed 22 ” instead 27 ”.

Kernel: 3.19.0-32-generic x86_64 (64 bit)
Graphics Card: NVIDIA GK107 [GeForce GT 640]
Display Server: X.Org 1.15.1 driver: nvidia
Resolution: 1920x1080@60.0hz
GLX Renderer: GeForce GT 640/PCIe/SSE2
GLX Version: 4.5.0 NVIDIA 375.66

---

