---
title: "Ubuntu and Acer Aspire One — running hot and continuous fan"
date: 2013-09-19
forum: General Help
---

### Post by CeejRab on 2013-09-19
Hello all,

Quick request for advice... 

I have a Acer Aspire One AOA150 netbook, and I've tried running quite area distros on I to improve battery performance and attempt to reduce lag and overheating. I sarted out with Ubuntu 12.04LTS and that's what I'm back to. 

I have a couple concerns/curiosities:

1. The fan seems to be always running, I don't believe it ever stops. Is this bad / can it be helped?
2. The laptop runs hot, is this bad for it? I've tried even very light distros like Lubuntu or even puppy Linux but there's not much diference, is it just my laptop's characteristic?
3. I'm getting about an hour of battery life with Ubuntu where I got nearly 30-50% more with windows XP (I don't want to go back!). Is there a way to increase battery life in Ubuntu? 

Thanks in advance, all the best.

---

### Post by carl4926 on 2013-09-20
> **CeejRab said:**
> Hello all,

Quick request for advice... 

I have a Acer Aspire One AOA150 netbook, and I've tried running quite area distros on I to improve battery performance and attempt to reduce lag and overheating. I started out with Ubuntu 12.04LTS and that's what I'm back to. 

I have a couple concerns/curiosities:

1. The fan seems to be always running, I don't believe it ever stops. Is this bad / can it be helped?
2. The laptop runs hot, is this bad for it? I've tried even very light distros like Lubuntu or even puppy Linux but there's not much difference, is it just my laptop's characteristic?
3. I'm getting about an hour of battery life with Ubuntu where I got nearly 30-50% more with windows XP (I don't want to go back!). Is there a way to increase battery life in Ubuntu? 

Thanks in advance, all the best.

It does not sound normal or right.
I can only compare with my Asus eeepc which runs silent unless I run multiple apps, then the fan kicks in from time to time.
I have Ubuntu 13.04 on there and Mint 13 Mate. Ubuntu for sure is harder work for the little machine, but it's in no way too much or making it hot.
Battery will go for 3hrs+ and I don't do power saving (it annoys me too much).

It might be worth giving 13.10 a run from a USB - it should be sufficient to get a feel and see if the newer kernel is offering improvements.

---

### Post by mastablasta on 2013-09-20
some of new little Acers are hot even in windows7 starter that they have. a bit also depends on the GPU you have. however i read the internet when though abotu buying some that new ones also have this fan issue. at the moment i cna't remember how it is solved (perhaps by contorling fan speed). you might also try tlp for power management. maybe it will help but hard to say.

also make sure the vents are clean (blow it with compressed can of air)

you might also try JoliOS or ArchOne

---

### Post by CeejRab on 2013-09-20
I've tried Lubuntu 13.04 and it ran just the same as Ubuntu 12.04.... As soon as Ubuntu starts to boot, my fan starts and doesn't stop until I shut down... 

Ive considered jolicloud and the smaller netbook distros but I afraid they lack the capability I need. 

Any opinions on SLAX 7? I really like the simplicity and capability as well as the module approach, but I'm not sure how stable to is at a permanent OS.

---

### Post by kjellahl on 2013-09-28
I see the same behavior in my new Acer Aspire V5-551G.

With Ubuntu 13.04 the fan contantly runs at full speed after a short while, and the computer becomes hot.
With Windows 8 this does not happen. The fan runs most of time, but usually at a much lower speed. The computer does not become as hot as with Ubuntu.

It's as if the processor is heavily used all the time in Ubuntu. But "ps -A" does not show any process using a lot of processor time.
The fan control is probably working correctly, but the processor (or possibly some other part of the computer) is working unreasonably hard.

Don't know what causes this behaviour, and what can be done about it, but I'd like to know.

---

### Post by CeejRab on 2013-10-01
thats interesting, i noticed windows 7 runs better than ubuntu on mine but i dont think it can handle windows 8. Have you tried 7 by any chance? if so, did  it seem to run more practically than linux distros?

---

### Post by kjellahl on 2013-10-02
I bought my Acer Aspire V5-551G just a few weeks ago with Windows 8 pre-installed. I have not tried any other Windows version on it.
It was difficult to install Ubuntu in such a way that I can dual-boot with Grub. If you're interested, see [http://ubuntuforums.org/showthread.php?t=2176273](http://ubuntuforums.org/showthread.php?t=2176273).

If your computer is older, and had Windows 7 pre-installed, I don't know if it can run WIndows 8. If it has no UEFI boot mode, only BIOS, I guess Windows 8 would refuse to boot on it.

I'd like to moderate a statement in my previous post in this thread. The fan does not run a full speed all of the time with Ubuntu 13.04. But it does on average run at a higher speed than with Windows 8, and the computer becomes warmer.

The system monitor in Ubuntu reports about 5% processor load when the computer is more or less idle. The system monitor also reports that it uses almost 5% of the processor capacity itself, so it seems other processes use very little. So, where does the heat come from?

---

### Post by martins_abyss on 2013-12-05
Ive just installed Lubuntu 13.10 on my Acer Aspire D255E and notice that the processor is warmer under Lubuntu than under Windows.

I assume that whatever controls the core voltage in Windows for this processor doesnt do it the same in Lubuntu. 

Any idea how to tweak the CPU voltage and CPU speed? (The CPUfreq frontend, which I use on my other Xubuntu laptop doesnt seem to work on Lubuntu)

The Aspire certainly had to work much harder under Win 7 starter just to thrash the hard disk about.  No disk thrashing at all under Lubuntu. So it must be something to do with the CPU speed and voltage control.

 (n.b. The other laptop, a Toshiba Satellite, runs much cooler under Xubuntu than Windows XP)

---

### Post by CeejRab on 2014-02-02
Thread marked as solved, I've sold this laptop and we didn't seem to get much progress here anyway! Thanks to everyone for their ideas and comments.

All the best,

---

### Post by Topsiho on 2014-02-03
Though this thread is closed, and the computer is sold, I want to add, for future reference by readers of this thread, the solution for the fan running constantly, for the Acer netbooks. I apply this solution to my own Acer Aspire One, successfully:

Add to (as root, with sudo):  /etc/modprobe.d/acerhdf.conf the line (or create this file, with the line:), using gedit, or vim in a terminal:

options   acerhdf   kernelmode = 1   fanon = 60000   fanoff = 54000


fanon and fanoff are optional, and determine the temperature at which the fan starts and stops, in this example at 60 degrees and 54 degrees Celsius
After reboot the fan control works.

I have noticed that, without fancontrol, with the fan running full speed constantly, the computer runs much hotter, and am not amazed to read that the battery is exhausted much sooner. Using the fan control, the fan is off most of the time, and only sometimes (reassuringly :) ) runs a while.

Topsiho

---

