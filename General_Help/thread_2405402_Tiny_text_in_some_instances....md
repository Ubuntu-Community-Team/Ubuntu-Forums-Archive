---
title: "Tiny text in some instances..."
date: 2018-11-05
forum: General Help
---

### Post by erinkanol on 2018-11-05
First I want to make it clear I'm a bit of a Ubuntu noob.

I first discovered it as I installed Cisco's Packet Tracer 7.2. In some instances the text on (one) application and on some web pages (using Firefox) becomes much much smaller than I can imagine was intended by the programmer.

[ATTACH=CONFIG]281550[/ATTACH]
Picture 1: PT7.2 on my 14" laptop screen. Text seems fine, but the symbols are way over-sized.

[ATTACH=CONFIG]281551[/ATTACH]
Picture 2: PT7.2 on my 24" Dell monitor. The symbols are now a better size, but the text almost totally shrunk into atoms.

[ATTACH=CONFIG]281552[/ATTACH]
Dell monitor: Just using Google and the text is way too small even though I'm at 133% magnification.

I have tried looking through the various settings within Tweak and Budgie settings, but to no avail.
The wild theory I have is that Budgie may have problems with showing some instances of code/text/stuff how they are intended to look...

---

### Post by speartip on 2018-11-06
I don't have any problems at all with font size on Budgie. What Font & Size are you using? And what apps are giving you the problem?

---

### Post by erinkanol on 2018-11-07
The two main applications where I've encountered this problem is Packet Tracer 7.2 and Firefox.

I'm using Ubuntu Regular as main fonts. In Firefox I have the Allow page to use its own fonts checkbox checked.

The screenshots are pretty much showing the problems.

---

### Post by speartip on 2018-11-07
Packet Tracer is not in the official Ubuntu Repo, so the problem there likely lies with the program itself, there should be some setting within the program to adjust the font size, if not that's maybe a shortcoming of the program. Firefox is another matter though. That should always follow the Font that you set. Did you install it from the repo or from the Mozilla website? Also do you have the xul-ext-ubufox package installed?

---

### Post by slickymaster on 2018-11-07
Packet Tracer does have a setting to adjust its font type and size. It's under **Options -> Preferences -> Font **tab

[ATTACH=CONFIG]281574[/ATTACH]

---

### Post by erinkanol on 2018-11-08
> **slickymaster said:**
> Packet Tracer does have a setting to adjust its font type and size. It's under **Options -> Preferences -> Font **tab

[ATTACH=CONFIG]281574[/ATTACH]

Yes, I've found that font size setting, but doesn't help me in any way - the differences are minimal in user experience.

---

### Post by erinkanol on 2018-11-08
> **speartip said:**
> Did you install it from the repo or from the Mozilla website? Also do you have the xul-ext-ubufox package installed?

I installed it from the software program thingy in Ubuntu, ie the repo.
The package is installed, yes.

---

### Post by speartip on 2018-11-08
Very strange. I'm struggling because I can't replicate your issue. Budgie behaves very nicely for me. It could be a Hardware issue. Could you list your machines specs. Install inxi & run:
```
inxi -F
```
It might be helpful if you post back the results.

---

### Post by erinkanol on 2018-11-09
```
System:    Host: bubuntu Kernel: 4.15.0-38-generic x86_64 bits: 64
           Desktop: Budgie 10.4  Distro: Ubuntu 18.04.1 LTS
Machine:   Device: laptop System: HP product: HP ProBook 440 G3 serial: N/A
           Mobo: HP model: 8100 v: KBC Version 40.71 serial: N/A
           UEFI: HP v: N78 Ver. 01.24 date: 01/29/2018
Battery    BAT0: charge: 35.1 Wh 94.5% condition: 37.2/37.2 Wh (100%)
CPU:       Dual core Intel Core i5-6200U (-MT-MCP-) cache: 3072 KB
           clock speeds: max: 2800 MHz 1: 500 MHz 2: 500 MHz 3: 500 MHz 4: 500 MHz
Graphics:  Card: Intel HD Graphics 520
           Display Server: x11 (X.Org 1.19.6 )
           drivers: modesetting (unloaded: fbdev,vesa)
           Resolution: 1920x1080@60.00hz
           OpenGL: renderer: Mesa DRI Intel HD Graphics 520 (Skylake GT2)
           version: 4.5 Mesa 18.0.5
Audio:     Card Intel Sunrise Point-LP HD Audio driver: snd_hda_intel
           Sound: Advanced Linux Sound Architecture v: k4.15.0-38-generic
Network:   Card-1: Realtek RTL8111/8168/8411 PCIE Gigabit Ethernet Controller
           driver: r8169
           IF: enp1s0 state: down mac: f4:30:b9:8d:88:18
           Card-2: Intel Wireless 3165 driver: iwlwifi
           IF: wlp2s0 state: up mac: 3c:f8:62:XXXXXXX
Drives:    HDD Total Size: 256.1GB (16.9% used)
           ID-1: /dev/sda model: SanDisk_SD8SN8U size: 256.1GB
Partition: ID-1: / size: 92G used: 41G (47%) fs: ext4 dev: /dev/sda7
RAID:      No RAID devices: /proc/mdstat, md_mod kernel module present
Sensors:   System Temperatures: cpu: 29.0C mobo: 0.0C
           Fan Speeds (in rpm): cpu: N/A
Info:      Processes: 336 Uptime: 2 days Memory: 3871.6/7872.0MB
           Client: Shell (bash) inxi: 2.3.56

```

---

### Post by speartip on 2018-11-09
Nothing seems unusual in your hardware specs. All Intel, same as mine. when you changed your fonts in Budgie Desktop Settings, did you increase the size of all the fonts listed? or just the One?
Also did you checksum the ISO that you downloaded to make sure it wasn't corrupt?

---

### Post by erinkanol on 2018-11-09
[ATTACH=CONFIG]281592[/ATTACH]
These are my font settings.

I have not checksummed the installation file and haven't kept since I installed Budgie this summer.

---

### Post by speartip on 2018-11-09
So to be clear. Are Firefox & Cisco the only 2 apps that you have this issue with?

---

### Post by erinkanol on 2018-11-11
Yes. They are the only 2 apps I have issues with, it seems.

---

