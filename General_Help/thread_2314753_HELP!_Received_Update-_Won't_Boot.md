---
title: "HELP! Received Update- Won't Boot"
date: 2016-02-23
forum: General Help
---

### Post by sasafrass452 on 2016-02-23
I received this morning's update, & now the system won't boot. I reinstalled Xubuntu from a 14.10 disc, upgraded back to 15.10, & got the same result. I waited 10 min, staring at the blank/black screen, hoping it would eventually continue. Nothing happened. I walked away, & came back 17 min later.... still nothing. No indication of hard drive activity. Zip. Zilch. Nada. I can only assume this is a compatibility issue with the update, since my laptop is very old. Unless there is some way to make it work again? I have a lenovo t-400. I'm not too happy about spending money on a new laptop, but if I must....

---

### Post by yoshii on 2016-02-23
I would re-install Xubuntu from a 14.04.3 LTS DVD-ROM instead.  I know it's older, but it's probably more of a stable baseline and should have your older hardware supported.  
Did you try 32-bit or 64-bit?  I suggest the 32-bit one for more likelihood of compatibility.

---

### Post by QDR06VV9 on 2016-02-23
sasafrass452 Hey have you tried to add nomodeset to your boot options yet?
When it begins to boot Hit F6 and you should see the "linux" string at the bottom. Just go the the end and add "nomodeset".
Do you have a hybrid graphics GPU?
Ninjed by yoshi..

---

### Post by sasafrass452 on 2016-02-23
Yoshi, I've been using 32 bit. Also, I was having issues with 14x that 15x fixed, so I'd prefer not to downgrade.

Runrickus, a hybrid graphics gpu? If you mean 3D, no. Otherwise, I really don't know but most likely not.

---

### Post by volleronline on 2016-02-23
I have experienced this same issue today on 3 Ubuntu VM's... 2 14.x vm's and one 15.x vm.

Always the same experience. Install the base OS, works fine. 
Run updates once, upon restart none of the vm's comes up.

---

### Post by QDR06VV9 on 2016-02-23
> [SIZE=2]**nomodeset**[/SIZE]
The newest kernels have moved the video mode setting into the kernel.   So all the programming of the hardware specific clock rates and  registers on the video card happen in the kernel rather than in the X  driver when the X server starts.. This makes it possible to have high  resolution nice looking splash (boot) screens and flicker free  transitions from boot splash to login screen. Unfortunately, on some  cards this doesnt work properly and you end up with a **black screen**. Adding the nomodeset parameter instructs the kernel to not load video drivers and use BIOS modes instead until X is loaded. 

Source:  [http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)

---

### Post by sasafrass452 on 2016-02-23
Well, I tried adding "nomodeset", & it didn't work. Any other ideas?

---

### Post by QDR06VV9 on 2016-02-23
I am afraid yoshi might have the best option ATM
I have seen what your specs are now and XFCE or LXDE (lubuntu) looks like some options to consider.
Not what you wanted i know :(

---

### Post by sasafrass452 on 2016-02-24
Won't LXDE & XFCE give me the same problem, if it's kernel related? Don't they all use the same kernel?

> **runrickus said:**
> I am afraid yoshi might have the best option ATM
I have seen what your specs are now and XFCE or LXDE (lubuntu) looks like some options to consider.
Not what you wanted i know :(

---

### Post by QDR06VV9 on 2016-02-24
Well I am at a loss for your problems with the kernels from 14.04 you have not said what they were.. But you could install a newer kernel in 14.04.
Currently I am running 4.3 Low Lat on 14.04.4 64Bit Heavily Tweaked...and it fly's.

---

### Post by sasafrass452 on 2016-02-24
Well, I attempted to install Lubuntu, but the disc wouldn't even load. It gave me errors, something like "line a20 is already enabled" & "cannot find unused 64 kilobyte memory...." something or other.... I can't remember the whole sentence. I'm at a loss now, I have no clue what to do.

---

### Post by QDR06VV9 on 2016-02-24
Been many years since I have seen that.
I think this means that you burned the iso onto the disk as data, instead of using the ISO to burn the disk as an image.
what application are you using to burn the .iso with?

---

### Post by sasafrass452 on 2016-02-25
I did burn it as a bootable image, using nero on a family member's window$ computer. I guess it's just not compatible with my old laptop.

> **runrickus said:**
> Been many years since I have seen that.
I think this means that you burned the iso onto the disk as data, instead of using the ISO to burn the disk as an image.
what application are you using to burn the .iso with?

---

### Post by sasafrass452 on 2016-06-02
Hello, everyone. First off, my appologies for not getting back here sooner. I attempted once again to burn the boot-repair disc, & it still wouldn't run. I even tried it on my mother's laptop, which is the same old model as mine, also running xubuntu but without the update(s) that caused my boot failure. This time, it gave me a choice of language, but then the screen went black & nothing happened. Anything I can do, or is it time for a new laptop?

---

