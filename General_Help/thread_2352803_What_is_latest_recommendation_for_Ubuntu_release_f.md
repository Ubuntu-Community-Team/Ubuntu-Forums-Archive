---
title: "What is latest recommendation for Ubuntu release for legacy AMD graphics?"
date: 2017-02-15
forum: General Help
---

### Post by psadams on 2017-02-15
Hi,

I have a HP ProBook 4530s laptop with an AMD Radeon 6490M graphics card. This is my 10yo son's & I want to install Ubuntu, primarily for gaming using Steam. I initially installed Ubuntu Mate 16.10, but had a lot of issues with the AMD drivers.

I was wondering what the current (2017) recommendation is for the best Ubuntu release to use for legacy AMD cards? Is 14.04 LTS still recommended as the best release, together with downloading AMD drivers directly from their website?
[https://support.amd.com/en-us/download/linux](https://support.amd.com/en-us/download/linux)

I would much prefer to run a later release, if possible. I have read that the 4.9 & 4.10 kernels have improved AMD open source drivers, but is this only for later video cards? I was considering installing 16.10 and upgrading to a 4.9 or 4.10 kernel. Good or bad idea?

Thanks in advance! Any help/advice is much appreciated.

Paul

---

### Post by QIII on 2017-02-15
Given that card and the desire to game, 14.04.1 or 14.04 would be suggested.  The hardware stacks for 14.04.2 - 14.04.4 are no longer supported.  14.04.5 will not use fglrx.

After that, the fglrx proprietary driver is unavailable or will fail.

That GPU is not supported by the new open source AMDGPU driver and will not be in the future because of it's technological shortcomings.

Although the open source Radeon driver is available for later Ubuntu releases, its performance is not really suitable for gaming.

---

### Post by mastablasta on 2017-02-16
14.04 is supported for 2 more years. 

on the other hand win 10 will support it well for gaming, but ofcoruse it will cost (money and maybe privacy, unless you can get the enteprise edition which has 10 years support and ability to turn off the snooping.).

---

### Post by psadams on 2017-02-21
@QIII Thank you so much! Since the games my son plays are mostly older, less graphically intensive (i.e. Age of Empires 2 HD, Portal, Minecraft etc.) I've gone with Ubuntu MATE 16.04.2. I'm very hesitant to go back to 14.04 and would much rather go with a more modern distro with more up-to-date packages and kernel. Very happy with the performance of Ubuntu MATE so far. Using PlayonLinux with Wine 2.1 and running Steam too. His HP laptop has a 3rd gen Intel i5 CPU, 8GB RAM and a Samsung 850 EVO 250GB SSD.

@mastablasta Thanks! I was running Windows 10 on this laptop before, but privacy and security were big concerns for me. Purely from a gaming PoV it is better than Linux, but I rate privacy/security as the highest priority when it comes to my kids' computers.

Some background: I ran Windows for many years (3.11 -> Vista), but got curious about Linux and tried Ubuntu 5.04, the second version ever released. I ordered the official CDs/DVDs from Canonical for the first several versions. Hence why I joined these forums way back in 2006. Then when Vista came out I was very frustrated by endless stability and performance issues so switched to Ubuntu as my main OS.  I used Ubuntu exclusively through to 8.04. Then in late 2008 I bought a MacBook Pro. I still used Ubuntu on and off on home PCs, but far less frequently. I now have various versions of Ubuntu installed on a few older computers, mostly for the kids use and for me to play around with.

---

### Post by mastablasta on 2017-02-22
> **psadams said:**
> 
@mastablasta Thanks! I was running Windows 10 on this laptop before, but privacy and security were big concerns for me. Purely from a gaming PoV it is better than Linux, but I rate privacy/security as the highest priority when it comes to my kids' computers.
.

shutup10 3rd party porgram turns off reporting. enteprise edition has the option to turn it off. not sure if this is even available to us consumers. it does have 10 years support (the LTS version).

AMD opensource drivers will get some major update in 17.04 and as some say it will be ported back to 16.04 as well. probably to 16.04.3. checking the tests it looks liek the drivers will then be about 5-10% weaker. which is good enough anyway for older games. i would imagine the issue would show more with latest games. 

minecraft is more CPU intensife than it is graphically. portal has "old" engine... i have E-450 AMD which has 6320 series chip  (lower end) it can run most games up to year 2005. hmmm havent' tried minecraft on it but i think it would run descently. in any case with your machine it shouldn't be that much of a problem.

---

