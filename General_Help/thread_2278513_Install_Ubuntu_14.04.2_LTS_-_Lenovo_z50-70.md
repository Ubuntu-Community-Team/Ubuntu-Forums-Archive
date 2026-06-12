---
title: "Install Ubuntu 14.04.2 LTS - Lenovo z50-70"
date: 2015-05-17
forum: General Help
---

### Post by danutz332 on 2015-05-17
Hi everyone and first of all I'm sorry for my bad English becouse is not my primary language.
I have a Lenovo z50-70 with i5 1.70 GHz, Nvidia 840m 2 GB and 4 GB ram with a SSD 250 GB. I want to install Ubuntu on this laptop and I facing with some problems. This laptop went with Windows 8.1 preinstalled and along time I installed Windows 8.1 cracked on legacy support and Ubuntu, but with Ubuntu I have problems with nvidia drivers(screen tearing, slow desktop environment, etc.) I want to install Ubuntu new and clean but I don't know what settings have in BIOS on UEFI or Legacy support, and what partitions make for best results. In Ubuntu I don't have proprietary drivers in additional drivers, everytime I installed drivers with xedges ppa like in tutorials but have desktop freeze and screen tearing, slow desktop environment, etc. I install new Ubuntu right now becouse i want to start new with your help becouse i don't want anymore screen tearing and other problems. Can you help me with settings in BIOS and partitions for best results becouse i want to install nvidia drivers without problems. I want someone help me with setting up Ubuntu for my laptop run flawsely and smooth with games and tasks. Please help me to configure my laptop. Apologize for my very bad English, becouse i learn it in primary school. Thank you very much for read my thread with my problems with English language.

EDIT: I have hybrid graphics intel and nvidia.

---

### Post by mc4man on 2015-05-17
Very simple in regards to Nvidia mobile chips (optimus)
If you want to use Ubuntu or any other compositing window manager DE  then don't bother with the nvidia drivers thru nvidia-prime, you will get tearing everywhere. The Intel 4000+ gpu is quite fine & suitable for most users & uses.

If you must use nvidia for whatever reason then - 
1. Use windows
2. Find a non compositing DE, then tearing may only occur on some videos
3. See if bumblebee still works, then nvidia is only used 'on demand',  otherwise the tear free Intel is used
4. Hope Mir or Wayland resolve this issue down the road
5. Get a desktop computer

I find recent  Intel is absolutely fine  & have no reason to use the nvidia chip on this Lenovo here (Y510P

---

### Post by danutz332 on 2015-05-17
Thank you for reply, i want Ubuntu or whatever version of Linux which are user friendly based on Ubuntu, becouse of fiability and is a stable OS in time. I don't want to be a Windows user becouse of problems and instability.
I want to know how to use intel graphics when i do some task on desktop and browsing, but i want when i am in a gaming sesion activate my nvidia card automaticaly and don't have this anoying screen tearing and other problems. I don't know i have problems with bumblebee instalation and get black screen after installed xedgers graphic driver and seems don't work bumblebee and i don't know how to configure read a lot of tutorials. I don't want have screen tearing and other problems just that. I want my Ubuntu works very well with hardware. How can make settings on BIOS, how to install ubuntu on UEFI or Legacy? And give me a partitions tabel what are good for my specs. Please help i want this OS on my laptop, i'm tired to use Windows, i fell unconfortable with it, i want Ubuntu or another user friendly linux distribution which work very good on my laptop.

---

### Post by trubludmn on 2015-05-17
Hello,

Regarding the Lenovo BIOS settings: I have a ThinkPad T420 and from the start with Ubuntu 14.04 LTS I changed the ThinkPad's BIOS settings to "UEFI only" and kept the default "Nvidia Optimus" setting. While Ubuntu defaulted to Intel HD Graphics upon first installation and startup, I quickly switched to using the proprietary Nvidia driver and then finally the X.Org Edgers Nvidia driver.

I have had no problems whatsoever with the Nvidia driver (I have a Quadro NVS Mobile 4200M) and use it extensively for games (full-screen Flash, Steam) and video (YouTube, VLC) with excellent performance and it has never crashed or taken down my system.

But yes, "UEFI only" is probably the best choice for the Lenovo BIOS settings.

For partitioning, I was overly generous: 500 MB for EFI System partition, 1 GB for boot partition, 16 GB swap, etc.

Hope this helps.

---

### Post by grahammechanical on 2015-05-17
I see 3 questions here

1) > I don't know what settings have in BIOS on UEFI or Legacy support,
2)> what partitions make for best results.
3)> i don't want anymore screen tearing

Answering more than one question in the same thread causes confusion. Please create a new thread for each question.

Question #1

When a machine comes with Windows 8.1 pre-installed then Windows 8.1 will be installed in EFI mode and we must install Ubuntu in EFI mode as well and not BIOS/Legacy mode.

[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

Question #2

Stick with the partitions that you now have until you become more experienced, especially with resizing and moving partitions. The number and use of partitions is a personal decision. There is no fixed rule.

Questions #3

You will not get automatic switching with Optimus technology on Linux because even the latest Nvidia drivers do not give Linux users automatic switching. If you are going to use a Nvidia driver then you should use the latest nvidia driver from Ubuntu Additional Drivers utility. It is an experiment to install video drivers from the manufacturer's web site or from a PPA. We need to know how to purge the driver and go back to the beginning. We need to become familiar with Recovery Mode.

If we install the Nvidia driver then we will get nvidia prime which we use to manually switch video adapters. Or we can install Prime Indicator which will also do the same thing.

[http://www.webupd8.org/2014/01/prime-indicator-lets-you-quickly-switch.html](http://www.webupd8.org/2014/01/prime-indicator-lets-you-quickly-switch.html)

This is as good as it gets on Linux with Optimus Technolgy. It is only by buying machines with Ubuntu pre-installed that we avoid hardware problems like this. But we do not always have the choice to buy a Ubuntu machine.

Regards.

---

### Post by oldfred on 2015-05-17
I suggest 300 to 500MB for efi partition. No separate /boot partition. Swap at 2GB unless you really want to hibernate then it must be equal to RAM in GiB or about 10% more than GB. Or if editing videos you may need more swap. My 4GB RAM Desktop never used swap with whatever is my normal use.
System or / (root) should be 20 or 25GB.
Then rest of drive can be /home or data partition(s), depending on what you want.

Buried in this long thread, this user mentions he installed to Lenovo Idepad         Y50-70. He may have more info somewhere on his site.
[http://www.dedoimedo.com/computers/windows-10-alt-os-lockout.html](http://www.dedoimedo.com/computers/windows-10-alt-os-lockout.html)
And he has posted install instructions in general.
       [http://www.dedoimedo.com/computers/dual-boot-windows-8-ubuntu.html](http://www.dedoimedo.com/computers/dual-boot-windows-8-ubuntu.html)

---

### Post by danutz332 on 2015-05-17
Thank you all for replies, i installed Ubuntu on UEFI mode but in additional drivers says "No additional drivers available.", i search for nvidia drivers. I made partitions: 20 Gb root partition, 500 Mb efi partition, 8 Gb swap partition and the rest of memory in home partition. I'm wait for some instruction for install nvidia drivers becouse in additional drivers is empty. Seriosly i don't want screen tearing anymore on desktop, video or in game. Thanks all for your support.

EDIT: I think my Ubuntu don't recognize my dedicated card and don't show up any drivers in Additional drivers.

---

### Post by danutz332 on 2015-05-18
Yeah, I don't figured out for resolve my problems with drivers and other things in this OS. Or nvidia drivers is crap on this laptop or laptop itself is piece of crap and is not able to run Ubuntu. Support for this OS is very poor, i have a desktop with AMD graphics card and don't have drivers from manufacturer for Linux but i find some tutorials and i try to install and failing everytime, i wan't to run Ubuntu exactly run Windows on every PC/Laptop but i have a poor experience with this OS. With intel hd graphics on Ubuntu i don't have problems but i not able to play games with integrate graphic card like i run with dedicate Nvidia card, i want to run like in windows i was able to play GTA V on Windows, here on Ubuntu play CS:GO with screen tearing and the rest of troubles. If Ubuntu or someone make a distribution and in installing process put some codes for select all manufacture of all comonents (I have i5-4210U with Nvidia 840m 2Gb and automaticaly search for best drivers for my Laptop and install it, no more headache or stress for find drivers) I try to make Ubuntu work on my PC/Laptop with no chances of succes. In future when i have some money i want to build a PC special for Ubuntu to run smooth and stable on it, i want to play games like in Windows. I don't have a good experience with Ubuntu, I don't know, i feel so bad i can't run this OS like Windows on desktop or in game. I like Ubuntu but i can't do nothing to make run better.

---

### Post by mc4man on 2015-05-18
If you need nvidia to play your games then what I told you before, will repeat once with some add. - 
Use a desktop computer
Use Windows, far better for games on any system or card.

Install nvidia drivers & use the default nvidia-prime. When playing games switch to nvidia in nvidia-settings, for everything else use Intel. This requires a log out/in to switch back & forth from nvidia & Intel

Get rid of nvidia-prime & install bumblebee, run your games thru it (primusrun). I tested bumblebee here with some Steam based games, worked ok.

Or find yourself some linux distro with no compositing at all. Then there is a possibly of nvidia with vsync (maybe

---

