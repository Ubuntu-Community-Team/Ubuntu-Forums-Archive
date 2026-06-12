---
title: "Some help would be nice."
date: 2012-12-26
forum: General Help
---

### Post by CodyPy1 on 2012-12-26
Okay, so I have been using Ubuntu since about 10.04 it's worked real good. I've been through about 2 computers with it. All of which still work very decent. 

But i recently got a new laptop some hp bull crap thing. I have lamp and all that set up for my php development purposes. Usually when i have a problem i try to figure it out myself. But i just can't see to find this problem.

I'm running 12.04. It keeps freezing on me in the middle of important work. Which is getting very agitating. Originally i thought it was lamp so i reinstalled that. Then i thought it may have been one of my editors reinstalled them it still done it. I even tried removing them completely. 
I tried updating it numerous times. I even tried to upgrade to 12.10 but still it froze up on me.
I even tried a fresh install of 12.04 but it's still freezing up. 

Could it be my computer itself doing it? When i originally bought the computer it had windows 8. It would freeze up every now and then. But it would soon be responsive again. But now it just competely freezes won't give any responses or nothing. 

Any help with this would be very much appreciated. 

Thanks

-Cody

---

### Post by sudodus on 2012-12-26
Welcome to the Ubuntu Forums :-)

I would guess some problem with memory: swap, ram or hdd (logical or physical).

If the lockups will be released after some time it might be improved with changed swappiness or more ram.

But I have noticed that several of the really experienced guys are logged in now, let us hope that some of them will find this thread ...

---

### Post by N00b-un-2 on 2012-12-26
In my experience with HP laptops, their cases are not particularly well designed. Especially the ones with AMD processors and nVidia graphics cards.  I used to make a decent bit of money fixing HP laptops that suffered from the "black screen plague".  They would get so hot that the graphics chips would actually desolder themselves from the board over time, resulting in non functioning displays.  These laptops typically also suffer from random freezing/crashing issues due to overheating.
The least invasive thing you can try in most situations is to use a USB powered cooling mat for your laptop.  If you feel confident in you ability to disassemble your laptop and reassemble it, cleaning the internals of all dust and then treating your GPU and CPU chips/heatsinks with Arctic Silver can result in dramatically more efficient heat dissipation and can increase the life span of your laptop.

BIOS updates can also fix issues sometimes.  I own a secondhand Acer laptop that I installed Windows 8 on which would crash frequently and shut itself off under normal operation.  All of the issues I had with this computer were alleviated by updating the BIOS to the latest firmware.
Obviously, this is a case by case basis, but I would recommend looking into your EXACT model of laptop and seeing what other owners are saying they have issues with.

---

### Post by Cheesemill on 2012-12-26
Yep, sounds like it could be a hardware issue to me.

One of the first things to do is to boot into memtest (you can select this from the grub menu) and let it run overnight to check if your RAM is OK.

---

### Post by bodhi.zazen on 2012-12-26
Random freezes can be from a multitude of problems ranging from over heating (most common IMO) to wireless drivers to video drivers to failing hardware to problems within the kernel.

Hard to know your problem without additional information.

[https://help.ubuntu.com/community/DebuggingSystemCrash](https://help.ubuntu.com/community/DebuggingSystemCrash)

[https://wiki.ubuntu.com/X/Troubleshooting/Freeze](https://wiki.ubuntu.com/X/Troubleshooting/Freeze)

etc.

---

### Post by CodyPy1 on 2012-12-26
Thanks for the welcome! 

Also I did the mem test it passed once. 
I'm not real sure what the problem is but i updated and removed a few things and restarted it.

It seems to be running fine now. It hasn't froze up. But I think it may be some internal issue with the hardware itself. 

Seeing as how cheap this computer is and how crappy hp is. 

Thanks for all the assistance everyone!

---

### Post by Cheesemill on 2012-12-26
> **CodyPy1 said:**
> Also I did the mem test it passed once.
This doesn't mean the memory is definitely OK, it may be an intermittent problem.
You should leave it for at least several passes which is why I said to let it run overnight.

---

### Post by abrianb on 2012-12-28
Does this bug look familiar? If so sign on.
[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/993187](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/993187)

---

