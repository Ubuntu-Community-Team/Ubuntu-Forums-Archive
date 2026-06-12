---
title: "Lubuntu 18.04 - Wake up the laptop using USB mouse"
date: 2022-12-18
forum: General Help
---

### Post by miragejet on 2022-12-18
So I can put my laptop into suspend mode and I can wake it up using the Power button, mouse and built-in keyboard don't work.

However I'd like to be able to wake it up using a mouse click, the mouse is connected to an USB Hub and is powered all the time (RGB light is changing).

Everything is enabled but the USB mouse doesn't work.

[IMG]https://i.ibb.co/jVwmF5X/Screenshot-from-2022-12-18-17-04-06.png[/IMG]

---

### Post by TheFu on 2022-12-20
I'm fairly certain that Lubuntu 18.04 support ended in 2021.  [https://lubuntu.me/bionic-eol/](https://lubuntu.me/bionic-eol/)  Yep.

Get on a supported release, ASAP.

---

### Post by guiverc on 2022-12-21
You can use `ubuntu-support-status` to view which packages still receive support (ie. those from 'main' that are used in common with Ubuntu Desktop, Ubuntu Server receive security fixes until April 2023), however those from the Lubuntu/LXDE desktop and other community pacakges (ie. from the 'universe' repository) ended *team support* back in April 2021.

You'll find it talked about here - [https://discourse.lubuntu.me/t/lubuntu-18-04-lts-end-of-life-30-april-2021/2466/7](https://discourse.lubuntu.me/t/lubuntu-18-04-lts-end-of-life-30-april-2021/2466/7) though the whole *thread* may be worth a scan/read, as you'll note if you're using *i386* or 32-bit x86, it was the last *supported* release (*given 18.10 & 19.04 are already EOL*), thus using it makes sense until you get newer hardware.

Also be aware Lubuntu 18.04 LTS was the *end of the road* with regards *release-upgrades* due to it being the last LXDE release. If you scan [https://lubuntu.me/focal-2-released/](https://lubuntu.me/focal-2-released/) you'll note the warning

> ***Note***, due to the extensive changes required  for the shift in desktop environments, the Lubuntu team does not support  upgrading from 18.04 or below to any greater release. Doing so will  result in a broken system. If you are on 18.04 or below and would like  to upgrade, please do a fresh install.

---

### Post by miragejet on 2022-12-21
> **TheFu said:**
> I'm fairly certain that Lubuntu 18.04 support ended in 2021.  [https://lubuntu.me/bionic-eol/](https://lubuntu.me/bionic-eol/)  Yep.

Get on a supported release, ASAP.

> **guiverc said:**
> You can use `ubuntu-support-status` to view which packages still receive support (ie. those from 'main' that are used in common with Ubuntu Desktop, Ubuntu Server receive security fixes until April 2023), however those from the Lubuntu/LXDE desktop and other community pacakges (ie. from the 'universe' repository) ended *team support* back in April 2021.

You'll find it talked about here - [https://discourse.lubuntu.me/t/lubuntu-18-04-lts-end-of-life-30-april-2021/2466/7](https://discourse.lubuntu.me/t/lubuntu-18-04-lts-end-of-life-30-april-2021/2466/7) though the whole *thread* may be worth a scan/read, as you'll note if you're using *i386* or 32-bit x86, it was the last *supported* release (*given 18.10 & 19.04 are already EOL*), thus using it makes sense until you get newer hardware.

Also be aware Lubuntu 18.04 LTS was the *end of the road* with regards *release-upgrades* due to it being the last LXDE release. If you scan [https://lubuntu.me/focal-2-released/](https://lubuntu.me/focal-2-released/) you'll note the warning

Thanks guys,

So given that my CPU is only 32-bit capable, what do you recommend as distro?

---

### Post by TheFu on 2022-12-21
> **miragejet said:**
> Thanks guys,

So given that my CPU is only 32-bit capable, what do you recommend as distro?

If the CPU is under 20 yrs old, it it probably 64-bit.   Please run, then post the output from 'lscpu' or 'inxi -C' so we know exactly which CPU you have. The best possible recommendation will then be possible.   BTW, with 'inxi -bz' output, we can make even better recommendations.  For example:
```
$ inxi -bz    # the -z option hides anything that might be sensitive .. like serial numbers or MACs.
System:    Host: romulus Kernel: 5.4.0-135-generic x86_64 bits: 64 Desktop: N/A
           Distro: Ubuntu 18.04.6 LTS
Machine:   Device: desktop System: BIOSTAR product: T5XE CFX-SLI v: 6.0 serial: N/A
           Mobo: BIOSTAR model: T5XE CFX-SLI serial: N/A
           BIOS: American Megatrends v: 080015 date: 06/02/2010
CPU:       Quad core Intel Core i5 750 (-MCP-) speed/max: 1208/2668 MHz
Graphics:  Card: NVIDIA GF108 [GeForce GT 430]
           Display Server: X.Org 1.20.8 drivers: nvidia (unloaded: modesetting,fbdev,vesa,nouveau)
           Resolution: 1920x1200@59.95hz
           OpenGL: renderer: N/A version: N/A
Network:   Card-1: Realtek RTL8111/8168/8411 PCIE Gigabit Ethernet Controller driver: r8169
           Card-2: Intel 82574L Gigabit Network Connection driver: e1000e
           Card-3: Marvell 88E8001 Gigabit Ethernet Controller driver: skge
Drives:    HDD Total Size: 12502.5GB (37.6% used)
RAID:      Device: 1: /dev/no
Info:      Processes: 264 Uptime: 16 days Memory: 3138.7/15999.9MB Client: Shell (bash) inxi: 2.3.56 

```
I built that system in 2010 to replace an older box. That older box was 64-bit too.  Just sayin'.  

Just because a 32-bit OS was shipped with a system, that doesn't mean the CPU isn't 64-bit.  Showing command output here means we don't have to wonder if a mistake has been made. Some output can be confusing and misinterpreted.

---

### Post by guiverc on 2022-12-21
A huge proportion of 64-bit hardware was sold with 32-bit windows; as it reduced the price by $5 USD, and buyers understood the $5 *saving* far more than 32-bit vs 64-bit.

64-bit systems appeared ~2000 so how old is your box?  Yes laptops (*pentium M*) were commonly 32-bit until 2004, with some still being sold in 2005 when they disappeared from major brands.  In time Ubuntu appeared on laptops incapable of running windows (*as it was sold then, Vista*) on new Intel Atom CPUs, which led microsoft to extend the life of XP & start selling it (again), so 32-bit boxes appeared again in 2006-2007 using Intel Atom CPUs.

In the Lubuntu *discourse* thread I talked about an old IBM Thinkpad t43 I have that still uses Lubuntu 18.04 LTS (which I now consider Ubuntu 18.04 LTS with LXDE).  I've not yet had a need to replace it with another OS as I'm happy with it as it is & how I use it (*rarely actually*).  I'll switch it to Debian myself.

My other *i386* boxes (all pentium M or intel atom) have already been switched to Debian (*or were running Debian already*).  I'm involved in QA (*Quality Assurance*) in both Ubuntu (*and flavors like Lubuntu*) and Debian, and I only had one [*low resource 2003 hp*] box that performed differently between Debian & Ubuntu (*that box performed much better with Lubuntu*)

I'd check your box is 32-bit, and not just sold as 32-bit to reduce price by $5.  You can get some details using `lscpu`*.*

---

### Post by miragejet on 2022-12-23
> 
root@R51E:~# inxi -bz
System:    Host: R51E Kernel: 4.15.0-200-generic i686 bits: 32
           Desktop: LXDE (Openbox 3.6.1) Distro: Ubuntu 18.04.6 LTS
Machine:   Device: laptop System: IBM product: 1843AL1 v: ThinkPad R51e serial: <filter>
           Mobo: IBM model: 1843AL1 serial: <filter>
           BIOS: IBM v: 78ET71WW (1.61 ) date: 12/07/2006
CPU:       Single core Intel Pentium M (-UP-) speed: 1733 MHz (max)
Graphics:  Card: Advanced Micro Devices [AMD/ATI] RC410M [Mobility Radeon Xpress 200M]
           Display Server: X.Org 1.19.6
           drivers: ati,radeon (unloaded: modesetting,fbdev,vesa)
           Resolution: 1024x768@60.00hz
           OpenGL: renderer: ATI RC410 version: 2.1 Mesa 20.0.8
Network:   Card-1: Broadcom and subsidiaries NetXtreme BCM5751F Fast Ethernet PCIE
           driver: tg3
           Card-2: Qualcomm Atheros AR5212/5213/2414 Wireless Network Adapter
           driver: ath5k
Drives:    HDD Total Size: 60.0GB (29.5% used)
Info:      Processes: 143 Uptime: 5:51 Memory: 480.2/1883.3MB
           Client: Shell (bash) inxi: 2.3.56 
root@R51E:~# 


Inxi output for my laptop.

---

### Post by tea for one on 2022-12-23
> **miragejet said:**
> So given that my CPU is only 32-bit capable, what do you recommend as distro?
Here is some light reading to help you choose.
[https://itsfoss.com/32-bit-linux-distributions/](https://itsfoss.com/32-bit-linux-distributions/)

---

### Post by poorguy on 2022-12-23
> **miragejet said:**
> 

So given that my CPU is only 32-bit capable, what do you recommend as distro?


[https://q4os.org/](https://q4os.org/)

***Go with the Trinity desktop.***
[https://q4os.org/downloads1.html](https://q4os.org/downloads1.html)
[I][B]
From above link.[/B][/I]
You can download either a lightweight efficient Trinity desktop, or  more advanced Plasma desktop edition. Live media allow users to get a  quick Q4OS experience, or try it out on a real hardware without  installation. If satisfied, an optional installer is available. Use the  install-cd media for older 64bit as well as 32bit machines.
 The minimal hardware requirements:
Plasma desktop - 1GHz CPU / 1GB RAM / 5GB disk
***Trinity desktop - 300MHz CPU / 256MB RAM / 3GB disk ***

32 bit download.
[https://sourceforge.net/projects/q4os/files/stable/q4os-4.11-i386-instcd.r1.iso/download](https://sourceforge.net/projects/q4os/files/stable/q4os-4.11-i386-instcd.r1.iso/download)

---

### Post by TheFu on 2022-12-23
I had a Dell 620M Pentium M laptop around 2005. Cost about $650+.  I hate to say this, but a $75 used Chromebook would be many times faster and more capable today.  In 2012, I got a $200 Chromebook (Acer C720) that was much, much, much, faster than my PentiumM.  That Chromebook had a  64-bit CPU.

If you stick with the same hardware, you won't be running any flavor of Ubuntu.  Openbox is fairly light.  You might consider fvwm too, which is even lighter.  I'd look for a small debian-based distro and drop fvwm as the WM onto it.

Just some things to consider, but only you can decide what's best.

---

### Post by miragejet on 2022-12-25
> **tea for one said:**
> Here is some light reading to help you choose.
[https://itsfoss.com/32-bit-linux-distributions/](https://itsfoss.com/32-bit-linux-distributions/)

> **poorguy said:**
> [https://q4os.org/](https://q4os.org/)

***Go with the Trinity desktop.***
[https://q4os.org/downloads1.html](https://q4os.org/downloads1.html)
[I][B]
From above link.[/B][/I]
You can download either a lightweight efficient Trinity desktop, or  more advanced Plasma desktop edition. Live media allow users to get a  quick Q4OS experience, or try it out on a real hardware without  installation. If satisfied, an optional installer is available. Use the  install-cd media for older 64bit as well as 32bit machines.
 The minimal hardware requirements:
Plasma desktop - 1GHz CPU / 1GB RAM / 5GB disk
***Trinity desktop - 300MHz CPU / 256MB RAM / 3GB disk ***

32 bit download.
[https://sourceforge.net/projects/q4os/files/stable/q4os-4.11-i386-instcd.r1.iso/download](https://sourceforge.net/projects/q4os/files/stable/q4os-4.11-i386-instcd.r1.iso/download)

Thank you.

> **TheFu said:**
> I had a Dell 620M Pentium M laptop around 2005. Cost about $650+.  I hate to say this, but a $75 used Chromebook would be many times faster and more capable today.  In 2012, I got a $200 Chromebook (Acer C720) that was much, much, much, faster than my PentiumM.  That Chromebook had a  64-bit CPU.

If you stick with the same hardware, you won't be running any flavor of Ubuntu.  Openbox is fairly light.  You might consider fvwm too, which is even lighter.  I'd look for a small debian-based distro and drop fvwm as the WM onto it.

Just some things to consider, but only you can decide what's best.

I see what you mean, I bought this Thinkpad in 2005 for $800 brand new (today's $1200).

I actually have a desktop and other laptops, but I still like this Thinkpad because it has strong sentimental values that can't be expressed in money. It was my mother's gift when I started my career as freelancer PHP/JS/SQL programmer and web designer.

---

