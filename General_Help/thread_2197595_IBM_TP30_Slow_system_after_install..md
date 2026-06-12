---
title: "IBM TP30: Slow system after install."
date: 2014-01-04
forum: General Help
---

### Post by aldokavcic on 2014-01-04
Hi,

My PC is an old IBM laptop TP30 this model has a P4-M 1.8GHz, 1 GB RAM & built in ATI 7500M. I usually run it on XP and  although it is a bit slow it does work acceptably OK.

 
I thought that ubuntu would be faster than my Win XP so I installed it. Also I was curious to see how we can work with it instead of WinXP. 

 
No mather what the whole system is awfully slow, I mean REALLy slow. It seems that any GUI operation is so slow.
Initially I thought my HD was the problem so I reinstalled on a different HD - same problem. Now I just installed for the thrid time 13.10.


 Could it be the video driver that I need to change? Or something in  the desktop display that I need to disable? Like disabling 3D? I think I have  read somewere that the videodrivers are not good with ATI.

I've spent the last days trying to read & understand how to fix this. I am really a beginner in linux, I can do the sudos but that's about it. From  what I understand I need to revert to some previous version of ubuntu  (12.10 ?) or change some components or is there another version of linux that  would work & allow me to have same functionnalities. Or should I use gnome-cinnamon instead of Unity?


 Anyways any help and guidance would be appreciated....

 THANKS A LOT in advance.

PS I also posted in lauchpad [https://answers.launchpad.net/ubuntu/+source/fglrx-installer/+question/241530](https://answers.launchpad.net/ubuntu/+source/fglrx-installer/+question/241530) so far not abble to resolve my problem.
PS2: glxgears give me between 35 & 45 fps. :-(
PS3: output of: 

sudo lshw -C display; lsb_release -a; uname -a
*-display
       description: VGA compatible controller
       product: RV200/M7 [Mobility Radeon 7500]
       vendor: Advanced Micro Devices, Inc. [AMD/ATI]
       physical id: 0
       bus info: pci@0000:01:00.0
       version: 00
       width: 32 bits
       clock: 66MHz
       
capabilities: agp agp-2.0 pm vga_controller bus_master cap_list rom
       configuration: driver=radeon latency=66 mingnt=8
       resources: irq:11 memory:e8000000-efffffff ioport:2000(size=256) memory:d0100000-d010ffff memory:d0120000-d013ffff
No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu 13.10
Release:	13.10
Codename:	saucy
Linux

---

### Post by Bucky Ball on 2014-01-04
*Post moved to own thread.*

---

### Post by mörgæs on 2014-01-05
Hi, welcome to the fora.
You will be better off with Lubuntu 13.10.

---

### Post by Bucky Ball on 2014-01-05
> **mörgæs said:**
> Hi, welcome to the fora.
You will be better off with Lubuntu 13.10.

+1. You could try Lubuntu or Xubuntu (I have Xubuntu 12.04 LTS running fine on a P4 with 1Gb RAM actually).

---

### Post by aldokavcic on 2014-01-06
Hi Morgaes & BB

Thanks for your reply & suggestion. As I am getting more & more familiar with Ubuntu not sure I want to switch. Any major drawbacks with Xubuntu or Lubuntu? I remember I tried Xubuntu 12.10 last year and there was something rather major missing I think it was Flash or Firefox. I want both. After all I have them with XP. I'll look into that or if anyone has the answer it would be appreciated. I also need the Open Office suite.

Regarding the Radeon-ATI drivers if I go with those versions will I have the necessary drivers for my Radeon  7500 card? I don't want to erase my installlation just to learn that no  graphic drivers available. I think (I might be wrong) the first  thing to solve is this. Is there anyone here with the necessary knowledge that can help me to get the best possible drivers (on ubuntu)? After all 35-45 fps is very low we can surely (I hope) improve this a lot?

Again thanks in advance to anyone that would kindly help, your input it is very much appreciated.

S-)

---

### Post by Bucky Ball on 2014-01-06
Flash and Firefox missing in Xubuntu? Just install them! That's what Linux is about. Make the system you want, you're not stuck with the default apps. Heck, install Xubuntu and stick in the Unity desktop from Ubuntu if you want (although, in your case, that will just make a heavy distro again). Customise however you want.

---

### Post by QIII on 2014-01-06
Hello!

That's an old RV series card and it will not be supported by a Linux driver from ATI.  The default open source Radeon driver will probably be fine.

---

