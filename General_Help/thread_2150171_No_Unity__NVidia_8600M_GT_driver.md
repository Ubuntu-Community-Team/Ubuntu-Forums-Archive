---
title: "No Unity / NVidia 8600M GT driver?"
date: 2013-05-31
forum: General Help
---

### Post by drbh on 2013-05-31
I am a Linux newbie, I just installed Unbutu 13.04 on an AREA 51 M15X-R1 and I am having some issues with the configuration. I cannot find the right driver for the NVIDIA 8600M GT. I tried to install nvidia-current from the software store and on the reboot the resolution was ten times worse and UNITY will not load.[CENTER]How do i remover the bad drivers?
Make Unity reappear?
What driver should i install?


[/CENTER]
I need to get the graphics card working asap, the laptop only has HDMI out and the screen is terribly cracked. I cant get the image on the tv without first installing the nvidia drivers (on windows) so how do I fix this in Ubuntu?

---

### Post by dino99 on 2013-05-31
about the driver : purge the installed ones, then install nvidia-313-updates

about unity, open a terminal (ctrl+alt+T) and run:
> compiz --replace ccp &
> setsid unity

you can also install and log with gnome-shell, which is an unity like feeling

---

### Post by drbh on 2013-06-03
noob question, but how do i purge the drivers i have? i think i have i915 drivers.

---

