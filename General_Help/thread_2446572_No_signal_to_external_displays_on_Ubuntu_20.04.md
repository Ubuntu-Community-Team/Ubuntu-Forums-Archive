---
title: "No signal to external displays on Ubuntu 20.04"
date: 2020-07-03
forum: General Help
---

### Post by mmead on 2020-07-03
Hello,

I am having an issue getting a signal from certain external displays connected my Dell Precision 5540 laptop that came pre-installed with Ubuntu 18.04 LTS. I have since upgraded to Ubuntu 20.04 in the hopes it would fix my issue.

My issue is this: when I connect certain external displays to my laptop, the display is recognized in Gnome settings but the screen remains black with a "No signal" message. My laptop has an Nvidia T1000 GPU. I have the latest driver installed from Nvidia (nvidia-driver-440) and can verify the driver is running by running "ls mod | grep nvidia". I've seen similar bug reports online but so far none of the fixes have worked. I have tried:

1. Commenting out the modeset line in /usr/lib/modprobe.d/nvidia-kms.conf
2. Running lightdm instead of gdm3
3. Running nvidia-driver-435
4. Building the latest driver recommended for the T1000 from source.
5. Toggling the input source on the monitor

At this point, I am pretty sure it is a driver issue since I actually installed Windows 10 as a sanity test that I do not have a hardware issue -- all displays were recognized and displayed at the correct resolution using the same exact cable configuration. Interestingly, when a display with the "No signal" issue is connected, I can actually navigate my mouse off the window to the other display, but it obviously does not show up. Dropping the resolution to something extremely low does display an image to the screen, but obviously that is not a suitable solution.

---

