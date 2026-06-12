---
title: "Poor video, flashing screen, no glxgears"
date: 2007-04-22
forum: General Help
---

### Post by laidback on 2007-04-22
I've put together a  new system which I am intending to use with Ubuntu, but to my horror I am having a few problems which appear to be associated with the video system. I can install/run 6.06 or 6.10 on the machine, but I keep getting screen flashes when I open a new package or create activity on the desktop. The flashing appears to be repetitive, i.e. it's the same image whenever I open OOo calc (in fact the left hand column repeated in the middle of the screen for a very short time). Similarly with OOo word and many other packages. The desktop flashes occassionally too.

Now like me you will say hardware problem, but I've tried other distros, Knoppix, Mepis and Mandriva, all are rock solid as I would expect. Even glxgears hardly works in Ubuntu, turning at a very slow rate with no printout or report. In Knoppix it runs at 587FPS, 2938 frames in 5 secs without any adjustment to the default video driver. 

I've been trying for the past week to resolve this but have to admit defeat. I've looked at 
$sudo dpkg-reconfigure xserver-xorg, and played with the settings. No change.
I've tried the CMOS/BIOS settings, giving max ram to video (128Mb). No change.
I've loaded new Nvidia drivers via Synaptic. No change
I've tried the legacy Nvidia driver via synaptic. Changes for the worse, got rid of that.
I've tried the same via EasyUbuntu. No change.
I've tried loading the latest Nvidia driver from the Nvidia site, but I've got into trouble here as to run the dowloaded file you need to exit from X. I thought that Ctrl+Shift+BackSpace did this, all I get is a reboot to the login splash screen. How do I stop the X server?

The hardware is:-
Gigabyte GA-K8N51GMF-9-RH mobo
1Gb Crucial ram, PC3200, DDR
on board video, nVidia GeForce 6100
Athlon 3500+ cpu
nVidia nForce 430 
usual CD/DVD RWs

The screen (same one) and video are rock solid on my earlier machine, which also runs 6.06LTS.

You assistance is much appreciated.

Kindest regards

Laidback

---

