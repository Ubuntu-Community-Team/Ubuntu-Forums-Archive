---
title: "Ubuntu turns slow over time and needs restart"
date: 2018-05-28
forum: General Help
---

### Post by ajmannen on 2018-05-28
Hello! I have this weird problem, I'm not even sure what logfiles to post. 
On my Laptop, a ThinkPad X1, Ubuntu works just fine for the first hour or so, then it gradually get's slower and slower, untill it is no longer usable and I have to restart my laptop. After a restart things work great again, I do not have the same problem in Windows.

I've tried using Ubuntu 16.04, 17.10 now on Ubuntu 18.04, pretty vanilla setup. I've also tried KDE Neon with the same problem there. 

I'm a CS student, so I mostly just spend time doing some pretty noob level programming, nothing heavy, going PHP now with VS Code. But the same problem happens even when I'm just browsing the net. I tried to find a process that takes up all the "juice" but I couldn't see anything that stood out in htop. 

Any advice? At least what logfiles I can look at.

---

### Post by SL0ltMJGyh on 2018-05-28
How much swap space do you have allocated on your machine with "swapon -summary"? Also, KDE is not really a lightweight desktop- XFCE or LXDE are lighter. What desktop manager are you using? Xorg, Wayland, X11, etc? All of these things can be contributing factors to slowness.

---

### Post by ajmannen on 2018-05-28
Tried both with Wayland and XORG, also had the same problem with Linux Mint running cinnamon. 

I have assigned 8 gb of swap and 250 gb of SSD space on my m2 SSD. 

Currently running Gnome in Ubuntu 18.04, it's a vanilla install. My processor should be good enough for both Gnome and KDE 
CPU Info:  Intel(R) Core(TM) i7-6500U CPU @ 2.50GHz

---

### Post by Yellow Pasque on 2018-05-28
I would monitor the output of 'free -m' to see if you have a memory leak.

---

### Post by Impavidus on 2018-05-28
Also try top or htop to find out if any processes consume excessive CPU or memory. It smells like a memory leak.

---

