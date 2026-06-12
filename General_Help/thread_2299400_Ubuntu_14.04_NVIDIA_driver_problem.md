---
title: "Ubuntu 14.04 NVIDIA driver problem"
date: 2015-10-18
forum: General Help
---

### Post by Tsvetanov on 2015-10-18
[CENTER]
[/CENTER]
Hello. I'm really new to Linux, sorry for lame questions.

Firstly I used the **Nouveau** driver but Ubuntu hanged/freezed almost every time I started any application - mostly System Preferences and Firefox, but other apps too.

Then I changed the driver to **NVIDIA legacy binary driver** **304.128 **(the latest one for GeForce 7025) and now Ubuntu doesn't crash at all, but certain areas of the display became blurry and windows movement, minimizing, maximizing, scrolling through pages etc. is not smooth at all - it's like a slow motion or something like that.

This is the hardware:[U]

System[/U]:
Ubuntu 14.04
GNOME 3.8.4 (Ubuntu 2015-04-02)
Kernel 3.19.0-30-generic (#34~14.04.1-Ubuntu SMP Fri Oct 2 22:09:39 UTC 2015)
GCC Version: 4.8 (x86_64-linux-gnu)
Xorg version: 1.17.1 (13 May 2015  04:35:05AM)[U]

CPU[/U]:
Vendor: AuthenticAMD
CPUs: 2
Model name: AMD Athlon(tm) II X2 240 Processor
Frequency: 1600.000 MHz
L2 cache: 1024 KB
Bogomips: 5625.55
Numbering: family(16) model(6) stepping(2)
Flags: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt pdpe1gb rdtscp lm 3dnowext 3dnow constant_tsc rep_good nopl nonstop_tsc extd_apicid pni monitor cx16 popcnt lahf_lm cmp_legacy svm extapic cr8_legacy abm sse4a misalignsse 3dnowprefetch osvw ibs skinit wdt hw_pstate npt lbrv svm_lock nrip_save vmmcall[U]

Memory[/U]:
Memory total: 2756 MiB, free: 72%
Swap total: 7284 MiB, free: 100%[U]

HDD[/U]:
SCSI device: scsi2
Vendor: ATA
Model: Hitachi HDT72106[U]

Motherboard[/U]:
NVIDIA nForce 630a[U]

Graphic card[/U]:
NVIDIA GeForce 7025[U]

Partitions of HDD[/U]:
1. Ubuntu partition (/dev/sda6): 61gb (used 6.27gb)
2. Ubuntu swap (/dev/sda5): 7.11gb
3. NTFS partition (/dev/sda2) (no Windows): 527gb


Is there any solution for this problem?

Thanks in advance!

---

### Post by Tsvetanov on 2015-10-18
.

---

### Post by grahammechanical on 2015-10-18
I am not clear what the problem is.

Each version of Ubuntu comes with the latest but stable proprietary video drivers. The newer proprietary video drivers drop support for older video adapters. This is the situation in my case. I run the very latest Ubuntu (15.10) with Linux kernel 4.2 but I cannot run the latest Nvidia drivers because they do not support my Nvidia GT220. Additional Drivers offers me Nvidia legacy 304 and 340. But I find that the X.org driver Nouveau to be sufficent.

Your Geforce 7025 is not supported by the latest Nvidia drivers that come with Ubuntu 14.04. This is why Additional Drivers is offering you Nvidia legacy drivers 173 and 804. They support your Geforce 7025

[http://www.geforce.co.uk/drivers/results/51453](http://www.geforce.co.uk/drivers/results/51453)

Regards.

---

### Post by mörgæs on 2015-10-18
Hi, welcome to the fora.

I suggest a fresh install of L/Xubuntu using the closed-source drivers offered. An Nvidia 7025 is a little to weak for Ubuntu.

---

### Post by night_sky2 on 2015-10-18
> **mörgæs said:**
> I suggest a fresh install of L/Xubuntu using the closed-source drivers offered. An Nvidia 7025 is a little to weak for Ubuntu.
That is my take as well.

Based on the computer's specs, the OP would benefit from using a lighter desktop environment such as Xfce (Xubuntu), MATE (Ubuntu MATE) or LXDE (Lubuntu) that is less graphically demanding. This alone should make a difference. Aftert that he can install the 340 legacy Nvidia driver which should support his graphic card perfectly well, better than the Nouveau open source driver.

---

### Post by Tsvetanov on 2015-10-18
Thank you very much for replies!

> **grahammechanical said:**
> I am not clear what the problem is.

My poor english, sorry about that. I edited my first post and I hope it's ok now ...

> **mörgæs said:**
> Hi, welcome to the fora.

I suggest a fresh install of L/Xubuntu using the closed-source drivers  offered. An Nvidia 7025 is a little to weak for Ubuntu.
> **night_sky2 said:**
> That is my take as well.

Based on the computer's specs, the OP would benefit from using a lighter  desktop environment such as Xfce (Xubuntu), MATE (Ubuntu MATE) or LXDE  (Lubuntu) that is less graphically demanding. This alone should make a  difference. Aftert that he can install the 340 legacy Nvidia driver  which should support his graphic card perfectly well, better than the  Nouveau open source driver.
I'll definitely consider that. Just watched some video previews of those 3 distros, and I really like MATE. Do you really think MATE should be good for my hardware and I won't experience those hangs/crashes, or blurry fonts & "broken" movement and scrolling anymore? 

**night_sky2**, in my Ubuntu the only drivers I get in the "Additional drivers" app are the NVIDIA legacy v304.128 and Nouveau. If I install MATE, for example, do you think I'll be able to install the newer 340 version of NVIDIA legacy driver?

Thanks!

---

### Post by night_sky2 on 2015-10-18
> **Tsvetanov said:**
> Thank you very much for replies!I'll definitely consider that. Just watched some video previews of those 3 distros, and I really like MATE. Do you really think MATE should be good for my hardware and I won't experience those hangs/crashes, or blurry fonts & "broken" movement and scrolling anymore?
I can't guarantee it but it's very possible that it will. MATE is a fork of Gnome 2, it's a 2-D desktop environment and lower on ressources than Unity (Ubuntu).

So it is much easier on older hardware.

> **Tsvetanov said:**
> **night_sky2**, in my Ubuntu the only drivers I get in the "Additional drivers" app are the NVIDIA legacy v304.128 and Nouveau. If I install MATE, for example, do you think I'll be able to install the newer 340 version of NVIDIA legacy driver?
If the 340 binary driver doesn't show up in ''Additional Drivers'' it's probably because it doesn't support your specific Nvidia graphic card.
I persosonnaly have a Nvidia Geforce 8400 GS [Rev 2] and the 340 binary driver is the recommended one. But it maybe not the case for you.

Still, the 304 legacy driver in a MATE environment should do the trick IMO. ;)

---

### Post by Tsvetanov on 2015-10-23
Still haven't tried Lubuntu or Xubuntu, but tried Ubuntu MATE 15.04, OpenSUSE 13.2 KDE, OpenSUSE 13.2 GNOME and OpenSUSE 13.2 Xfce.

OpenSUSE 13.2 KDE, GNOME and Xfce:
The system crashed every time after booting. The output most of the times was something really similar to this:

[IMG]http://cdn.overclock.net/d/da/600x450px-LL-da083e37_Photo0778.jpeg[/IMG]

.. or, in some cases, the system just freezed and didn't respond at all.
Couldn't manage to change the graphic driver to NVIDIA legacy because the system crashed too fast after booting.

Ubuntu MATE 14.04:
It didn't crash with the Nouveau driver, but when I enabled Compiz in "MATE Tweak" window the system started freezing regularly. Somehow managed to change the driver to NVIDIA legacy 304 and the freezing was gone, but fonts became blurry and actions and effects looked like a slow motion.
When I exit the Compiz mode and use the Nouveau driver the system didn't crash and performed smoothly, but in this case the GUI is really poor.

I don't quite fancy the GUI of Lubuntu or Xubuntu neither.

Now I'm back to Ubuntu 14.04. It's the same as before - crashing with the Nouveau driver - I get the same screen from the picture above, or the system freezes; with NVIDIA legacy it doesn't crash, but fonts are blurry and all actions and effects look like a slow motion.

By the way, Windows 10 looked blurry too. Deleted it couple of weeks ago. As far as I remember, Windows 8.1 was totally ok.... but I would like to use Linux instead.

So, Instead of dealing with user interface I don't quite like (if I manage to run them), I prefer to buy some decent graphic card. Is there a chance that I will run, for example, OpenSUSE LEAP 42.1 with KDE environment or the future version of Unity, if I replace the current graphic card with a decent one (not too expensive, but decent), but still use the other hardware of this PC? If yes, please, can you recommend something compatible with those distros?

Regards!

---

