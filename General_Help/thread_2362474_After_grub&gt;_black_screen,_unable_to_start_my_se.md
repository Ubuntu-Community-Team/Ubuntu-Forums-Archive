---
title: "After grub&gt; black screen, unable to start my session"
date: 2017-05-29
forum: General Help
---

### Post by caema on 2017-05-29
Hello all,


I am in possession of an Acer Aspire V15, whose configuration is as follows:


Processor: Intel Core i7-6700HQ
RAM: 12GB
Graphics card: Nvidia Geforce GTX 960 M


I have a dual boot Windows 10 | Xubuntu 16.04 LTS.


Yesterday, I did a lot of stuff, so a global update of my packages (if my memories are good).
Small pause, I close the cover of my laptop.


1h later, I reopen the cover of my laptop: black screen, impossible to take the PC out of its watch.
To the barbarian, I hold the power button to cut the PC, and I then restart: Bios, grub where I select Xubuntu,
And there it is the drama: black screen that seems "blink", from time to time I can see in the upper left corner the pointer console that blinks, but nothing more ... basically, I can not do anything.
So I have to shut down my laptop again with the power button pressed: when I do this, I can see the Xubuntu screen blue sky, then the PC turns off.


Do you have any idea what's going on, and especially how I can solve that please?


I specify that the PC works well, there I am on my Windows 10 session and I have no worries.


In advance thank you for what you can bring as help.

---

### Post by yancek on 2017-05-29
You did a "global" update of what, Xubuntu or windows?
Are you saying that you can still boot windows 10 but not Xubuntu?

---

### Post by caema on 2017-05-30
> **yancek said:**
> You did a "global" update of what, Xubuntu or windows?
Are you saying that you can still boot windows 10 but not Xubuntu?


I made a Global update of Xubuntu, with ```
sudo apt-get update
```.
And yes, the computer can boot on windows 10, but if I choose Xubuntu in the grub, I have the problems I describe in my first post.

I have the feeling that it can be a problem with the drivers of my graphic card: I say that because the screen seems "Flashing".
I thought I could install old drivers, but I don't have access to Xubuntu so... It's difficult ;-)

May be it's possible, but I don't know HOW ?

Thanks for reply dude ;-)

---

### Post by oldfred on 2017-05-30
Can you boot recovery mode, or second line in grub menu?

Abnormal shutdown often causes corruption. In Windows you run chkdsk. If ext4 standard partitioning in Linux you run fsck from live installer.
But it seems you can start to boot, and have more like a video issue. Unless that is the corruption fsck may not help.

If you installed nVidia driver from repository you may just need to reinstall same driver from recovery mode.

 Never force shutdown your system. Use Alt+SysRq R-E-I-S-U-B instead. (For newer laptops they don't bother adding the SysRq print to the key, but it's the same as the PrtScr key) 
   Holding down Ctrl+Alt and SysRq (which is the Print Screen key) while slowly typing REISUB
R-E-I-S-U-B to force shutdown
A good way to remember it is, and S can be before E, but others should be in order
Raising Skinny Elephants Is Utterly Boring ...or
Reboot System Even If Ultimately Broken ...LOL.
[https://en.wikipedia.org/wiki/Magic_SysRq_key](https://en.wikipedia.org/wiki/Magic_SysRq_key)
[http://kember.net/articles/reisub-the-gentle-linux-restart/](http://kember.net/articles/reisub-the-gentle-linux-restart/)

---

