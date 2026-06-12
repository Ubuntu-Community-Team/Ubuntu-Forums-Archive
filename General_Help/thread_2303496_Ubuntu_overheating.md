---
title: "Ubuntu overheating"
date: 2015-11-19
forum: General Help
---

### Post by soulblasted on 2015-11-19
So I installed ubuntu 15.10 because i needed something more stable for work and thought easy out of box would be nice for change but it's overheating. Idling temperatures is 70 C. This is not hardware issue nor any process consumes much cpu around 1-2% total! On arch idling temp is ~50 C and on funtoo around 45 C. It is ubuntu problem. I have nvidia optimus laptop and current installed driver is nouveau which i always use. So i have no idea how to fix this since it seems to be ubuntu specific.

---

### Post by Vladlenin5000 on 2015-11-19
Hi and welcome.

> **soulblasted said:**
> I have nvidia optimus laptop and current installed driver is nouveau which i always use.

This is most likely the root cause. The open source driver is good for most scenarios and nvidia hardware out there but it's far from perfect. You probably need to install nvidia proprietary drivers (and nvidia prime due to optimus) for better performance.

---

### Post by soulblasted on 2015-11-19
Thank you for reply but i think im giving up on ubuntu... It's bad tbh and fixing all this is more complicated than setting up fresh arch install and installing all i need. Now mobile broadband doesnt work and all i did was turn off laptop to cool down. It connects but it doesnt, still no internet access and no errors whatsoever and it worked first time. Nouveau driver works fine on arch and funtoo but not on ubuntu I mean wtf? It's probably just my luck..

---

### Post by Vladlenin5000 on 2015-11-19
Well, to each its own... That said, there are also a few details you should be aware of:

As an Arch user I expect you to have an higher than average understanding of desktop environments and their requirements. Also, you're certainly aware that standard Ubuntu uses Unity which is a high demanding desktop, requiring powerful 3D Graphics acceleration whereas anything you'll be using in Arch, Gentoo and derivatives don't even come close. So, nouveau may be enough for the latter, i.e., no noticeable difference when compared to the nvidia drivers in lightweight DEs but certainly not enough for a DE like Unity. That alone may account for the different temps you've been experiencing.

In a nutshell, you're comparing the system requirements of a (striped down) Windows 98/2000 with a full featured eye candy galore Windows 7.

---

### Post by soulblasted on 2015-11-19
Well i like unity and idea of ubuntu thats why i installed it, but on my laptop it has too many problems to be worth the trouble. I never had such problems even with kde with all effects enabled (unity shouldnt be more heavy right?), and network problems are not DE related (at least i hope so). Don't get me wrong i dont have anything against ubuntu in general, i was just frustrated since i wanted to get some work done and hoped ubuntu would just work and that i would save time (i currently have only funtoo installed and compiling takes a while), i apologize for ranting.

---

### Post by mastablasta on 2015-11-19
so arch with latest kernel performs better than Ubuntu with older kernel - shocking! especially since you use the opensource drivers which are part of kernel. 

network --> network driver -->  kernel issue
GPU heat & performance --> opensource driver -->  kernel issue
GPU heat & performance --> proprietary driver --> NVidia issue

you can install newer kernel in Ubuntu as well.

on one hand you do not want things complicated. well if so, all you would need to do is use the additional driver app to install NVidia drivers. maybe then add bumblebee (all it takes is click on the PPA link AFAIK) so you can use either NVidia or Intel. and that's it. all in all 2 or 3 mouse clicks must be exhausting.

also if Arch works well why bother with Ubuntu at all? stability ? well using dev version of everything (like in Arch) won't make it stable. but you will get the newest and latest stuff. so there is a tradeoff.
 Ubuntu is well positioned and offers stability to which you can add various dev and beta things and hope it will stay stable. like adding only new GPU drivers and keep all other stuff at stable. and it just might stay stable.

by the way 15.10 and other intermitent versions are again experimental ground. though images are considered stable and frozen, they are meant to showcase new features, often include various smaller "experiments" that will ultimately land in LTS. so if it's stability that you want you should go with LTS and use hardware enablement stack to pull in latest kernels.

---

### Post by soulblasted on 2015-11-19
I wanted ubuntu for stability and i thought 15.10 would be stable enough while more up to date than lts and i quite like whole look and feel. Arch is perfectly stable for daily use but I find it bit annoying for development i have problems from time to time which I'd rather avoid. I'll probably just set up vagrant box but i would have preferred to cut the middle man and just use ubuntu. Again this is probably issue with ubuntu and my laptop not ubuntu in general.
 So if I read your post correctly, you recommend latest kernel + bumblebee? I can do that, if i manage to get online again ill also install something light weight like dwm or bspwm and see if its unity problem. 
And im not complaining that ubuntu is slower or not enough bleeding edge or whatever, my problem is 20 degrees higher _idle_ temp (which is pretty bad, its unpleasant to type on keyboard) and inability to get online after one reboot (it worked fine first time) and no errors or anything, and kernel version is 4.2 which was same kernel i used on arch before i installed ubuntu over it!

---

