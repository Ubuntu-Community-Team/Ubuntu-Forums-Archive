---
title: "Lenovo E540 issues with 14.04"
date: 2015-01-19
forum: General Help
---

### Post by mexp on 2015-01-19
I recently bought a new Lenovo Thinkpad Edge E540, and installed Ubuntu 14.04 on it. I ran in to a few problems:

1) Suspend did not work -> workaround was to disable USB 3 in Bios, which prevents using the Docking station.
2) Desktop freezes intermittently (apparently Nvidia issue, I couldn't find a workaround). Very annoying.
3) Compiz uses tons of memory, 400-600 MB after some hours of using the computer. Apparently some memory leak issue.
4) Also the battery life is not so great. I installed TLP, and still the maximum time I get with battery is around 3 hours.

Otherwise everything is running smoothly and well. I'm not so happy about the touchpad, but it could be a matter of getting used to it.

Does anyone here have experience of running 12.04 on similar machine instead? Any issues?

Specs for this machine:
RAM 4 GB
CPU Intel® Core™ i3-4000M CPU @ 2.40GHz × 4 
GPU GeForce 710M/PCIe/SSE2 (driver Nvidia 331.113)
HD 128 GB SSD

---

### Post by mexp on 2015-03-01
Replying my own question...

2 & 3: I tried several versions of Nvidia drivers, but always there was something wrong. 

Now I use nouveau, and things work great! I can use dual monitor setup, compiz uses 60-120 Mb of memory and the touchpad doesn't halt the system any more (not sure if this is related, though). 
To get out of freeze, shifting to tty1 (ctrl+alt+F1) and then back to Unity (ctrl+alt+F7) works.

---

### Post by YosSte on 2015-04-04
Thank you Mexp for sharing this,

Im having the same problems with my brand new ThinkPad Edge E540 ... it has i7 4712MQ processor and 8GB od RAM ... not a slow machine. I constantly freezes and crashes in different programs, I tried to play with the GTK (Oxygen is just buggy) which solved the problem atleast for my IDE, but now it completely freezes while browsing Chromium ... Currently I have a problem removing the Nvidia-update driver.

I have one more problem though :

5) Audio is very silent, also when a plug a headset or other audio device it gives  low volume , and I am sure this is not a hardware problem, as I had the same experience with HP laptop on Kubuntu 14.10 ... just shame , going to Arch Linux when a new SSD arrives.

---

