---
title: "File transfer icon stays even after transfer is complete"
date: 2017-11-02
forum: General Help
---

### Post by meetdilip on 2017-11-02
The progress bar in " Files " icon in launcher stays until the system gets restarted. Even if the file transfer is complete. I am using Unity + 16.04

I was told that this is an old bug in 16.04 which got fixed. But, for me, it is there since around 6 months now. Is it possible to get rid of it ? Thanks.

---

### Post by mörgæs on 2017-11-02
Bug fixes related to security are released for 16.04, other bug fixes are normally not. All old Buntu releases are essentially left 'as-is', both long and short term support.

If the bug has been fixed then the correct code will be present by default in 17.10. 

17.10 might have other bugs (after all it's a major task to integrate Wayland) so best to test in a live boot before installing.

---

### Post by meetdilip on 2017-11-02
You mean 16.04 will now only get security updates ?

---

### Post by mörgæs on 2017-11-02
It will get all security updates and a small selection of highly delayed non-security ones. This is the price for stability.

It's not about 'now'. This is the way all old releases are handled.

---

### Post by vasa1 on 2017-11-02
> **meetdilip said:**
> The progress bar in " Files " icon in launcher stays until the system gets restarted. Even if the file transfer is complete. I am using Unity + 16.04

I was told that this is an old bug in 16.04 which got fixed. But, for me, it is there since around 6 months now. Is it possible to get rid of it ? Thanks.
Could you post a link to "I was told that this is an old bug in 16.04 which got fixed."? The progress bar disappears for me once the transfer is completed.
```
$ inxi -Fxz
System:    Host: aes-3567 Kernel: 4.12.0-041200-generic x86_64 (64 bit gcc: 6.3.0)
           Desktop: Unity 7.4.0 (Gtk 3.18.9-1ubuntu3.3)
           Distro: Ubuntu 16.04 xenial
Machine: ...
```and```
$ apt policy nautilus
nautilus:
  Installed: 1:3.18.4.is.3.14.3-0ubuntu6
  Candidate: 1:3.18.4.is.3.14.3-0ubuntu6
  Version table:
 *** 1:3.18.4.is.3.14.3-0ubuntu6 500
        500 http://archive.ubuntu.com/ubuntu xenial-updates/main amd64 Packages
        100 /var/lib/dpkg/status
     1:3.18.4.is.3.14.3-0ubuntu4 500
        500 http://archive.ubuntu.com/ubuntu xenial/main amd64 Packages
$ 
```

---

### Post by meetdilip on 2017-11-02
> "I was told that this is an old bug in 16.04 which got fixed."? The progress bar disappears for me once the transfer is completed.

[https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/1716419](https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/1716419)

---

### Post by meetdilip on 2017-11-02
Here you go

> $ inxi -Fxz
System:    Host: my-PC Kernel: 4.4.0-98-generic x86_64 (64 bit gcc: 5.4.0)
           Desktop: Unity 7.4.0 (Gtk 3.20.8-1ubuntu0~ppa1)
           Distro: Ubuntu 16.04 xenial
Machine:   System: Dell (portable) product: Vostro 3550
           Mobo: Dell model: 0PD77K v: A12 Bios: Dell v: A12 date: 02/18/2014
CPU:       Dual core Intel Core i5-2430M (-HT-MCP-) cache: 3072 KB
           flags: (lm nx sse sse2 sse3 sse4_1 sse4_2 ssse3 vmx) bmips: 9578
           clock speeds: max: 3000 MHz 1: 897 MHz 2: 883 MHz 3: 811 MHz
           4: 804 MHz
Graphics:  Card-1: Intel 2nd Generation Core Processor Family Integrated Graphics Controller
           bus-ID: 00:02.0
           Card-2: Advanced Micro Devices [AMD/ATI] Whistler [Radeon HD 6630M/6650M/6750M/7670M/7690M]
           bus-ID: 01:00.0
           Display Server: X.Org 1.18.4 drivers: ati,radeon,intel (unloaded: fbdev,vesa)
           Resolution: 1366x768@60.00hz
           GLX Renderer: Mesa DRI Intel Sandybridge Mobile
           GLX Version: 3.0 Mesa 17.0.7 Direct Rendering: Yes
Audio:     Card Intel 6 Series/C200 Series Family High Definition Audio Controller
           driver: snd_hda_intel bus-ID: 00:1b.0
           Sound: Advanced Linux Sound Architecture v: k4.4.0-98-generic
Network:   Card-1: Realtek RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
           driver: r8169 v: 2.3LK-NAPI port: d000 bus-ID: 05:00.0
           IF: eth0 state: down mac: <filter>
           Card-2: Broadcom BCM4313 802.11bgn Wireless Network Adapter
           driver: wl bus-ID: 09:00.0
           IF: wlan0 state: up mac: <filter>
Drives:    HDD Total Size: 500.1GB (56.5% used)
           ID-1: /dev/sda model: ST500LT012 size: 500.1GB
Partition: ID-1: / size: 129G used: 79G (65%) fs: ext4 dev: /dev/sda6
           ID-2: swap-1 size: 44.55GB used: 0.15GB (0%) fs: swap dev: /dev/sda5
RAID:      No RAID devices: /proc/mdstat, md_mod kernel module present
Sensors:   System Temperatures: cpu: 57.0C mobo: N/A gpu: N/A
           Fan Speeds (in rpm): cpu: N/A
Info:      Processes: 259 Uptime: 42 min Memory: 2389.3/3857.3MB
           Init: systemd runlevel: 5 Gcc sys: 5.4.0
           Client: Shell (bash 4.3.481) inxi: 2.2.35 


> $ apt policy nautilus
nautilus:
  Installed: 1:3.20.3-1ubuntu2~ubuntu16.04.1
  Candidate: 1:3.20.3-1ubuntu2~ubuntu16.04.1
  Version table:
 *** 1:3.20.3-1ubuntu2~ubuntu16.04.1 100
        100 /var/lib/dpkg/status
     1:3.18.4.is.3.14.3-0ubuntu6 500
        500 [http://in.archive.ubuntu.com/ubuntu](http://in.archive.ubuntu.com/ubuntu) xenial-updates/main amd64 Packages
     1:3.18.4.is.3.14.3-0ubuntu4 500
        500 [http://in.archive.ubuntu.com/ubuntu](http://in.archive.ubuntu.com/ubuntu) xenial/main amd64 Packages



Thanks

---

### Post by vasa1 on 2017-11-02
So you have```
 ii nautilus 1:_3.20_.3-1ubuntu2~ubuntu16.04.1 amd64 file manager and graphical shell for GNOME
```which, AFAICT, isn't the default and so your system isn't "stock" is it?

I just noticed you have GTK 3.20 via a ppa. So definitely not stock or default.

---

### Post by meetdilip on 2017-11-03
I am with stock since 12.04. I want to move to stock, if that's not the case. I am having this issue since some time. I get a Gnomish boot screen instead of Purple from Ubuntu. I don't want to loose my customizations and go for a fresh install. 

I used to have Gnome, Cinnamon and Unity when I was running 14.04. While updating through Cinnamon, I lost Unity. I continued with Cinnamon and upgraded through Gnome DE to 16.04. The upgrade and related fixing from support sites got me my Unity DE back. Currently, I have only Unity, and have not installed any other DE. Thanks.

---

### Post by vasa1 on 2017-11-03
Ouch! That may explain why some things aren't working as they should. Since you're not having major issues, I guess you could just continue with what you have until 16.04 is no longer supported!

---

### Post by meetdilip on 2017-11-03
I have updated by previous post.

I was using stock 12.04 > upgraded to 14.04 > tried a couple of other DE ( Cinnmaon, Gnome ) > automatically lost Unity while in Cinnamon > Upgraded to 16.04 ( with some help ) 

I don't want to loose a couple of things I have set for Android Studio, Ionic Framework etc. I may not be able to put them back. Is there any chance I can replace non-stock elements with stock modules ? Thanks.

---

### Post by vasa1 on 2017-11-03
I think your latest question is now unrelated to the original question. Time for a new thread in which you layout very clearly the history of your system so that people can help you try to get back to "stock"?

---

### Post by meetdilip on 2017-11-03
I had a thread on it long back. I was advised to go with a fresh install. Do you want me to ask this in a new thread or the old one ?

During the process of learning Ubuntu, I have tried various DEs and a few PPAs. I am not sure which took over. What should I do ?

---

### Post by vasa1 on 2017-11-03
Start a new thread! There's no charge ;)

---

### Post by meetdilip on 2017-11-03
Ok

[https://ubuntuforums.org/showthread.php?t=2376551](https://ubuntuforums.org/showthread.php?t=2376551)

---

### Post by mörgæs on 2017-11-03
Though the system might be supported in the sense that security updates are provided you have to realise that you are on your own. There is no need for creating Launchpad reports for a system which is composed of so many parts since people basically can't replicate your environment. 

I know that it takes time to recreate your settings but still I suggest that you do the clean install, keeping as little as possible from the existing system.

(Sorry, should probably have been in the new thread).

---

### Post by meetdilip on 2017-11-04
In fact, until @vasa1 told me last day, I had no idea about the non stock elements in my PC.

---

### Post by deadflowr on 2017-11-04
> **meetdilip said:**
> In fact, until @vasa1 told me last day, I had no idea about the non stock elements in my PC.

I can tell you the non stock parts of the system.
You added (and then somehow disabled) the gnome3-staging ppa.

(It's the only place that you could have grabbed the nautilus  and gtk versions used.)

Properly, you need to re-enable the ppa and then run ppa-purge against it.
That would revert the packages that have been upgraded from the ppa and get you closer to stock Ubuntu.

---

### Post by meetdilip on 2017-11-04
I do fainly recollect adding something like that. 

Software & Updates > Other Software  lists PPAs I have added. There is no entry which refers to gnome3-staging PPA. Should I add it again ? If yes, please share the commands for the same.Thanks.

---

