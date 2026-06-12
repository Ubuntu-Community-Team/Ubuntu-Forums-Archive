---
title: "Terrible battery life on newly-acquired Sony Vaio S15."
date: 2013-04-10
forum: General Help
---

### Post by Styleion on 2013-04-10
Hi everyone,

I just recently bought a new Sony Vaio S15, which came with Windows 8 preinstalled.
First thing I did was to install Linux and completely erase Windows, since I plan on virtualise it when needed instead of wasting disk space.

I installed the latest Ubuntu 12.10 version and most things are fine after installation with the exception of some important issues.
The most important setback is that the battery life I'm getting is horrible, about 1 hour 45 minutes (I checked the battery life on Windows 8 before removing it and it was more than 4 hours).
I've tried lots of things that I came across searching on Google: installed Jupiter, set power saving scripts, reduce screen brightness, etc. 
According to powertop my battery discharges at a rate of 23.6 Watts and It drains pretty quickly.

I'm running out of ideas and google searches. Anyone knows how to fix this and increase significantly battery life on a Vaio without making the laptop unusable? Should I remove Ubuntu and install another distro more suited for battery life (Fedora maybe) or that's a thing only dependant on the kernel?

Cheers.

---

### Post by Impavidus on 2013-04-10
It may be the graphics card (nvidia, isn't it?) not going into power saving mode. Have you tried installing proprietary drivers? That sometimes helps.

---

### Post by Styleion on 2013-04-11
Hi Impavides,

I've blacklisted the Nouveau driver and installed the proprietary driver downloaded from NVIDIA webpage but it seems something went wrong and, after rebooting, now I got a desktop with low resolution and nvidia-settings is telling me it can't find any gpu :/

---

