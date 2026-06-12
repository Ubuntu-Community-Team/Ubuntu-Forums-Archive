---
title: "Glitches and Lag observed in Firefox and Chrome in Ubuntu 14.04 LTS and NVIDIA"
date: 2014-10-27
forum: General Help
---

### Post by gauravdighe on 2014-10-27
Hello,

I am using Ubuntu 14.04. I have below hardware configuration:
500GB HardDisk
4 GB RAM
NVIDIA 9600GT - 1GB Graphics Card
Intel Core i5 1st Generation Processor.

I have below partitions installed:
500MB - /boot
50 GB - /
445 GB - /home
4800 MB - Swap

I have installed xorg-edgers ppa and installed NVIDIA-340 from Additional Drivers.

I have changed the NVIDIA settings:
Open-GL Settings - High Performance
Antialiasing Settings - Override Application Settings- 16x with Texture Sharpening enabled
Power Mizer - Prefer Maximum Performance

Since then I have observed below things:
1. Glitchess while opening a webpage on firefox
2. Lag in scrolling down a webpage in google chrome.

I did a fresh and clean install of Ubuntu and installed NVIDI-340. Previously, I never observed such things with Ubuntu 14.04 and NVIDIA-331 along with above mentioned settings(my previosu installation. Installation was corrupted due to compiz and i did clean install again).


I have attached the Additional-Drivers Screenshot. Please assist what I need to do and have I selected the right drivers?

[ATTACH=CONFIG]257538[/ATTACH]

---

### Post by CantankRus on 2014-10-27
> **gauravdighe said:**
>  I never observed such things with Ubuntu 14.04 and NVIDIA-331 along with above mentioned settings
Then why don't you just stick with the recommended drivers. (may need to purge the xorg-edgers ppa) 
or
make a bug report to the ppa where you installed the drivers from?

---

### Post by gauravdighe on 2014-10-27
I wanted to use new NVIDIA Drivers. Nvidia-343 thugh visible in Synaptic, its having issue and therefore I tried nvidia-340.
How to create a bug report ?

---

### Post by CantankRus on 2014-10-27
[**_[COLOR="#B22222"]A Beginners Guide to Filing Bug Reports[/COLOR]_**]("http://ubuntuforums.org/showthread.php?t=1011078")

---

