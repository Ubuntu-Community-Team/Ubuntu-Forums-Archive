---
title: "HP EliteBook-850-G1 Laptop with a Radeon HD 8730M Graphics Card"
date: 2020-11-10
forum: General Help
---

### Post by amendt on 2020-11-10
I can't get my second screen working any more since I updated my kernel. I am running 20.04 with a 5.4.0052 kernel. 
If i run the command inxi -G I get
>  Device-1: Intel Haswell-ULT Integrated Graphics driver: i915 v: kernel 
  Device-2: AMD Mars [Radeon HD 8730M] driver: amdgpu v: 5.6.16.20.40 
  Display: x11 server: X.Org 1.20.8 driver: amdgpu,ati,modesetting 
  unloaded: fbdev,vesa resolution: 1920x1080~60Hz 
  OpenGL: renderer: Mesa DRI Intel HD Graphics 4400 (HSW GT2) 
  v: 4.5 Mesa 20.3.0-devel (git-fb1793b 2020-11-08 focal-oibaf-ppa) 
I tried installing amdgpu-pro-20.40-1147286-ubuntu-20.04 and everything installed ok, but nothing changes on "Screen Display" (no second monitor option)
Funny that it was working for a few months after a fresh install of Ubuntu 20.04
I tried 20.10 ubs boot and it still doesn't work.

---

