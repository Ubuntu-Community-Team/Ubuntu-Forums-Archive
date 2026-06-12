---
title: "Video Card/OpenGL driver bug with Steam?"
date: 2013-02-21
forum: General Help
---

### Post by IceFlame1019 on 2013-02-21
Hey,

My apologies in advance if this has been answered somewhere but the Search didn't turn up anything relating to my problem :s  Also kinda under a time limit for this...
Also sorry if this is in the wrong subforum, I'm terrible with forum placements >_<;

Steam recently added support for Linux and I wanted to try Ubuntu to see if it'll be a viable fallback for my gaming if this old Dell laptop kicks the bucket (whole slew of issues that I won't go into detail here).  There is also a Linux promo for Team Fortress 2 offering an item if one logs in to TF2 on a Linux system before the first of March.  Missing the item isn't that big a deal really, it's just something I'd like to have, but I also want to see how well TF2 works on Ubuntu.

I installed Ubuntu, as advertised by Steam (I believe it's 12.10), and installed Steam and Team Fortress 2.  However, when I try to run TF2, it gives me an error message:
> Could not find required OpenGL entry point "glColorMaskedIndexedEXT"!  Either your video card is unsupported, or your OpenGL driver needs to be updated.The only topics I could find about OpenGL or video drivers are from way back in 2010 :s so...if anyone could help me with this, I'd very much appreciate it.

Thanks for your time, and sorry again if this is out of place or answered somewhere else, I'm terrible with forums @_@

--Ice


SYSTEM SPECS (as read by Ubuntu):
Memory: 3.0 GiB
Processor: Genuine Intel CPU T2500 @ 2.00GHz x 2
Graphics: Unknown
OS Type: 32-bit
Disk: 0 bytes

Ubuntu was installed using the Wubi installer, which gave a maximum partition of 30GB. 

SYSTEM SPECS (as read by Windows 7)
Dell Precision M90
Memory: 4.00 GB RAM (3.00GB usable)
Processor: (same as above)
OS Type: (same)
Display Adapter typer: NVIDIA Quadro FX 1500M
Total available graphics memory: 1535 MB
Dedicated graphics mem: 256 MB
Dedicated system mem: 0 MB
Shared system mem: 1279 MB
DirectX version: DirectX 9.0 or better

(when in Ubuntu Steam's system specs reader says the graphics driver is "nouveau Gallium 0.4 on NV49", if this helps any)

EDIT: 
I just installed "nvidia-current" through the terminal using the code ```
sudo apt-get install nvidia-current
```.  My other issue of screen being dimmed has been solved with that, but I'm still getting the error for TF2.  I'm assuming this is an OpenGL error then?  Or are there other video drivers I need to install?

---

