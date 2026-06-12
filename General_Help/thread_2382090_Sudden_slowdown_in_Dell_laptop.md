---
title: "Sudden slowdown in Dell laptop"
date: 2018-01-08
forum: General Help
---

### Post by oygle on 2018-01-08
My post may be off-topic, so please delete it, if it is. My Dell laptop 3542 is incredibly slow lately, taking 5 mins or more to shutdown. All applications are taking longer to respond, and some I have to kill the process, just kinda hanging ?

I check the monitor, and it says the load is not much higher than 10 percent. Have run smartctl on HDD, passed. Ran memtest and it passed, but I see the CPU temp was between 60 degress C and 65 degrees C. That seems a bit high.  Disk space is okay, plenty of swap and spare HDD; in fact I have removed some big files.

Is it this problem mentioned here ?

---

### Post by DuckHook on 2018-01-08
*Thread moved to **General Help** as the more appropriate forum.*

I've moved your post to a more appropriate forum for technical help. Your initial surmise (that this is the result of Spectre/Meltdown) is less likely than being struck by lightning. The exploit is so new and untested that bad actors are not going to be directing it at you and me. The ones who have to worry for now are guys like banks, cloud providers and server farms.

If you provide more info about your symptoms, specs and logs, the members here may be able to help you with your problem.

---

### Post by vasa1 on 2018-01-08
> **DuckHook said:**
> ...
If you provide more info about your symptoms, specs and logs, the members here may be able to help you with your problem.
^^^^ This!

Posting the following may be a start...

```
inxi -Fxz
```
```
top -bn1 -o %MEM | head -20
```
```
top -bn1 -o %CPU | head -20
```

---

### Post by oygle on 2018-01-08
> **DuckHook said:**
> *Thread moved to **General Help** as the more appropriate forum.*

I've moved your post to a more appropriate forum for technical help. Your initial surmise ....

Okay thanks.

```
inxi -Fxz
```

```
System:    Host: ********-Inspiron-3542 Kernel: 4.4.0-104-generic x86_64 (64 bit gcc: 5.4.0)
           Desktop: KDE Plasma 5.5.5 (Qt 5.5.1) Distro: Ubuntu 16.04 xenial
Machine:   System: Dell (portable) product: Inspiron 3542
           Mobo: Dell model: 0WW73H v: A01 Bios: Dell v: A01 date: 03/28/2014
CPU:       Dual core Intel Core i7-4510U (-HT-MCP-) cache: 4096 KB
           flags: (lm nx sse sse2 sse3 sse4_1 sse4_2 ssse3 vmx) bmips: 7981
           clock speeds: max: 3100 MHz 1: 2000 MHz 2: 2064 MHz 3: 2000 MHz 4: 2000 MHz
Graphics:  Card-1: Intel Haswell-ULT Integrated Graphics Controller bus-ID: 00:02.0
           Card-2: NVIDIA GM108M [GeForce 840M] bus-ID: 08:00.0
           Display Server: X.Org 1.18.4 drivers: intel (unloaded: fbdev,vesa) Resolution: 1366x768@60.02hz
           GLX Renderer: Mesa DRI Intel Haswell Mobile GLX Version: 3.0 Mesa 17.2.4 Direct Rendering: Yes
Audio:     Card-1 Intel 8 Series HD Audio Controller driver: snd_hda_intel bus-ID: 00:1b.0
           Card-2 Intel Haswell-ULT HD Audio Controller driver: snd_hda_intel bus-ID: 00:03.0
           Sound: Advanced Linux Sound Architecture v: k4.4.0-104-generic
Network:   Card-1: Qualcomm Atheros QCA9565 / AR9565 Wireless Network Adapter driver: ath9k bus-ID: 06:00.0
           IF: wlp6s0 state: down mac: <filter>
           Card-2: Realtek RTL8101/2/6E PCI Express Fast/Gigabit Ethernet controller
           driver: r8169 v: 2.3LK-NAPI port: e000 bus-ID: 07:00.0
           IF: enp7s0 state: up speed: 100 Mbps duplex: full mac: <filter>
           Card-3: Atheros usb-ID: 001-007
           IF: null-if-id state: N/A speed: N/A duplex: N/A mac: N/A
Drives:    HDD Total Size: 1000.2GB (46.0% used) ID-1: /dev/sda model: ST1000LM024_HN size: 1000.2GB
Partition: ID-1: / size: 17G used: 7.6G (50%) fs: ext4 dev: /dev/sda1
           ID-2: /home size: 896G used: 417G (50%) fs: ext4 dev: /dev/sda6
           ID-3: swap-1 size: 5.00GB used: 0.00GB (0%) fs: swap dev: /dev/sda5
RAID:      No RAID devices: /proc/mdstat, md_mod kernel module present
Sensors:   System Temperatures: cpu: 52.0C mobo: N/A
           Fan Speeds (in rpm): cpu: N/A
Info:      Processes: 182 Uptime: 2:35 Memory: 956.6/7887.7MB Init: systemd runlevel: 5 Gcc sys: 5.4.0
           Client: Shell (bash 4.3.481) inxi: 2.2.35
```

```
top -bn1 -o %MEM | head -20
```

```
top - 15:37:57 up  2:44,  2 users,  load average: 0.44, 0.37, 0.22
Tasks: 184 total,   1 running, 183 sleeping,   0 stopped,   0 zombie
%Cpu(s):  1.2 us,  0.4 sy,  0.0 ni, 97.5 id,  0.8 wa,  0.0 hi,  0.0 si,  0.0 st
KiB Mem :  8076964 total,  4990072 free,  1079064 used,  2007828 buff/cache
KiB Swap:  4882428 total,  4882428 free,        0 used.  6532984 avail Mem 

  PID USER      PR  NI    VIRT    RES    SHR S  %CPU %MEM     TIME+ COMMAND
 3868 user1     20   0 2466440 422108 135444 S   0.0  5.2   0:31.30 firefox
 1646 user1     20   0 9495504 226740 124900 S   0.0  2.8   0:23.94 plasmashell
 1608 user1     20   0 1507984 219680 150312 S   0.0  2.7   0:03.75 kded5
 7603 user1     20   0 1884428 187492 124144 S   0.0  2.3   0:22.32 Web Content
 3917 user1     20   0 1846992 169808  96924 S   0.0  2.1   0:02.50 Web Content
 1639 user1     39  19 5506296 142600 110064 S   0.0  1.8   0:03.06 baloo_file
 7647 user1     20   0 1830184 135536  94956 S   0.0  1.7   0:03.75 Web Content
 7569 user1     20   0 1801144 113408  88100 S   0.0  1.4   0:00.88 file:// Content
 1638 user1     20   0 2920808  80672  47932 S   0.0  1.0   0:23.00 kwin_x11
 1176 root      20   0  303924  79640  60168 S   0.0  1.0   1:29.04 Xorg
 7519 user1     20   0  605280  70756  56220 S   0.0  0.9   0:02.00 kate
 1643 user1     20   0  679480  70512  52204 S   0.0  0.9   0:02.18 krunner
 1743 user1     20   0  550252  59704  29400 S   0.0  0.7   0:11.84 claws-mail
```

```
top -bn1 -o %CPU | head -20
```

```
top - 15:40:56 up  2:47,  2 users,  load average: 0.17, 0.29, 0.21
Tasks: 184 total,   1 running, 183 sleeping,   0 stopped,   0 zombie
%Cpu(s):  1.3 us,  0.4 sy,  0.0 ni, 97.5 id,  0.8 wa,  0.0 hi,  0.0 si,  0.0 st
KiB Mem :  8076964 total,  4940736 free,  1114044 used,  2022184 buff/cache
KiB Swap:  4882428 total,  4882428 free,        0 used.  6484156 avail Mem 

  PID USER      PR  NI    VIRT    RES    SHR S  %CPU %MEM     TIME+ COMMAND
 1176 root      20   0  312672  81532  61708 S   6.7  1.0   1:32.64 Xorg
 1638 user1     20   0 2920808  80672  47932 S   6.7  1.0   0:24.56 kwin_x11
 3106 user1     20   0  526920  56204  46276 S   6.7  0.7   0:06.87 konsole
    1 root      20   0  119700   5868   4012 S   0.0  0.1   0:01.35 systemd
    2 root      20   0       0      0      0 S   0.0  0.0   0:00.00 kthreadd
    3 root      20   0       0      0      0 S   0.0  0.0   0:00.05 ksoftirqd/0
    4 root      20   0       0      0      0 S   0.0  0.0   0:00.55 kworker/0:0
    5 root       0 -20       0      0      0 S   0.0  0.0   0:00.00 kworker/0:0H
    7 root      20   0       0      0      0 S   0.0  0.0   0:02.02 rcu_sched
    8 root      20   0       0      0      0 S   0.0  0.0   0:00.00 rcu_bh
    9 root      rt   0       0      0      0 S   0.0  0.0   0:00.00 migration/0
   10 root      rt   0       0      0      0 S   0.0  0.0   0:00.04 watchdog/0
   11 root      rt   0       0      0      0 S   0.0  0.0   0:00.04 watchdog/1
```



I notice the CPU is down to 52 degress C, so I assume it was the memtest that increased it significantly ??

---

### Post by oygle on 2018-01-09
Looking at this further and it caused me to install "rkhunter" and it found 10 suspicious files, all 64 Mb in /dev/shm. ( E.g.  /dev/shm/pulse-shm-2530832173: data) . Something to do with pulse-audio, so will add a post in the security forum.

---

### Post by vasa1 on 2018-01-09
```
$ ls /dev/shm
pulse-shm-2003119060  pulse-shm-251514588  pulse-shm-2915995558  pulse-shm-3232626827  pulse-shm-3359133380  pulse-shm-4035981528
$
```This is on Kubuntu 16.04. CPU temp 34 Celsius.

---

### Post by oygle on 2018-01-09
> **vasa1 said:**
> ```
$ ls /dev/shm
pulse-shm-2003119060  pulse-shm-251514588  pulse-shm-2915995558  pulse-shm-3232626827  pulse-shm-3359133380  pulse-shm-4035981528
$
```This is on Kubuntu 16.04. CPU temp 34 Celsius.

Okay, so these files are 'normal'. I don't understand why the CPU temp here is 53 Celsius, whereas your cpu temp is 34 Celsius. I'm only running firefox, dolphin, terminal, kate and claws. None of those are actually processing, just idle. I may look into seeing how to blow any dust,etc away from the cpu.

---

### Post by Yellow Pasque on 2018-01-09
- 60-65C is not bad for a high-powered laptop CPU running Memtest.

- The rkhunter warnings about /dev/shm/pulse are common and nothing to worry about.

- If it was me, I'd be looking through logs. I'd also try to create a new user and see if slowdowns occur with him/her.

---

### Post by oygle on 2018-01-09
> **Temüjin said:**
> - 60-65C is not bad for a high-powered laptop CPU running Memtest.

Yes, I was concerned at first of that high temp, but no after "vasa1" supplied that code to check on temp, I have been able to monitor it. It is doing quite intensive work now (CPU in excess of 25% ) and the temp is not getting over 56.0C

> **Temüjin said:**
> - The rkhunter warnings about /dev/shm/pulse are common and nothing to worry about.

- If it was me, I'd be looking through logs. I'd also try to create a new user and see if slowdowns occur with him/her.

Okay thanks re 'rkhunter' warnings. I was able to use the "lsof" command and saw that it is not just pulseaudio that uses /dev/shm . Noticed 'kate' and 'firefox' and 'web' , and as I closed those apps, the related files disappeared.

Logs - not sure what to check there, other than looking for 'warning' or other strings with grep.

As a precaution (or it may be an overkill), I have installed clamav and running it now. It is very high on CPU usage though.

---

### Post by HermanAB on 2018-01-09
Well, first of all, forget about rkhunter and clamav.  Clamav is useless on a laptop and rkhunter is simply useless in general.  IMHO rkhunter should be dropped from the repositories.

According to top, your CPU is doing nothing and you are using no swap space.  So, when you are doing nothing, your machine is doing nothing - that is how it should be.  You need to be concerned when you are doing nothing and the machine use remains high due to some spinning process.  In that case, kill it to get control back, but this is not your problem.

My guess is that your machine is not slow - rather that your network is probably slow.  Check your DNS with dig.  If you have a lame DNS, then everything you do online will be hickety pickety.  You can check the general network load with ntop.

Finally, you say it is a laptop - so don't shut it down.  Use Suspend.

---

### Post by oygle on 2018-01-11
> **HermanAB said:**
> Well, first of all, forget about rkhunter and clamav.  Clamav is useless on a laptop and rkhunter is simply useless in general.  IMHO rkhunter should be dropped from the repositories.

Can you supply more information please ?

> **HermanAB said:**
> My guess is that your machine is not slow - rather that your network is probably slow.  Check your DNS with dig.  If you have a lame DNS, then everything you do online will be hickety pickety.  You can check the general network load with ntop.

It was all applications, not just firefox.

---

### Post by DuckHook on 2018-01-11
> **nakerasy said:**
> Oh ,i get , you'd better not install"rkhunter" unless you know a lot about operation system ,
*rkhunter* is a tool that finds a ridiculous number of false positives. Moreover, it requires some understanding of what processes normally run in an OS to avoid constantly crying "Wolf", either to yourself or when seeking help. Many experts don't like it because, in the hands of someone not trained in its use, it wastes time, energy and focus that could be better applied towards doing things that *actually* improve real-world security.

If it is used as simply one tool among many, is used as part of a much larger security strategy, and is understood as a very imperfect tool that shouldn't be taken more seriously than it deserves to be, then there is no problem with it. Most users are not knowledgeable enough about it to approach it that way.

Please have a look at the link in my sig: Security Basics.

---

### Post by djchandler on 2018-01-11
I don't want to belabor the obvious solution or be insulting, but have you checked your BIOS settings and made sure the computer isn't running in power saver mode? What about System Settings>Power? Your Memtest CPU temps seem cool to me. A lot of laptops operate in the 70º-90ºC range or higher at full load. I have one old laptop I don't dare run Memtest without a thorough cleaning first for fear the CPU will overheat. 

Occam's Razor.

Either that, or your HD is about to fail. Usual first symptom of that is system slowing down, most noticeable while booting and shutting down. Back up your data.
:(

---

### Post by Yellow Pasque on 2018-01-12
> **djchandler said:**
> I don't want to belabor the obvious solution or be insulting, but have you checked your BIOS settings and made sure the computer isn't running in power saver mode? What about System Settings>Power? Your Memtest CPU temps seem cool to me. A lot of laptops operate in the 70º-90ºC range or higher at full load. I have one old laptop I don't dare run Memtest without a thorough cleaning first for fear the CPU will overheat. 


The CPU reports max non-Turbo speed (2.0 GHz) in the OP's output, so it seems unlikely that it's being limited to idle speed in BIOS.
 
I would still try a different user and/or see if the symptoms occur with LiveUSB.

---

### Post by djchandler on 2018-01-12
Yes, that's true. But the computer doesn't have to run that fast to return those stats. Those stats (multiplier, instruction sets, etc.) are embedded in the CPU. All you need is the software to read it. I stand behind my appraisal.

So the the alternative is HD failure. 3 year warranty, 3 year old latop. I've seen a lot of that problem, so-called dead machines that won't boot, or the complaint is slow boot and shut-down. Easy to recover the data for my friend or customer. All you have to do is boot a Linux live DVD. Or mount the drive via USB on a Linux box and recover data. If I have the freedom to do so, I re-partition and install Linux from scratch after bad sectors have been mapped. Otherwise, we re-install Windows on a new drive or we fix the MBR if possible. Happens all the time.
;)

---

### Post by Yellow Pasque on 2018-01-12
> **djchandler said:**
> Yes, that's true. But the computer doesn't have to run that fast to return those stats. Those stats (multiplier, instruction sets, etc.) are embedded in the CPU.

The **current** speed inxi is reading is not embedded in the CPU. (Hint: Look at /sys/devices/system/cpu/cpu0/cpufreq/ )

> I stand behind my appraisal.

Even if you don't trust CPU speed readings in Linux, reduced CPU speed is not going to cause shutdown of 5 mins.

> So the the alternative is HD failure.

It's possible, but it's not the only possibility. A LiveUSB would help isolate issues related to the hard disk.

---

### Post by oygle on 2018-01-15
Thanks everyone for your help and replies, much appreciated. The laptop seems okay now ?? All I have done is run rkhunter and Clamav, both which gave many false positives, but have found out how to address that. Some things will stay a mystery I guess.  :)

---

### Post by oygle on 2018-01-18
Today I performed a full backup on a website. Used Ark to extract everything and then noticed the very slow response again. Loaded system monitor and watched for a while. As the total CPU load went from between 33% to about 50%, and everything locked up for a while, realised the **culprit** is baloo and baloo_file_extractor.

Killed any processes named 'baloo' and the laptop was very responsive again. There are many posts on the internet in regards to the high CPU usage by these tools. This one interesting at [https://bbs.archlinux.org/viewtopic.php?id=231709](https://bbs.archlinux.org/viewtopic.php?id=231709) , and mention of disabling it. Will read up on this one and otherrs - [https://bbs.archlinux.org/viewtopic.php?id=193169](https://bbs.archlinux.org/viewtopic.php?id=193169)

---

