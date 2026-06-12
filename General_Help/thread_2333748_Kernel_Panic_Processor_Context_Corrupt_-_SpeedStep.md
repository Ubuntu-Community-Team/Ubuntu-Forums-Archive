---
title: "Kernel Panic: Processor Context Corrupt - SpeedStep problem?"
date: 2016-08-12
forum: General Help
---

### Post by catscratch2 on 2016-08-12
Hi guys.

I got a similar problem like here: [https://ubuntuforums.org/showthread.php?t=2182192&highlight=processor+context+corrupt](https://ubuntuforums.org/showthread.php?t=2182192&highlight=processor+context+corrupt)

First of all. Thanks for reading and trying to help. Second, I searched the threads but nothings really helped.

On booting from live usb stick (or DVD) I got a message on boot which ends in a system halt and reboot of ubuntu 14.04.

Message: Kernel Panic: Processor context corrupt. And some more messages. I added a screenshot.

[ATTACH=CONFIG]270669[/ATTACH]

Anyway. My system:
Intel Core i5 750 (4x 2,67 GHz)
Asus P7P55D
4x2 GB Corsair RAM
SSD HDD

I noticed that the problem comes from Intel SpeedStep activated. I overclocked my CPU to 3.2 GHz. I'm running 166 MHz clock with 1328 RAM clock which comes to about 3.2 GHz. I can overclock the CPU to 4.2 GHz without any problems. It's still running stable with Windows 10!

I'm running the overclocked CPU for month now and it's super stable on Windows 10. No freezes, no bluescreens. 

Also RAM check was fine. Prime95 too. CPU can handle stress on 100% load. Cooling is also ok. I don't use the boxed one. I got a powerful cooler. CPU runs about 60 degress on stress and 35 on idle.

So. But when trying to boot ubuntu I got the kernel panic message above.

When deactivating Intel SpeedStep, Ubuntu is booting fine. But I really want SpeedStep to lower power consumption when not needed.

So my question is, what can I do and what is the problem here? For me it seems like a linux kernel problem not like a hardware problem. I mean, hardware is still running stable on 4.2 GHz overclocked. Is it a known problem with SpeedStep?

Can someone give me a hint on how to get ubuntu running with Intel SpeedStep activated?

Thanks a lot!

---

### Post by mörgæs on 2016-08-12
Hi, welcome to the fora.
Have you tried a live boot of 16.04.1?

---

### Post by catscratch2 on 2016-08-13
Thanks for replay. Unfortunately the result is the same. Only the error messages changes...I think. ;-)

I took two screenshots:
[ATTACH=CONFIG]270674[/ATTACH][ATTACH=CONFIG]270673[/ATTACH]

Then after some time the screen goes offline and the pc reboots. Again, without SpeedStep, everything works perfect.

---

