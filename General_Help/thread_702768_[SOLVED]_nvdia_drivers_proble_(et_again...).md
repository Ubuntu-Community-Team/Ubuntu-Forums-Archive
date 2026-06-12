---
title: "[SOLVED] nvdia drivers proble (et again...)"
date: 2008-02-20
forum: General Help
---

### Post by orlox on 2008-02-20
Hi!

I just aquired a e-geforce 6200 (256mb) video card so I could enable desktop efefcts and play some games...But i've found problems with any method I've found. Always, it happens that when GDM starts, the system only lasts a few seconds and then completely freezes (I cant move the mouse, sound stopst, can't shutdown GDM, etc...)

The things I've tried are:

-envy, uninstallign everything, and then installing the latest restricted drivers with envy
-installing the restricted drivers from the repos
-using an older version of the driver (NVIDIA-Linux-x86-100.14.11-pkg1) with no result...

I'm a gutsy user, and my kernel is 2.6.22-14-generic. I also tried a couple more methods I can't remember right know with the same results...

---

### Post by orlox on 2008-02-20
tried another thing...

used the nvidia-glx package from the repos. This at first gave me an error that it couldn't find /lib/modules/2.6.22-14-generic/volatile/nvidia.ko, but I red that this could be solved by running lrm-manager before X starts. Even though I did this, the only result was that when X started, I got a glitch of the NVIDIA logo and then everything went black :(

---

### Post by socceroos on 2008-02-20
I would start afresh.

Reconfigure xserver and try installing the official restricted drivers (first completely remove them from synaptec).

To reconfigure xorg you need to run this command from a terminal:

```
sudo dpkg-reconfigure xserver-xorg
```

And follow the prompts. The defaults should work. Remember to select the resolutions that you know work for your monitor too.

---

### Post by orlox on 2008-02-21
Been using that constantly, although, the defaults aren't what i'm looking for since they use the nv driver instead of the restricted nvidia driver.

By using the drivers that ubuntu installs thorugh the GUI (wich correspond to the package nvidia-glx-new) and then setting xorg with dpkg-reconfigure to work with this driver (althoug as far as I know, ubuntu does this automatically..) just lets me initiate X for a short time and then freezes (completely, even sound stops and it's imosible to stop GDM), without being usable for even a second.

When i need to restore the system, I use dpkg-reconfigure to set xorg to work with the vesa driver (the default nv driver causes some freezes..)

---

### Post by orlox on 2008-02-21
Well, nothing I've found seems to work, guess I'll just have to try a fresh install on another partition to check if it works with the nvidia drivers....

...the last thing that's lost is hope :P...

---

### Post by orlox on 2008-02-23
A fresh install didn't work, although I got a better performance with the nv driver (it froze the system after like 5-10 minutes of use).

I also tested this on ubuntu 7.04 (wich uses nvidia-glx instead of nvidia-glx-new) and it didn't work.

But, I tried the card on my sister's PC wich has a different MOBO and ubuntu 7.04 installed and worked almost instantly, I just had to download the restricted drivers and voila! got 3d acceleration and desktop effects running OK.

After that I putted my sister's hard drive on my own PC and guess what...I got the same issue, the system froze seconds after initiating GDM.

So, my best bet, is that it has something to do with the motherboard and not related to ubuntu or the drivers...Maybe updating the BIOS could help somewhat, so I'm trying to do this right now. The only problem, is that the file given by ECS (the manufacturer) has an exe file to do this :mad::mad::mad: and I can't retrive the appropiate commands to flash the BIOS :mad::mad::mad:

(By the way, my mobo model is p4m800pro-m v1.0a)

---

### Post by orlox on 2008-02-23
Solved! I flashed the BIOS and installed NVIDIA-Linux-x86-100.14.11-pkg1drivers again (I was able to use the nvidia-glx-new drivers that ubuntu installs but they were far too unstable). After this, Everything is working OK:):):):):)

only a little problem...the bios flashing seems t:) have screwed my ethernet, now I have to restart CMOS every time I start the computer to have ethernet....

---

