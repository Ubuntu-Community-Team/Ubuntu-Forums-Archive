---
title: "PC shuts down randomly and then restarts"
date: 2021-05-03
forum: General Help
---

### Post by arggeo on 2021-05-03
Hello Ubuntu Community,
I am a completely new Ubuntu user and although I already loved the OS I am experiencing a really disturbing problem to the point I cannot work on the computer at all.

The problem: Computer shuts down (crushes?) unexpectedly (no matter what I am doing at the time ex: browsing the internet, coding, watching videos etc) and then turns on again (like restarting but with a pause). Some time it works normally for 1 or 2 days and other times it may happen 2-5 times in a single day.

I have built a brand new desktop computer (every part is new). I have been struggling to find the cause however I've reached to a point where my knowledge can only get me so far when it comes to troubleshooting.
All drivers and any other software are up to date.

PC: 
Keyboard/Mouse: Logitech MX Keys / MX Master 3
GPU: NVIDIA GeForce GT 1030
MB: ASUS Rog Strix X570-F Gaming
SSD: Kingston A200 1TB NVMe
CPU: Ryzen 7 3800XT
RAM: G.Skill Ripjaws V 32GB DDR4 3600MHz
PSU: Corsair TX750

Is there any advanced user who can detect the problem and suggest a fix?
My syslog [https://we.tl/t-MPhhZX7xxR](https://we.tl/t-MPhhZX7xxR).

Thanks in advance.

---

### Post by grahammechanical on 2021-05-03
Is it the operating system that shuts down and the reboots? Or, is it the hardware that switches off and then re-powers back on?

If it is the hardware, then double check the power connections from the mains outlet into the power supply. My motherboard is not as new as your motherboard but if I use the On/Off switch to power off the computer power will continue to be supplied from the Power Supply Unit as long as the mains lead is switched on. The motherboard shows this to be the case by keeping an LED on the motherboard illuminated. I also have an On/Off switch on the back of the PSU that completely shuts off the power to the motherboard.

Is the PSU fan working? If not then an automatic shutdown function may be triggered. I am just throwing in some guesses. Please determine if it is a hardware power supply issue. If it is the OS that is shutting down then check if the Memory modules are fully seated. Likewise check if the CPU is over heating. Is the CPU fan working? The Motherboard fans working?

Regards

---

### Post by arggeo on 2021-05-03
Thanks for replying mate.

Hardware is fine, all fans are working properly (PSU, CPU etc) and temperatures are fine too. I have installed Vitals and it shows 40 degrees celcius on average on all components. I have concluded that the problem has to do with the software as I installed Windows 10 for a few days (to eliminate the possibility of having to deal with hardware issues) and everything worked normally. Not a single shut down, no freezes, no problems at all. I have also cut the power and kept the power button pushed for a minute to discharge the hardware in case there was any electricity left "running".

---

### Post by tea for one on 2021-05-03
> **arggeo said:**
> SSD: Kingston A200 1TB NVMe

Some Kingston SSD NVME drives need a little tweak in grub - added in blue below:-

```
GRUB_DEFAULT=0
GRUB_TIMEOUT_STYLE=menu
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
#GRUB_DISTRIBUTOR="Ubuntu 20.04"
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash [COLOR="#0000FF"]nvme_core.default_ps_max_latency_us=0[/COLOR]"
GRUB_CMDLINE_LINUX=""
```

Don't forget to update grub after editing:-
```
sudo update-grub
```

[https://tekbyte.net/2020/fixing-nvme-ssd-problems-on-linux/](https://tekbyte.net/2020/fixing-nvme-ssd-problems-on-linux/)

Fingers crossed

---

### Post by arggeo on 2021-05-03
> **tea for one said:**
> Some Kingston SSD NVME drives need a little tweak in grub - added in blue below:-

```
GRUB_DEFAULT=0
GRUB_TIMEOUT_STYLE=menu
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
#GRUB_DISTRIBUTOR="Ubuntu 20.04"
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash [COLOR=#0000FF]nvme_core.default_ps_max_latency_us=0[/COLOR]"
GRUB_CMDLINE_LINUX=""
```

Don't forget to update grub after editing:-
```
sudo update-grub
```

[https://tekbyte.net/2020/fixing-nvme-ssd-problems-on-linux/](https://tekbyte.net/2020/fixing-nvme-ssd-problems-on-linux/)

Fingers crossed

Thank you very much for your answer mate. It seems I am facing the very same issue. I followed the instructions given in the article, verified that changes are applied and I hope it is fixed. Will be sure in 2-3 days time. While you inserted the code in "GRUB_CMDLINE_LINUX_DEFAULT", the article suggests that it should be included in "GRUB_CMDLINE_LINUX". Am I getting something wrong?

Regards

---

### Post by tea for one on 2021-05-04
```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash nvme_core.default_ps_max_latency_us=0" [COLOR="#0000FF"]normal boot[/COLOR]
GRUB_CMDLINE_LINUX="" [COLOR="#0000FF"]recovery boot[/COLOR]
```
You do not want grub parameters in recovery boot because it may be the parameters themselves which cause difficulties.
> GRUB_CMDLINE_LINUX
    Entries on this line are added to the end of the 'linux' command line (GRUB legacy's "kernel" line) for both normal and recovery modes. It is used to pass options to the kernel. 

GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"

    This line imports any entries to the end of the 'linux' line (GRUB legacy's "kernel" line). The entries are appended to the end of the normal mode only.
        To view a black screen with boot processes displayed in text, remove "quiet splash". To see the grub splash image plus a condensed text output, use "splash". 

The above quote is from [https://help.ubuntu.com/community/Grub2/Setup](https://help.ubuntu.com/community/Grub2/Setup)

---

### Post by ActionParsnip on 2021-05-04
Check for blown capacitors on the motherboard. Also test RAM health as a good first step

---

### Post by HermanAB on 2021-05-04
Random restarts are almost always due to bad power quality.  One major advantage of a laptop computer is that it has a built-in uninterruptable power supply.

---

### Post by dragonfly41 on 2021-05-04
If you have built this system from new parts (as you write - [COLOR=#000000]RAM: G.Skill Ripjaws V 32GB DDR4 3600MHz[/COLOR]) then one possible (but unlikely) cause is that RAM is not seated firmly.
Try cleaning the edges with a rubber then reseating.
Have you run Memtest?

---

### Post by arggeo on 2021-05-05
> **tea for one said:**
> ```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash nvme_core.default_ps_max_latency_us=0" [COLOR=#0000FF]normal boot[/COLOR]
GRUB_CMDLINE_LINUX="" [COLOR=#0000FF]recovery boot[/COLOR]
```
You do not want grub parameters in recovery boot because it may be the parameters themselves which cause difficulties.


The above quote is from [https://help.ubuntu.com/community/Grub2/Setup](https://help.ubuntu.com/community/Grub2/Setup)

Thank you very much for explaining. I will have a look in the grub setup article.

---

### Post by arggeo on 2021-05-05
> **HermanAB said:**
> Random restarts are almost always due to bad power quality.  One major advantage of a laptop computer is that it has a built-in uninterruptable power supply.

If this was the problem then shouldn't I face the problem while running windows too? I tried and windows OS is running with no such problem.

---

### Post by arggeo on 2021-05-05
Update: Not sure if the problem is fixed yet however after applying what "**tea for one" **suggested I have noticed that in general Ubuntu is running a bit smoother. Is this a valid statement?

---

### Post by arggeo on 2021-05-05
> **tea for one said:**
> Some Kingston SSD NVME drives need a little tweak in grub - added in blue below:-

```
GRUB_DEFAULT=0
GRUB_TIMEOUT_STYLE=menu
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
#GRUB_DISTRIBUTOR="Ubuntu 20.04"
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash [COLOR=#0000FF]nvme_core.default_ps_max_latency_us=0[/COLOR]"
GRUB_CMDLINE_LINUX=""
```

Don't forget to update grub after editing:-
```
sudo update-grub
```

[https://tekbyte.net/2020/fixing-nvme-ssd-problems-on-linux/](https://tekbyte.net/2020/fixing-nvme-ssd-problems-on-linux/)

Fingers crossed

Unfortunately I still experience the same issue. I got shut downs again.

---

### Post by exfulgor on 2021-11-04
I have the exact same problem:


Ryzen 7 3700x
ASUS ROG STRIX X570-F GAMING
Corsair Vengeance LPX DDR4 3600MHz CL18 32GB (2x16GB)
Samsung SSD 970 EVO Plus 500GB
Nvidia RTX 3080ti FE


I've had this PC for a year. With Win10 it works perfectly and has never given me any problems. Two days ago I decided to install Ubuntu. Sometimes it works for a minute, sometimes for an hour. Then everything turns off instantly (even the LEDs on the whole motherboard) and restarts. I had already tried 6 months ago and the only hardware difference was the Cerberus 1050ti OC. But he had the same problem.
Were you able to solve the problem?

---

### Post by HermanAB on 2021-11-05
If you boot off the install media and let it run (without installing again!), what happens? You could also try a completely different distribution such as Fedora or Arch Linux. Each distro tests with different machines and nobody tests with every machine ever manufactured…

---

### Post by exfulgor on 2021-11-07
I forgot to mention that the problem is also with the LiveCD, before installation. I was deciding how to partition and suddenly the pc shut down the same way.
I haven't tried other distributions.
The only constant I see is NVidia HWs. Problems with the drivers?

---

### Post by ActionParsnip on 2021-11-07
Test RAM health and check for blown caps

---

### Post by exfulgor on 2021-11-07
I tested the memory in every way. No problem. Win10 has been working properly for over a year.

---

### Post by exfulgor on 2021-11-25
As for my case, it seems that I have found the solution ...
Ubuntu, Fedora, Linux Mint all had the same random reboot problem.
I solved it like this:
1) Deactivated the D.O.C.P configuration for my memory at 3600 and set to "auto".
2) Updated ROG X570-f firmware to the latest version (the firmware was three months old)
3) Restored the default configuration of the Mobo
4) Reconfigured D.O.C.P to restore the memory to 3600


Ubuntu now works fine ... and Win 10, which seemed to work fine, now feels more responsive.

---

