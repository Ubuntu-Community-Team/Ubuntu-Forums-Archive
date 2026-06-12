---
title: "low latency kernel for gutsy"
date: 2007-12-21
forum: General Help
---

### Post by ZeldaFan on 2007-12-21
How do you install the low latency kernel in Ubuntu gutsy. I don't want to install Ubuntu Studio or upgrade to it, because at this point I'm not interested in all of the audio packages and such. I was just installing the Enemy Territory Quake Wars demo and it recommended that I use a low latency kernel, so I figured I might as well install it to maximize performace.

---

### Post by dcstar on 2007-12-21
> **ZeldaFan said:**
> How do you install the low latency kernel in Ubuntu gutsy. I don't want to install Ubuntu Studio or upgrade to it, because at this point I'm not interested in all of the audio packages and such. I was just installing the Enemy Territory Quake Wars demo and it recommended that I use a low latency kernel, so I figured I might as well install it to maximize performace.

Synaptic-Name Search "-rt" and install all the packages you need.

---

### Post by jayson.rowe on 2007-12-21
> **ZeldaFan said:**
> How do you install the low latency kernel in Ubuntu gutsy. I don't want to install Ubuntu Studio or upgrade to it, because at this point I'm not interested in all of the audio packages and such. I was just installing the Enemy Territory Quake Wars demo and it recommended that I use a low latency kernel, so I figured I might as well install it to maximize performace.

There is a HUGE difference between a "Low Latency" kernel and a "Real Time" kernel. Feisty had a "Low Latency build, but no "Real Time" - Gutsy has a "Real Time" with no "Low Latency".

A Real Time Kernel will hurt your overall performance rather than help it. Trust me!

If you need a Low Latency kernel in Gutsy, search out the "Master Kernel Thread" here on the forums and build your own - keep all the default options of the Ubuntu kernel except turn on Pre-emption and change Config_Hz=250 to Conifg_Hz=1000.

---

### Post by ZeldaFan on 2007-12-22
Well recompiling takes a pretty long time, I want to only resort to that as a last option. I am only going to use this kernel exclusively for the game, nothing else. I want it to be available as another option in my grub menu, not as my default kernel option. For everyday desktop use, I would use the generic kernel. So couldn't I just install the real time kernel. Overall performance should naturally suffer, because it dedicates most of its CPU processes to one program. So unless it makes everything slower, I might as well install  it, right? I'm not going to use it for anything else except the  game.

---

### Post by Steven_B on 2007-12-23
> There is a HUGE difference between a "Low Latency" kernel and a "Real Time" kernel. Feisty had a "Low Latency build, but no "Real Time" - Gutsy has a "Real Time" with no "Low Latency".
Could you explain the difference?  Everything I've read seems to say that a low-latency kernel is similar to real-time, just not quite.

---

