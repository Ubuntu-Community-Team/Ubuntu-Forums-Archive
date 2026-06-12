---
title: "Ubuntu and Nvidia multi-GPU desktop crashes!"
date: 2019-11-30
forum: General Help
---

### Post by ProDigit on 2019-11-30
When installing more than 1 Nvidia GPU, and enabling overclocking (enable coolbits), one has to execute the 'sudo nvidia-xconfig --enable-all-gpus' command.
This command crashes the desktop.
It's a very basic setup, that never worked well in Ubuntu, when installing the .deb files, but in 16.xx, and 18.xx can be circumvented by installing the .run files from Nvidia.
Talk about making a working .run file into a broken .deb file, before adding them to the Linux repositories!...

This bug still is in Ubuntu, after nearly 4 years!
Granted, for 1 GPU it works fine. Multiple GPUs have problems with the desktop.
1- Desktop by default notifies of multiple crashes upon startup.
2- Desktop background displays last known window configuration, like a Windows 98 crashed window, that displays a trail of itself when you move it.
3- Desktop extends past screen, and when mouse goes off screen, the pointer can't come back on the screen, unless one uses a trick.(*)



*The trick to use when the mouse is off screen, is to change the display resolution to a higher resolution. A countdown window will pop up asking if you're ok with this new resolution, and only in this state can you recall the mouse. If the mouse gets off screen again, at the highest screen resolution, there's no other way to recall it, but to restart the pc.
Select 'no', and the screen reverts back to it's lower resolution, with a working mouse (if the mouse pointer didn't go past the X/Y position of the reverted (lower) resolution).

Crashes are present: ALWAYS when the 'sudo nvidia-xconfig -enable-all-gpus' command is executed from a .deb installed driver (and a reboot is done to bring the change into effect); or only on 19.04/19.10 even with the .run files.
The 'sudo nvidia-xconfig -enable-all-gpus' command, HAS to be enabled, to enable overclocking, fan speed adjustment, voltage regulation, or power limiting the GPU.

In other words, it's currently NOT possible, to run a desktop using 2 or more Nvidia GPUs, that have cool-bits enabled, without the ugly broken crashed desktop.
4+ years guys! Come on! There's really no one that has looked into a fix for this?

---

