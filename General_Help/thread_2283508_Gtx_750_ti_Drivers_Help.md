---
title: "Gtx 750 ti Drivers Help"
date: 2015-06-22
forum: General Help
---

### Post by Davis_Shriver on 2015-06-22
I've downloaded the nvidia display drivers for my gtx 750 ti, and I'd like to know what to do next with the .run file. I am brand new to linux and I don't know what to do now. I have the drivers downloaded but how do I install them?

---

### Post by papibe on 2015-06-22
Hi Davis_Shriver.

Don't install it just yet.

First, try the driver that is packaged and supported by Ubuntu. Open 'Additional Drivers' and install the suggested driver there.

You may need to restart, to take 100% effect.

Hope it helps. Let us know how it goes.
Regards.

---

### Post by Davis_Shriver on 2015-06-22
When I look for additional drivers nothing happens. I just want to install my cards drivers, but I haven't got a clue how.

---

### Post by Davis_Shriver on 2015-06-22
It just says no additional drivers.

---

### Post by papibe on 2015-06-22
Could you open a terminal, run this command, and post back the output (you can copy/paste the text)?
```
lspci -nnk | grep -iA2 vga
```
Regards.

---

### Post by oldfred on 2015-06-22
The .run file directly from nVidia is the last method. You in effect have to reinstall it with every kernel update. If you can use the drivers from Ubuntu that is first choice, but you can get the very  newest from ppa. A ppa is another repository (be sure it is one you trust) and it installs as part of updates. System just installs the very newest available and ppa will have newer version.

Post command from papibe so we know your system is seeing the nVidia card.

---

### Post by Davis_Shriver on 2015-06-22
fragger@fragger-desktop:~$ lspci -nnk | grep -iA2 vga
01:00.0 VGA compatible controller [0300]: NVIDIA Corporation GM107 [GeForce GTX 750 Ti] [10de:1380] (rev a2)
    Subsystem: ASUSTeK Computer Inc. Device [1043:84bb]
01:00.1 Audio device [0403]: NVIDIA Corporation Device [10de:0fbc] (rev a1)
fragger@fragger-desktop:~$ 

This is what my about this computer says for graphics: "VESA: GM107 Board - 20100050"

---

### Post by oldfred on 2015-06-22
What version of Ubuntu. 
The newest should partially work with the open source driver, where older versions did not at all.

 Maxwell 750 - kernel 3.15 or newer required
[http://ubuntuforums.org/showthread.php?t=2214805](http://ubuntuforums.org/showthread.php?t=2214805)
[http://ubuntuforums.org/showthread.php?t=2265505](http://ubuntuforums.org/showthread.php?t=2265505)
Usually better to use PPA.
[http://ubuntuforums.org/showthread.php?t=2252908](http://ubuntuforums.org/showthread.php?t=2252908)
[http://ubuntuforums.org/showthread.php?t=2257506](http://ubuntuforums.org/showthread.php?t=2257506)
[http://ubuntuforums.org/showthread.php?t=2261714](http://ubuntuforums.org/showthread.php?t=2261714)
[http://www.phoronix.com/scan.php?page=article&item=evga_geforce_gtx750&num=1](http://www.phoronix.com/scan.php?page=article&item=evga_geforce_gtx750&num=1)
[http://www.phoronix.com/scan.php?page=article&item=nvidia_maxwell_750linux&num=1](http://www.phoronix.com/scan.php?page=article&item=nvidia_maxwell_750linux&num=1)

---

### Post by Davis_Shriver on 2015-06-22
Ubuntu 14.0.4 64 bit.

---

### Post by grahammechanical on 2015-06-22
If Additional Drivers is not showing any proprietary video drivers it could mean that the 14.04 repositories to not have an Nvidia driver for that video card. The Nvidia web site shows Linux drivers for that card as 346, 349, 352. But nothing lower than 346. And if the 346 driver is not in the 14.04 repository then that would be a problem.

[http://www.geforce.co.uk/drivers](http://www.geforce.co.uk/drivers)

Are you using 14.04.2? In July Ubuntu 14.03.3 will be released and that should later Nvidia drivers.

Regards.

---

### Post by Davis_Shriver on 2015-06-22
I think I'll just wipe it and get windows. Thanks for your help, but ubuntu has had way to many issues.

---

### Post by Yellow Pasque on 2015-06-22
Please mark the thread solved if you don't care about it anymore. BTW, this is what I'd recommend to install the nvidia drivers on 14.04: [https://launchpad.net/~mamarley/+archive/ubuntu/nvidia](https://launchpad.net/~mamarley/+archive/ubuntu/nvidia)
Noobs should not be messing around with Nvidia's or AMD's .run files downloaded directly from their sites.

---

### Post by ka55o5 on 2015-06-22
> **Temüjin said:**
> Noobs should not be messing around with Nvidia's or AMD's .run files downloaded directly from their sites.
Yes, thank you!.. It's a trap that people -often- fall into. xD

The documentation *and* the available drivers are very clear, btw. I remember years ago, when there were **NO** drivers available (whatsoever!), I think it might've been -even- before **nvidia-settings** (which, incidentally, is a very easy way to solve any issues; mind you, it's an *alternate* way), it took me 20-30 minutes maximum (being entirely clueless about *nix systems) to get everything working.

^^ Why I love Ubuntu. The community, documentation, easy of use (the ultra-smart installer, auto-partitioning and so on). List would be huge! :DD

---

