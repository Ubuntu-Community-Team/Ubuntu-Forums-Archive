---
title: "Ubuntu 14.04 LTS Extreme Lag"
date: 2014-08-26
forum: General Help
---

### Post by Josh22799 on 2014-08-26
When I boot it up. The mouse and Keyboard input are delayed and typing  is almost impossible. Have to keep rebooting it up to 15 times to try to  get it not to lag. But, Since recently It wont stop lagging. The whole  thing is lagging, Not just the Mouse and Keyboard. 
 
Model: Compaq Presario 
Memory: 3.0 GiB 
Prosessor: AMD Athlon 64 Processor 3200+ 
Graphics: Gallium 0.4 on AMD RV620 
OS type: 32 Bit 
Disc size: Around 150 - 200 Gigabytes 
 
Thanks for any help.

---

### Post by mörgæs on 2014-08-28
Hi, welcome to the fora.

Does **top** indicate a process which takes a lot of CPU cycles?

---

### Post by Josh22799 on 2014-08-29
I don't think so. The CPU doesn't seem to be the cause of my problem by  the way. The computer just Lags non stop for no reason. The guy who  built the PC for me said he put some good guts into it. So, I guess it is not supposed to lag.

---

### Post by mörgæs on 2014-08-29
First let's see if it's related to hardware or the system installed. How does it run in a live boot?

---

### Post by Josh22799 on 2014-08-29
It Boots up smoothly. It just lags out when it gets to the login screen and wont stop lagging even after I login.

---

### Post by Tadaen_Sylvermane on 2014-08-29
> [COLOR=#000000]Model: Compaq Presario [/COLOR]
[COLOR=#000000]Memory: 3.0 GiB [/COLOR]
[COLOR=#000000]Prosessor: AMD Athlon 64 Processor 3200+ [/COLOR]
[COLOR=#000000]Graphics: Gallium 0.4 on AMD RV620 [/COLOR]
[COLOR=#000000]OS type: 32 Bit [/COLOR]
[COLOR=#000000]Disc size: Around 150 - 200 Gigabytes 

[/COLOR]

CPU is likely the problem. Socket 939 single core @2ghz. It was awesome 10 years ago. Try Xubuntu or Lubuntu. That video card is also 5 generations old. I hope you didn't get these "good guts" recently and pay a premium for them. If so you were taken big time. I guess you could try installing the proprietary video driver but that won't help the cpu limitations.

---

### Post by Josh22799 on 2014-08-30
Thanks for the info. The thing that confuses me, Is that some times when I boot it up it doesn't lag, and Runs steam games Absolutely beautifully, Other times it just lags out forcing me to reboot it.

Same thing happens if I run another OS on it. (Tried Linux Kali)

---

### Post by QIII on 2014-08-30
Just to pop in here:

There is no current proprietary AMD driver that will work with that GPU, so don't even try to install one.  AMD dropped Linux support for that adapter some time ago and since it is no longer maintained it has not been modified to work with the current X Server used by Ubuntu.

Don't try to install it or you may find me answering in the thread you start on how to fix things!  ;)

Cheers!

---

### Post by mörgæs on 2014-08-30
There's no login in a live boot.

I was not referring to booting, but to a live boot (from USB preferably). You could use the occasion and try X/Lubuntu.

---

### Post by Josh22799 on 2014-08-30
I said that I live booted Linux Kali, Still lagged. But, Sometimes (10%  chance) the system will run Flawlessly (On Any Live boot / Regular  Boot), Even while Playing a Game such as Garry's Mod.

Sorry If I am not very good at this, Only had the PC for 1-2 months :)

---

### Post by patrick48 on 2014-09-01
Hi,

using the same graphic card here and no lagging (kali or Mint 17)
post back the result of 
```
inxi -Fxz
```
> Graphics:  Card: Advanced Micro Devices [AMD/ATI] RV620/M82 [Mobility Radeon HD 3450/3470]
           bus-ID: 01:00.0
           Display Server: X.Org 1.15.1 drivers: ati,radeon (unloaded: fbdev,vesa)
           Resolution: 1280x800@59.9hz
           GLX Renderer: Gallium 0.4 on AMD RV620
           GLX Version: 3.0 Mesa 10.3.0-devel Direct Rendering: Yes



---

### Post by Josh22799 on 2014-09-02
Hi, Here is what I got

```

josh@josh-Ubuntu-Server:~$ inxi -fxz
CPU:       Single core AMD Athlon 64 3200+ (-UP-) cache: 512 KB bmips: 1989.84 clocked at 1000.00 MHz 
           CPU Flags: 3dnow 3dnowext apic clflush cmov cx8 de fpu fxsr fxsr_opt lahf_lm lm mca 
           mce mmx mmxext msr mtrr nx pae pat pge pni pse pse36 sep sse sse2 syscall tsc vme 

```

Hope this is usefull, Took a while to get the computer to do this.

---

### Post by mörgæs on 2014-09-02
I don't have any specific advice for the problem. I think the best you can do is installing some different distros for comparison and post the results. Maybe we are then able to identify a pattern.

---

### Post by patrick48 on 2014-09-03
hi

you did inxi -fxz
we need inxi -Fxz             the full output

---

### Post by Josh22799 on 2014-09-03
Sorry XD

Here is the full result

```

josh@josh-Ubuntu-Server:~$ inxi -Fxz
System:    Host: josh-Ubuntu-Server Kernel: 3.13.0-35-generic i686 (32 bit, gcc: 4.8.2) 
           Desktop: Gnome Distro: Ubuntu 14.04 trusty
Machine:   System: Compaq Presario 061 product: PY068AA-ABG SR1560AN AN530 version: 03l0411RE101AMETH00
           Mobo: MSI model: AMETHYST-M version: 1.0 Bios: Phoenix version: 3.19 date: 06/24/2005
CPU:       Single core AMD Athlon 64 3200+ (-UP-) cache: 512 KB flags: (lm nx pae sse sse2 sse3) bmips: 3979.46 clocked at 2000.00 MHz 
Graphics:  Card: Advanced Micro Devices [AMD/ATI] RV620 LE [Radeon HD 3450] bus-ID: 01:00.0 
           X.Org: 1.15.1 drivers: ati,radeon (unloaded: fbdev,vesa) Resolution: 1440x900@59.9hz 
           GLX Renderer: Gallium 0.4 on AMD RV620 GLX Version: 3.0 Mesa 10.1.3 Direct Rendering: Yes
Audio:     Card-1: Advanced Micro Devices [AMD/ATI] RV620 HDMI Audio [Radeon HD 3400 Series] 
           driver: snd_hda_intel bus-ID: 01:00.1 
           Card-2: Advanced Micro Devices [AMD/ATI] IXP SB400 AC'97 Audio Controller driver: snd_atiixp bus-ID: 00:14.5 
           Sound: Advanced Linux Sound Architecture ver: k3.13.0-35-generic
Network:   Card-1: Realtek RTL-8100/8101L/8139 PCI Fast Ethernet Adapter 
           driver: 8139too ver: 0.9.28 port: df00 bus-ID: 02:03.0
           IF: eth0 state: down mac: <filter>
           Card-2: Realtek RTL8187B Wireless 802.11g 54Mbps Network Adapter driver: rtl8187 usb-ID: 001-003
           IF: wlan2 state: up mac: <filter>
Drives:    HDD Total Size: 160.0GB (14.6% used) 1: id: /dev/sda model: SAMSUNG_SP1614C size: 160.0GB 
Partition: ID: / size: 144G used: 22G (16%) fs: ext4 ID: swap-1 size: 3.22GB used: 0.00GB (0%) fs: swap 
RAID:      No RAID devices detected - /proc/mdstat and md_mod kernel raid module present
Sensors:   System Temperatures: cpu: 29.0C mobo: N/A gpu: 41.0 
           Fan Speeds (in rpm): cpu: N/A 
Info:      Processes: 170 Uptime: 1 min Memory: 336.0/3028.8MB Runlevel: 2 Gcc sys: 4.8.2 
           Client: Shell (bash 4.3.11) inxi: 1.9.17 

```

---

### Post by ThatBum on 2014-09-03
Afraid that machine is pretty old and slow, dude. It was introduced 9 years ago.
[Specifications page for Presario SR1560AN]("http://h20566.www2.hp.com/portal/site/hpsc/template.PAGE/public/kb/docDisplay/?spf_p.tpst=kbDocDisplay&spf_p.prp_kbDocDisplay=wsrp-navigationalState%3DdocId%253Demr_na-c00404367-5%257CdocLocale%253D%257CcalledBy%253D&javax.portlet.begCacheTok=com.vignette.cachetoken&javax.portlet.endCacheTok=com.vignette.cachetoken")
[CPU Rating]("http://www.cpubenchmark.net/cpu.php?cpu=AMD+Athlon+64+3200%2B")
[GPU Rating]("http://www.videocardbenchmark.net/gpu.php?gpu=Radeon+HD+3450&id=581")
Not much you can do. Try Xubuntu or Lubuntu, they're lightweight.

---

### Post by Josh22799 on 2014-09-04
Like I said, 10% of the time, If I boot it up in a Specific way it works flawlessly, Even while running a Game off steam. But when it does lag, It lags from boot-up and that is the thing that confusing. If it is so old, Why does it run flawlessly one day, Then crap the next day? I simply don't get it.

---

### Post by mörgæs on 2014-09-04
That's why people (now three of them) are encouraging you to experiment, for example by installing other distros. When you are able to compare different runs a pattern might appear.

---

### Post by Josh22799 on 2015-03-21
Hello,

Have been doing some Extensive digging into my machine.
I have came up with a few possible causes of my problem.
1. the machines RAM is DDR(1)
2. Motherboard is getting kind of old
3. Power supply?

Have tried different types of Linux on it Such as Xubuntu and Lubuntu, All have the same result.

Also, Sorry for the extensive inactivity. Have been very busy.

Thanks.

---

### Post by Josh22799 on 2015-03-21
Have screwed around with the components more.
The system is now fully functional after a Graphics Card swap with another machine.
The system is now working flawlessly with an amazing 55+ FPS

Thanks to all who have helped! I really appreciate it!

---

