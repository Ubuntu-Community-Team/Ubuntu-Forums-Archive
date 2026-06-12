---
title: "ps -eLf displays numerous threads per process. Malfunction?"
date: 2018-01-25
forum: General Help
---

### Post by ffrr on 2018-01-25
Hi. ps -eLf displays many threads for some processes. They are identical except for the thread id (column 4). My system has become very slow after an upgrade to 16,04, which is why I looked at the processes, hoping to find a hint. Here is what ps -eLf shows:

. . .
mysql     1057     1  1057  0   43 08:07 ?        00:00:00 /usr/sbin/mysqld --daemonize --pid-file=/var/run/mysqld/mysqld.pid
mysql     1057     1  1064  0   43 08:07 ?        00:00:00 /usr/sbin/mysqld --daemonize --pid-file=/var/run/mysqld/mysqld.pid
mysql     1057     1  1108  0   43 08:07 ?        00:00:01 /usr/sbin/mysqld --daemonize --pid-file=/var/run/mysqld/mysqld.pid
. . . 27 more

Is this normal?

Firefox Add-ons: AdBlock, AntiMiner, Cookie AutoDelete, Javascript Control, No Script.

Thanks for any suggestion

Frederic

---

### Post by TheFu on 2018-01-26
I don't have a clue, but ... 

Could you have been hit with one of the crypto-jacking websites/ads that kicks off bitcoin mining in the browser?

---

### Post by vasa1 on 2018-01-26
Please run```
top -bn1 -o %MEM | head -20
```and```
top -bn1 -o %CPU | head -20
```and post the output here.

You could do so when Firefox is running and also when you've completely quit Firefox and disabled internet access.

---

### Post by ffrr on 2018-01-30
Hi TheFu, vasa1

Thanks for your response. I had considered the situation TheFu suggests. I installed the AddOn Antiminer, possibly too late.
The machine is barely usable with Firefox running. It responds in strange ways or not at all, freezes frequently for a little while, grays out, indicating memory squeeze.

vasa1. Below the output of the commands you suggested. I tried to pick a typewriter font for legibility, but failed miserably. Sorry about that.

Frederic   


=================================================================================

Firefox running and internet connected

---------------------------------------------------------------------------------

```
fr@hatchbox-2:~/finance/banks/fidelity/work$ top -bn1 -o %MEM | head -20 

top - 22:42:50 up 13:59,  1 user,  load average: 1.32, 1.49, 1.29
Tasks: 216 total,   2 running, 214 sleeping,   0 stopped,   0 zombie
%Cpu(s):  4.2 us,  1.1 sy,  0.0 ni, 93.1 id,  1.6 wa,  0.0 hi,  0.0 si,  0.0 st
KiB Mem :  3910876 total,   554232 free,  2805264 used,   551380 buff/cache
KiB Swap:  4064252 total,  1183164 free,  2881088 used.   535828 avail Mem 

  PID USER      PR  NI    VIRT    RES    SHR S  %CPU %MEM     TIME+ COMMAND
 2181 fr        20   0 2695732 671252  22068 S   0.0 17.2  16:38.75 Web Content
 2082 fr        20   0 3135964 425580  76464 S  13.3 10.9  32:26.26 firefox
 2134 fr        20   0 3560188 386776  67568 S   0.0  9.9  10:13.27 Web Content
  838 clamav    20   0  779756 376220      0 S   0.0  9.6   1:10.95 clamd
 3209 fr        20   0 4445344 346692   2412 S   0.0  8.9   4:12.37 java
 5251 fr        20   0 2582820 243540  25628 S   0.0  6.2   4:59.36 Web Content
 3109 fr        20   0 2218488 159448  43556 S   0.0  4.1   1:53.32 thunderbird
 5290 fr        20   0 2338024 133272  39060 S   0.0  3.4   8:15.12 Web Content
 1032 root      20   0 1548972 114032  99436 S   0.0  2.9  16:10.81 Xorg
 1835 fr        20   0 1694744  59576  31576 R  20.0  1.5  30:51.56 compiz
 6939 fr        20   0 1762560  25152  22860 S   0.0  0.6   0:09.68 eog
 3278 fr        20   0  130708  24656   1688 S   0.0  0.6   5:12.59 idle-python2.7
 1532 fr        20   0  628652  23060   6556 S   0.0  0.6   0:04.29 hud-service


fr@hatchbox-2:~/finance/banks/fidelity/work$ top -bn1 -o %CPU | head -20 

top - 22:43:56 up 14:00,  1 user,  load average: 1.06, 1.37, 1.26
Tasks: 216 total,   1 running, 215 sleeping,   0 stopped,   0 zombie
%Cpu(s):  4.2 us,  1.1 sy,  0.0 ni, 93.1 id,  1.6 wa,  0.0 hi,  0.0 si,  0.0 st
KiB Mem :  3910876 total,   555648 free,  2802812 used,   552416 buff/cache
KiB Swap:  4064252 total,  1183932 free,  2880320 used.   537928 avail Mem 

  PID USER      PR  NI    VIRT    RES    SHR S  %CPU %MEM     TIME+ COMMAND
 1835 fr        20   0 1695208  59848  31832 S  13.3  1.5  31:01.89 compiz
 2082 fr        20   0 3135964 426384  76464 S  13.3 10.9  32:36.48 firefox
 1032 root      20   0 1548840 114100  99504 S   6.7  2.9  16:15.01 Xorg
 2134 fr        20   0 3560188 387040  67568 S   6.7  9.9  10:14.72 Web Content
 5251 fr        20   0 2978084 512392  25628 S   6.7 13.1   5:01.31 Web Content
 8404 fr        20   0   42112   3640   3040 R   6.7  0.1   0:00.01 top
    1 root      20   0  185248   1936    828 S   0.0  0.0   0:01.74 systemd
    2 root      20   0       0      0      0 S   0.0  0.0   0:00.01 kthreadd
    4 root       0 -20       0      0      0 S   0.0  0.0   0:00.00 kworker/0:0H
    6 root       0 -20       0      0      0 S   0.0  0.0   0:00.00 mm_percpu_wq
    7 root      20   0       0      0      0 S   0.0  0.0   0:00.04 ksoftirqd/0
    8 root      20   0       0      0      0 S   0.0  0.0   0:07.67 rcu_sched
    9 root      20   0       0      0      0 S   0.0  0.0   0:00.00 rcu_bh
```

=================================================================================

Firefox closed and internet disconnected

---------------------------------------------------------------------------------

```
fr@hatchbox-2:~/finance/banks/fidelity/work$ top -bn1 -o %MEM | head -20 

top - 22:46:11 up 14:02,  1 user,  load average: 6.12, 2.76, 1.76
Tasks: 213 total,   1 running, 212 sleeping,   0 stopped,   0 zombie
%Cpu(s):  4.2 us,  1.1 sy,  0.0 ni, 93.0 id,  1.7 wa,  0.0 hi,  0.0 si,  0.0 st
KiB Mem :  3910876 total,  1873980 free,  1487720 used,   549176 buff/cache
KiB Swap:  4064252 total,  2260924 free,  1803328 used.  1912460 avail Mem 

  PID USER      PR  NI    VIRT    RES    SHR S  %CPU %MEM     TIME+ COMMAND
 2082 fr        20   0 2993432 376740  46508 S   6.2  9.6  32:45.95 firefox
  838 clamav    20   0  779756 376220      0 S   0.0  9.6   1:10.95 clamd
 3209 fr        20   0 4445344 349356   4876 S   0.0  8.9   4:13.01 java
 3109 fr        20   0 2218488 159840  43788 S   0.0  4.1   1:53.53 thunderbird
 1032 root      20   0 1515576  98284  79096 S   0.0  2.5  16:19.94 Xorg
 1835 fr        20   0 1694608  64756  36168 S   6.2  1.7  31:13.26 compiz
 1532 fr        20   0  628936  25240   6808 S   0.0  0.6   0:04.37 hud-service
 6939 fr        20   0 1762560  25152  22860 S   0.0  0.6   0:09.69 eog
 3278 fr        20   0  130708  24656   1688 S   0.0  0.6   5:13.74 idle-python2.7
 1806 fr        20   0  979236  17808   8120 S   0.0  0.5   0:14.90 nautilus
 3286 fr        20   0  631128  15860   1360 S   0.0  0.4   8:45.82 python2.7
 1577 fr        20   0  644636  15140   5692 S   0.0  0.4   0:07.73 unity-panel-ser
 4278 fr        20   0  519452  14724   6808 S   0.0  0.4   0:27.37 gnome-terminal-

fr@hatchbox-2:~/finance/banks/fidelity/work$ top -bn1 -o %CPU | head -20 

top - 22:46:15 up 14:02,  1 user,  load average: 6.12, 2.76, 1.76
Tasks: 214 total,   1 running, 213 sleeping,   0 stopped,   0 zombie
%Cpu(s):  4.2 us,  1.1 sy,  0.0 ni, 93.0 id,  1.7 wa,  0.0 hi,  0.0 si,  0.0 st
KiB Mem :  3910876 total,  1857424 free,  1499092 used,   554360 buff/cache
KiB Swap:  4064252 total,  2262972 free,  1801280 used.  1901204 avail Mem 

  PID USER      PR  NI    VIRT    RES    SHR S  %CPU %MEM     TIME+ COMMAND
 1032 root      20   0 1515576  97840  78652 S   6.2  2.5  16:19.98 Xorg
 2082 fr        20   0 2960648 387536  46604 S   6.2  9.9  32:46.04 firefox
 8476 fr        20   0   42112   3668   3072 R   6.2  0.1   0:00.01 top
    1 root      20   0  185248   3068   1864 S   0.0  0.1   0:01.75 systemd
    2 root      20   0       0      0      0 S   0.0  0.0   0:00.01 kthreadd
    4 root       0 -20       0      0      0 S   0.0  0.0   0:00.00 kworker/0:0H
    6 root       0 -20       0      0      0 S   0.0  0.0   0:00.00 mm_percpu_wq
    7 root      20   0       0      0      0 S   0.0  0.0   0:00.04 ksoftir
    8 root      20   0       0      0      0 S   0.0  0.0   0:07.78 rcu_sched
    9 root      20   0       0      0      0 S   0.0  0.0   0:00.00 rcu_bh
   10 root      rt   0       0      0      0 S   0.0  0.0   0:00.01 migration/0
   11 root      rt   0       0      0      0 S   0.0  0.0   0:00.09 watchdog/0
   12 root      20   0       0      0      0 S   0.0  0.0   0:00.00 cpuhp/0

```
=================================================================================

---

### Post by vasa1 on 2018-01-30
From your results ...

 Firefox running and internet connected
```
 2082 fr        20   0 3135964 425580  76464 S  13.3 10.9  32:26.26 firefox
```

 Firefox closed and internet disconnected
```
 2082 fr        20   0 2993432 376740  46508 S   6.2  9.6  32:45.95 firefox
```
So Firefox doesn't appear to be closed :???:

---

### Post by TheFu on 2018-01-31
On a 4G machine, FF is a hog.  BTW, I have a 4G machine and FF is a hog here too.  I have just a few addons.
* noscript - default is to block all JS. 
* uBlock Origin (is this the safe one?)
* ghostery
* tree style tabs
* Wallabag - save pages to my self-hosted server
and I've disabled/removed the "ubuntu chrome" and readitlater stuff.
Also disabled flash playback of any sort and the Cisco video plugins.

I've had to kill firefox a few times, but the newest versions haven't been so bad on real hardware.  

Also use and NX remote desktop about 8 hrs a day and inside that connection, firefox is slow, slow, slow, slow, slow. The NX-agent is the only process that uses more CPU than FF.   Started researching that issue this morning.

---

### Post by vasa1 on 2018-01-31
> **TheFu said:**
> ...
* uBlock Origin (is this the safe one?)...
That's the one I use and it's developed and maintained by the original developer: [https://github.com/gorhill/uBlock](https://github.com/gorhill/uBlock)

---

### Post by ffrr on 2018-02-01
vasa1

I reran top again after closing Firefox and killing the process:

--------------------------------------------------------------------------------------------------

```
fr@hatchbox-2:~/finance/banks/r$ top -bn1 -o %MEM | head -20
top - 18:37:24 up 10:19,  1 user,  load average: 0.71, 0.84, 1.02
Tasks: 219 total,   1 running, 218 sleeping,   0 stopped,   0 zombie
%Cpu(s): 18.7 us,  2.9 sy,  0.2 ni, 77.1 id,  1.1 wa,  0.0 hi,  0.0 si,  0.0 st
KiB Mem :  3910876 total,  1182424 free,  1973572 used,   754880 buff/cache
KiB Swap:  4064252 total,  3075232 free,   989020 used.  1309780 avail Mem 

  PID USER      PR  NI    VIRT    RES    SHR S  %CPU %MEM     TIME+ COMMAND
  842 clamav    20   0  779652 523636    244 S   0.0 13.4   0:42.70 clamd
 3264 fr        20   0  785268 337032   4508 S   0.0  8.6   5:20.61 python2.7
 2068 fr        20   0 4443296 313116   8056 S   0.0  8.0   1:55.99 java
 5834 fr        20   0 2193112 190260  49500 S   0.0  4.9   0:38.86 thunderbird
 1693 fr        20   0 1562268 147880  46744 S   6.7  3.8  12:02.30 compiz
 1069 root      20   0  536904 143336 122316 S   0.0  3.7   9:47.43 Xorg
 6257 fr        20   0 1374912  97276   9472 S   0.0  2.5   0:17.82 gimp-2.8
 7173 fr        20   0  347264  51852   9736 S   0.0  1.3   0:00.48 display
 7679 fr        20   0  538760  49248  34948 S   6.7  1.3   0:44.69 gnome-system-mo
 7045 fr        20   0  186236  37084  12932 S   0.0  0.9   0:00.12 display
 6828 fr        20   0  186236  36988  12840 S   0.0  0.9   0:00.09 display
 1557 fr        20   0  550396  36156   7392 S   0.0  0.9   0:06.85 hud-service
 1577 fr        20   0  652420  35588  13452 S   0.0  0.9   0:08.96 unity-panel-ser
fr@hatchbox-2:~/finance/banks/r$ top -bn1 -o %CPU | head -20
top - 18:37:35 up 10:19,  1 user,  load average: 0.68, 0.83, 1.01
Tasks: 219 total,   1 running, 218 sleeping,   0 stopped,   0 zombie
%Cpu(s): 18.7 us,  2.9 sy,  0.2 ni, 77.1 id,  1.1 wa,  0.0 hi,  0.0 si,  0.0 st
KiB Mem :  3910876 total,  1181928 free,  1974568 used,   754380 buff/cache
KiB Swap:  4064252 total,  3075232 free,   989020 used.  1309316 avail Mem 

  PID USER      PR  NI    VIRT    RES    SHR S  %CPU %MEM     TIME+ COMMAND
 1069 root      20   0  536392 142968 121948 S  13.3  3.7   9:48.32 Xorg
 1693 fr        20   0 1562260 147880  46744 S  13.3  3.8  12:02.89 compiz
 7842 fr        20   0   42112   3580   3004 R  13.3  0.1   0:00.02 top
    1 root      20   0  185248   3500   2200 S   0.0  0.1   0:01.55 systemd
    2 root      20   0       0      0      0 S   0.0  0.0   0:00.00 kthreadd
    4 root       0 -20       0      0      0 S   0.0  0.0   0:00.00 kworker/0:0H
    6 root       0 -20       0      0      0 S   0.0  0.0   0:00.00 mm_percpu_wq
    7 root      20   0       0      0      0 S   0.0  0.0   0:00.04 ksoftirqd/0
    8 root      20   0       0      0      0 S   0.0  0.0   0:04.99 rcu_sched
    9 root      20   0       0      0      0 S   0.0  0.0   0:00.00 rcu_bh
   10 root      rt   0       0      0      0 S   0.0  0.0   0:00.01 migration/0
   11 root      rt   0       0      0      0 S   0.0  0.0   0:00.05 watchdog/0
   12 root      20   0       0      0      0 S   0.0  0.0   0:00.00 cpuhp/0

```
(How does one get that into a scrollable window?)



As TheFu suggested, I may have been get hit by a crypto-mining son of a bitch. If I run the system monitor after reactivating from suspended, I see a lot of activity in both cpu and in/out trail, doing nothing myself. The memory (3.7 Gb) is used up near or at the top. After a few minutes the agitation ceases. I do have almost 20 browser tabs standing by. Possibly the respective pages cause the commotion and it might be better no to continuously auto-delete cookies. Who knows how to manage runnign tasks? Monitoring is one thing but doesn't do much good, if one doesn't know what one is looking at. Is there a way to detect malicious processes and the actor that kicks them off?

Frederic

---

### Post by TheFu on 2018-02-02
Too hard to read that output. Please, please, please, use **code tags**.  That's "Adv Reply" and the (#) key. Changing fonts is discouraged.  

20 tabs is about 10 too many on a 4G machine, sadly.  Cookies don't matter from what I can tell.

Task management is part of most early chapters in Learning Unix books.  [http://blog.jdpfu.com/2017/03/31/learning-linux-condensed](http://blog.jdpfu.com/2017/03/31/learning-linux-condensed) has a link to one such book.  There are lots of different ways to trace how any process was launched.  **pstree** is pretty easy.

---

### Post by vasa1 on 2018-02-02
While cryptomining is quite the craze these days, if you have issues when no browser is open, then it's possible to discount that as the cause.

All of your top outputs show your system is using swap. Even when I was using a laptop with 4GB RAM, I never saw swap being used.

The impact of having numerous tabs open in your browser depends on the content in each tab. All the same, browsers are getting better at giving fewer resources to background tabs.

Re. browser extensions, I don't use any of those you've listed in your first post.

If you're experiencing issues, why don't you first limit the number of user-initiated programs?

A useful tool is *inxi*. After installing it, run```
inxi -Fxz
```and post the output here. The output may help people understand more about your system and guide you better.

---

### Post by TheFu on 2018-02-02
> **vasa1 said:**
> While cryptomining is quite the craze these days, if you have issues when no browser is open, then it's possible to discount that as the cause.


Yep. Looks like the GPU is the slowdown above.  Using a lite desktop would probably help with that.

GIMP is a hog.
Thunderbird isn't lite.
compiz?  On a 4G box?  Might not be a good idea.

Ah ... Unity.  Would you consider loading a lighter GUI, perhaps Mate or XFCE or LXDE?  Should take about 3 minutes.   I find Mate to be the most "polished" of the lighter DEs. ```
 sudo apt update ; sudo apt install mate-desktop
``` will install it.  Logout, click on the "gear", select Mate from the menu and login again. If this works nicely, wait 1 or 2 weeks, then you can purge Unity (or not), as you like.  Unity is pretty heavy, IMHO.

---

### Post by ffrr on 2018-02-02
Thanks for your continued support.

Here's the output of inxi

```
fr@hatchbox-2:~/finance/banks/pi/correspondence$ inxi -Fxz
System:    Host: hatchbox-2 Kernel: 4.13.0-32-generic x86_64 (64 bit gcc: 5.4.0)
           Desktop: Unity 7.4.0 (Gtk 3.18.9-1ubuntu3.3) Distro: Ubuntu 16.04 xenial
Machine:   System: Dell product: Latitude E6530 v: 01
           Mobo: Dell model: 0JC5MT v: A01 Bios: Dell v: A07 date: 10/08/2012
CPU:       Dual core Intel Core i5-3320M (-HT-MCP-) cache: 3072 KB
           flags: (lm nx sse sse2 sse3 sse4_1 sse4_2 ssse3 vmx) bmips: 10366
           clock speeds: max: 3300 MHz 1: 2591 MHz 2: 2591 MHz 3: 2591 MHz 4: 2591 MHz
Graphics:  Card: Intel 3rd Gen Core processor Graphics Controller bus-ID: 00:02.0
           Display Server: X.Org 1.19.5 drivers: (unloaded: fbdev,vesa) Resolution: 1920x1080@60.15hz
           GLX Renderer: Mesa DRI Intel Ivybridge Mobile GLX Version: 3.0 Mesa 17.2.4 Direct Rendering: Yes
Audio:     Card Intel 7 Series/C210 Series Family High Definition Audio Controller
           driver: snd_hda_intel bus-ID: 00:1b.0
           Sound: Advanced Linux Sound Architecture v: k4.13.0-32-generic
Network:   Card-1: Intel 82579LM Gigabit Network Connection driver: e1000e v: 3.2.6-k port: f080 bus-ID: 00:19.0
           IF: eno1 state: up speed: 1000 Mbps duplex: full mac: <filter>
           Card-2: Broadcom BCM4313 802.11bgn Wireless Network Adapter driver: wl bus-ID: 02:00.0
           IF: wlp2s0 state: down mac: <filter>
Drives:    HDD Total Size: 1320.2GB (14.9% used) ID-1: /dev/sda model: WDC_WD3200BPVT size: 320.1GB temp: 40C
           ID-2: USB /dev/sdc model: Elements_25A2 size: 1000.2GB temp: 0C
Partition: ID-1: / size: 290G used: 62G (23%) fs: ext4 dev: /dev/sda1
           ID-2: swap-1 size: 4.16GB used: 0.87GB (21%) fs: swap dev: /dev/sda5
RAID:      No RAID devices: /proc/mdstat, md_mod kernel module present
Sensors:   System Temperatures: cpu: 48.0C mobo: N/A
           Fan Speeds (in rpm): cpu: N/A
Info:      Processes: 229 Uptime: 12:37 Memory: 2566.9/3819.2MB Init: systemd runlevel: 5 Gcc sys: 5.4.0
           Client: Shell (bash 4.3.481) inxi: 2.2.35 

```

And thanks for the reference: [http://blog.jdpfu.com/2017/03/31/learning-linux-condensed](http://blog.jdpfu.com/2017/03/31/learning-linux-condensed). I'll lean into that first thing. I have used pstree and marvelled at the outstanding legibility. After learning linux condensed I hope to be able to interpret the genealogy or processes.

 Frederic

---

### Post by TheFu on 2018-02-02
Seems like a nice enough laptop, just light on RAM for what that CPU can do.  
I have an older i5-520M which is about 50% slower than yours, but with more RAM. It does Ubuntu-Mate nicely.

---

### Post by ffrr on 2018-02-03
Thanks for your continued support. Sorry about the delay. I posted the output of inxi yesterday. It seems to have gotten lost. So here I go again.

```
fr@hatchbox-2:~$ inxi -Fxz
System:    Host: hatchbox-2 Kernel: 4.13.0-32-generic x86_64 (64 bit gcc: 5.4.0)
           Desktop: Unity 7.4.0 (Gtk 3.18.9-1ubuntu3.3) Distro: Ubuntu 16.04 xenial
Machine:   System: Dell product: Latitude E6530 v: 01
           Mobo: Dell model: 0JC5MT v: A01 Bios: Dell v: A07 date: 10/08/2012
CPU:       Dual core Intel Core i5-3320M (-HT-MCP-) cache: 3072 KB
           flags: (lm nx sse sse2 sse3 sse4_1 sse4_2 ssse3 vmx) bmips: 10366
           clock speeds: max: 3300 MHz 1: 2591 MHz 2: 2591 MHz 3: 2591 MHz 4: 2591 MHz
Graphics:  Card: Intel 3rd Gen Core processor Graphics Controller bus-ID: 00:02.0
           Display Server: X.Org 1.19.5 drivers: (unloaded: fbdev,vesa) Resolution: 1920x1080@60.15hz
           GLX Renderer: Mesa DRI Intel Ivybridge Mobile GLX Version: 3.0 Mesa 17.2.4 Direct Rendering: Yes
Audio:     Card Intel 7 Series/C210 Series Family High Definition Audio Controller
           driver: snd_hda_intel bus-ID: 00:1b.0
           Sound: Advanced Linux Sound Architecture v: k4.13.0-32-generic
Network:   Card-1: Intel 82579LM Gigabit Network Connection driver: e1000e v: 3.2.6-k port: f080 bus-ID: 00:19.0
           IF: eno1 state: up speed: 1000 Mbps duplex: full mac: <filter>
           Card-2: Broadcom BCM4313 802.11bgn Wireless Network Adapter driver: wl bus-ID: 02:00.0
           IF: wlp2s0 state: down mac: <filter>
Drives:    HDD Total Size: 320.1GB (21.7% used) ID-1: /dev/sda model: WDC_WD3200BPVT size: 320.1GB
Partition: ID-1: / size: 290G used: 61G (23%) fs: ext4 dev: /dev/sda1
           ID-2: swap-1 size: 4.16GB used: 1.72GB (41%) fs: swap dev: /dev/sda5
RAID:      No RAID devices: /proc/mdstat, md_mod kernel module present
Sensors:   System Temperatures: cpu: 46.0C mobo: N/A
           Fan Speeds (in rpm): cpu: N/A
Info:      Processes: 214 Uptime: 7:43 Memory: 1831.8/3819.2MB Init: systemd runlevel: 5 Gcc sys: 5.4.0
           Client: Shell (bash 4.3.481) inxi: 2.2.35 

```

My latest hunting efforts point to a Firefox Add-On. After disabling them all, memory ceased to hit the ceiling. It's still high at 68% with a relatively modest number of open apps and 9 tabs in Firefox. What surprised me when I fired up this morning and ran the system monitor first thing, memory was already up to 50% (1.85 Gb.)

What I am going to do is reactivate the Add-Ons one at a time and hopefully catch the culprit. That is going to take a few cycles of shutdowns and restarts, which I don't intend to do in one session. The line-up of suspects is AdBlock, AntiMiner, Cookie AutoDelete, Javascript Control and NoScript. I'll be back with a report.

Frederic

---

### Post by ffrr on 2018-02-05
Here my latest findings:

Turning on and off add-ons made no difference. Clearing the cache made some difference: It takes as little longer till memory is full. Immediately after starting, before opening any apps, the system monitor already shows memory at 50% (1.85 Gb). Is that okay? 

At this point I return to my first post: Is the generation of multiple identical threads at system initialization evidence of a malfunction and if so what could be cause and remedy? "pstree" shows the respective threads as "n*[{name}]":

```
fr@hatchbox-2:~$ pstree | grep '*'

        |-fwupd-+-3*[{GUsbEventThread}]
        |         |         |         |                 |                 |-2*[{evolution-calen}]
        |         |         |         |                 |                 |-2*[{evolution-alarm}]
        |         |         |         |                 |                 `-10*[{pool}]
        |         |         |         |                 |                 `-4*[{pool}]
        |         |         |         |            `-2*[{gvfsd-fuse}]
        |         |         |         |               `-4*[{pool}]
        |         |         |         |-2*[upstart-dbus-br]
        |-mysqld---26*[{mysqld}]
        |-rtkit-daemon---2*[{rtkit-daemon}]
        |-snapd---7*[{snapd}]


``` 

"mysqld"' has no descendants and descends itself directly from the initializing process # 1 systemd

```


systemd&#9472;&#9516;&#9472; . . .
                . . .
               &#9500;&#9472;mysqld&#9472;&#9472;&#9472;26*[{mysqld}]
                . . .
 

``` 

Grepping threads for "mysqld", which scores a record 26 repetitions:

```
fr@hatchbox-2:~$ ps -eLf | grep mysqld
mysql     1008     1  1008  0   27 12:22 ?        00:00:00 /usr/sbin/mysqld --daemonize --pid-file=/var/run/mysqld/mysqld.pid
mysql     1008     1  1009  0   27 12:22 ?        00:00:00 /usr/sbin/mysqld --daemonize --pid-file=/var/run/mysqld/mysqld.pid
mysql     1008     1  1011  0   27 12:22 ?        00:00:00 /usr/sbin/mysqld --daemonize --pid-file=/var/run/mysqld/mysqld.pid
mysql     1008     1  1012  0   27 12:22 ?        00:00:00 /usr/sbin/mysqld --daemonize --pid-file=/var/run/mysqld/mysqld.pid
mysql     1008     1  1013  0   27 12:22 ?        00:00:00 /usr/sbin/mysqld --daemonize --pid-file=/var/run/mysqld/mysqld.pid
mysql     1008     1  1014  0   27 12:22 ?        00:00:00 /usr/sbin/mysqld --daemonize --pid-file=/var/run/mysqld/mysqld.pid
mysql     1008     1  1015  0   27 12:22 ?        00:00:00 /usr/sbin/mysqld --daemonize --pid-file=/var/run/mysqld/mysqld.pid
mysql     1008     1  1016  0   27 12:22 ?        00:00:00 /usr/sbin/mysqld --daemonize --pid-file=/var/run/mysqld/mysqld.pid
mysql     1008     1  1017  0   27 12:22 ?        00:00:00 /usr/sbin/mysqld --daemonize --pid-file=/var/run/mysqld/mysqld.pid
mysql     1008     1  1018  0   27 12:22 ?        00:00:00 /usr/sbin/mysqld --daemonize --pid-file=/var/run/mysqld/mysqld.pid
mysql     1008     1  1019  0   27 12:22 ?        00:00:00 /usr/sbin/mysqld --daemonize --pid-file=/var/run/mysqld/mysqld.pid
mysql     1008     1  1020  0   27 12:22 ?        00:00:00 /usr/sbin/mysqld --daemonize --pid-file=/var/run/mysqld/mysqld.pid
mysql     1008     1  1021  0   27 12:22 ?        00:00:00 /usr/sbin/mysqld --daemonize --pid-file=/var/run/mysqld/mysqld.pid
mysql     1008     1  1033  0   27 12:22 ?        00:00:00 /usr/sbin/mysqld --daemonize --pid-file=/var/run/mysqld/mysqld.pid
mysql     1008     1  1034  0   27 12:22 ?        00:00:00 /usr/sbin/mysqld --daemonize --pid-file=/var/run/mysqld/mysqld.pid
mysql     1008     1  1035  0   27 12:22 ?        00:00:00 /usr/sbin/mysqld --daemonize --pid-file=/var/run/mysqld/mysqld.pid
mysql     1008     1  1036  0   27 12:22 ?        00:00:00 /usr/sbin/mysqld --daemonize --pid-file=/var/run/mysqld/mysqld.pid
mysql     1008     1  1037  0   27 12:22 ?        00:00:00 /usr/sbin/mysqld --daemonize --pid-file=/var/run/mysqld/mysqld.pid
mysql     1008     1  1038  0   27 12:22 ?        00:00:00 /usr/sbin/mysqld --daemonize --pid-file=/var/run/mysqld/mysqld.pid
mysql     1008     1  1039  0   27 12:22 ?        00:00:00 /usr/sbin/mysqld --daemonize --pid-file=/var/run/mysqld/mysqld.pid
mysql     1008     1  1040  0   27 12:22 ?        00:00:00 /usr/sbin/mysqld --daemonize --pid-file=/var/run/mysqld/mysqld.pid
mysql     1008     1  1041  0   27 12:22 ?        00:00:00 /usr/sbin/mysqld --daemonize --pid-file=/var/run/mysqld/mysqld.pid
mysql     1008     1  1042  0   27 12:22 ?        00:00:00 /usr/sbin/mysqld --daemonize --pid-file=/var/run/mysqld/mysqld.pid
mysql     1008     1  1043  0   27 12:22 ?        00:00:00 /usr/sbin/mysqld --daemonize --pid-file=/var/run/mysqld/mysqld.pid
mysql     1008     1  1044  0   27 12:22 ?        00:00:00 /usr/sbin/mysqld --daemonize --pid-file=/var/run/mysqld/mysqld.pid
mysql     1008     1  1102  0   27 12:22 ?        00:00:00 /usr/sbin/mysqld --daemonize --pid-file=/var/run/mysqld/mysqld.pid
mysql     1008     1  1103  0   27 12:22 ?        00:00:00 /usr/sbin/mysqld --daemonize --pid-file=/var/run/mysqld/mysqld.pid
fr        2529  2438  2529  0    1 12:26 pts/16   00:00:00 grep --color=auto mysqld


```

Comments? Suggestions?

Frederic

---

### Post by TheFu on 2018-02-05
mysql has lots of tuning controls.  I don't use it, so cannot help. Certainly there is away to control how many initial/max threads are used.  For a home system, I'd expect 4-5 threads to be more than enough. Threads share the same memory space, BTW.

If you want to reduce RAM use, don't use Unity. Switch to a lighter DE.

I don't use evolution. Seemed too bloaty like Outlook last time I played with it.  OTOH, Thunderbird isn't exactly lite either.

Canonical has decided to push snaps on all of us, even when we don't use it.  They do that with lots of other things too, in-case someone might need it in 3 yrs.  I guess. [https://ubuntuforums.org/showthread.php?t=2328152](https://ubuntuforums.org/showthread.php?t=2328152)

Unused RAM is a waste. Generally, the OS keeps things in RAM as needed to improve performance. Sometimes RAM is used for network and disk buffers.

---

### Post by vasa1 on 2018-02-05
> **ffrr said:**
> Here my latest findings:

Turning on and off add-ons made no difference. Clearing the cache made some difference: It takes as little longer till memory is full. **Immediately after starting, before opening any apps,** the system monitor already shows memory at 50% (1.85 Gb). Is that okay? 

...
What is in your autostart?

---

### Post by ffrr on 2018-02-07
The Fu - I appreciate your suggestions about alternatives that use less memory. Would you comment again on the tixi output in view of the purchase of a new machine. This one is about five years old and the technical documentation doesn't say it will run forever. If it quits I'm up there high and dry. So I want to custom-order a new one. Which of the tixi items do you think are most in need of imporvement? More RAM, that's for sure. What abount SSD drives? As to the brand, I favor Dell, because I've never had a hardware problem in ten years, other than a key come loose that was fixed the next day when some overnight delivery service brought a new keyboard free of charge under the warranty terms. Dell also offers Ubuntu as an option. So does HP, I understand. I am open to suggestions regarding other brands.

vasa1 - Here's what I find in autostart:

```
fr@hatchbox-2:/etc/xdg/autostart$ ll
total 208
drwxr-xr-x 2 root root 4096 Feb  2 11:03 ./
drwxr-xr-x 5 root root 4096 Aug  1  2017 ../
-rw-r--r-- 1 root root  345 Apr 15  2016 a11y-profile-manager-indicator-autostart.desktop
-rw-r--r-- 1 root root  202 Feb 25  2016 at-spi-dbus-bus.desktop
-rw-r--r-- 1 root root  286 Apr  4  2016 caribou-autostart.desktop
-rw-r--r-- 1 root root  374 Dec  7  2016 deja-dup-monitor.desktop
-rw-r--r-- 1 root root  462 May 19  2017 evolution-alarm-notify.desktop
-rw-r--r-- 1 root root  193 Dec  5  2015 gnome-getting-started.desktop
-rw-r--r-- 1 root root  485 Nov  1  2015 gnome-keyring-pkcs11.desktop
-rw-r--r-- 1 root root  478 Nov  1  2015 gnome-keyring-secrets.desktop
-rw-r--r-- 1 root root  445 Nov  1  2015 gnome-keyring-ssh.desktop
-rw-r--r-- 1 root root  448 Jan  4  2016 gnome-screensaver.desktop
-rw-r--r-- 1 root root  302 Aug 22  2016 gnome-settings-daemon.desktop
-rw-r--r-- 1 root root  183 Jul 13  2017 gnome-software-service.desktop
-rw-r--r-- 1 root root  464 Apr 20  2016 gnome-user-share-obexpush.desktop
-rw-r--r-- 1 root root  444 Apr 20  2016 gnome-user-share-webdav.desktop
-rw-r--r-- 1 root root  279 Nov 27  2015 gsettings-data-convert.desktop
-rw-r--r-- 1 root root  264 Jan 20  2017 indicator-application.desktop
-rw-r--r-- 1 root root  302 May 27  2016 indicator-bluetooth.desktop
-rw-r--r-- 1 root root  310 Apr  7  2016 indicator-datetime.desktop
-rw-r--r-- 1 root root  298 Nov 25  2015 indicator-keyboard.desktop
-rw-r--r-- 1 root root  283 May  5  2015 indicator-messages.desktop
-rw-r--r-- 1 root root  286 Jan  5  2016 indicator-power.desktop
-rw-r--r-- 1 root root  202 Jan  4  2016 indicator-printers.desktop
-rw-r--r-- 1 root root  252 Apr 12  2016 indicator-session.desktop
-rw-r--r-- 1 root root  295 Apr  7  2016 indicator-sound.desktop
-rw-r--r-- 1 root root  210 Dec 14  2016 nautilus-autostart.desktop
-rw-r--r-- 1 root root  350 May 12  2017 nm-applet.desktop
-rw-r--r-- 1 root root  289 Apr 18  2016 onboard-autostart.desktop
-rw-r--r-- 1 root root  301 Apr  8  2016 orca-autostart.desktop
-rw-r--r-- 1 root root  358 Nov 21  2014 polkit-gnome-authentication-agent-1.desktop
-rw-r--r-- 1 root root  375 Mar  8  2016 print-applet.desktop
-rw-r--r-- 1 root root 4474 Jun 21  2017 pulseaudio.desktop
-rw-r--r-- 1 root root 4141 Oct 11  2016 tracker-extract.desktop
-rw-r--r-- 1 root root 4438 Oct 11  2016 tracker-miner-apps.desktop
-rw-r--r-- 1 root root 5316 Oct 11  2016 tracker-miner-fs.desktop
-rw-r--r-- 1 root root 5121 Oct 11  2016 tracker-miner-user-guides.desktop
-rw-r--r-- 1 root root 5032 Oct 11  2016 tracker-store.desktop
-rw-r--r-- 1 root root  363 Jul  1  2016 unity-fallback-mount-helper.desktop
-rw-r--r-- 1 root root  302 Jul  1  2016 unity-settings-daemon.desktop
-rw-r--r-- 1 root root 9344 Mar 28  2017 update-notifier.desktop
-rw-r--r-- 1 root root  312 Jul  3  2013 user-dirs-update-gtk.desktop
-rw-r--r-- 1 root root  424 Oct  5  2016 vino-server.desktop
-rw-r--r-- 1 root root  244 Feb 24  2016 zeitgeist-datahub.desktop

```

This is the outcome of default installations, downloads from respectable sources, and upgrades, precooked fare out of the microwave, as it were. A competent cook can surely improve the recipe. I am too unfamiliar with ingredients to risk spoiling the meal. 

Frederic

---

### Post by vasa1 on 2018-02-07
> **ffrr said:**
> ...
This is the outcome of default installations, downloads from respectable sources, and upgrades, precooked fare out of the microwave, as it were. A competent cook can surely improve the recipe. I am too unfamiliar with ingredients to risk spoiling the meal. 

FredericI'm not quite sure what you're getting at there, but > **Immediately after starting, before opening any apps**, the system monitor already shows memory at 50% (1.85 Gb). Is that okay? made me wonder ...

---

### Post by TheFu on 2018-02-07
I look for a few different things when considering a purchase.  What I need and what you need probably aren't similar.  For me, laptops are remote access machines. I know that a $400 desktop will blow away a $2000 laptop for performance. It just needs to be available on the internet - which my systems are - via ssh and openvpn.

My list:
[LIST=1]
[*]Price - this is always a consideration
[*]Ability to run Linux easily; my current chromebook was difficult to get Linux installed
[*]Screen size (personal preference)
[*]Video resolution (personal preference at lest 1080p)
[*]VGA and HDMI video output; I have a KVM switch for VGA.
[*]8G+ RAM; need at least 4, 8 is better, 16G is a complete waste for my needs.
[*]4+ Cores (check the passmark for average performance)
[*]VT-x support (non-negotiable)
[*]Storage slot type (m.2, mSATA, 2.5inch HDD?)
[*]Keyboard "feel" - I like Dell
[*]Wired GigE ethernet - non-negotiable to me.
[*]eSATA for external storage
[*]At least 2 USB3+ ports
[*]Repair issues check for problems.
[*]Customer service issues check for problems.
[*]Media slot for SDHC storage (camera)
[*]Under 3 lbs
[*]8+ hrs of battery
[*]The best wifi chip available
[*]Ability to disable bluetooth completely.
[/LIST]

Replaceable RAM and storage on a real laptop is necessary.  My chromebook has 4G soldered on. No upgrade possible.  The disk storage is a small m.2, but easy enough to swap out.  Keyboard replacements, however, require breaking plastic rivets and disassembling the entire laptop, including the motherboard. Not fun or easy. Swapping a keyboard on a Dell XPS is trivial.

I've been burned by keyboards wearing out on my last 3 laptops.  Even the Dell Core i5 system has a repeating key that occurs about 1-2 times a week. It is from 2010, so I don't really want to put any money into it. Battery is dead. It hasn't left the house in 6 yrs, since I became addicted to sub-3lb, 8+ hr, devices.

But your needs are probably very different.

---

### Post by ffrr on 2018-02-08
The Fu  - Thanks for your ideas about hardware configuration. Harking back to your recommendation to replace 'untity' with 'mate', I installed 'mate', logged out, clicked on the "gear" and down dropped a two-item menu: 'Suspend' and 'Shut Down'. To get on I had to log in again. Now the "gear" menu offered more choices. The only pertinent one seemed 'System Settings'. Alas, after walking through all the choices, none pertained to 'mate', 'unity' or anything of the kind.

Both of you, please don't feel compelled to continue this thread. I shall have to spend some time improving my familiarity with the basics. Thank you for your help.   

Frederic

---

### Post by TheFu on 2018-02-08
It sounds like you are pushing the wrong "gear" icon on the login page.  Different login managers have it in different locations. Some have it next to the password field, not up in the corner.

---

### Post by ffrr on 2018-02-09
I found the "gear" in the login frame. It is an Ubuntu logo. When I hit it I can select either GNOME or Ubuntu (default). The frame that visualizes the current choice is around Ubuntu (default). When I pick GNOME, everything looks the same. So Ubuntu (default) may be GNOME. The menu doesn't offer 'mate', which I did download.

---

### Post by TheFu on 2018-02-09
> **ffrr said:**
> I found the "gear" in the login frame. It is an Ubuntu logo. When I hit it I can select either GNOME or Ubuntu (default). The frame that visualizes the current choice is around Ubuntu (default). When I pick GNOME, everything looks the same. So Ubuntu (default) may be GNOME. The menu doesn't offer 'mate', which I did download.

Did you install ubuntu-mate-desktop?  It needs to be installed, not just downlaoded.
I helped someone running 16.04 Unity last Sunday do exactly this.  Worked for them.

---

### Post by ffrr on 2018-02-11
I simulated the installation of 'mate' and got 26 items to be installed, about 300  lines 'Inst' and about 300 Conf, whatever that means. I would expect the  installation to take more time than I have right now. I am not even  sure I want to install 'mate'. I am very conservative with  installations, because they sometimes introduce inconsistencies. An  installation of this size makes me a little nervous. Furthermore, I made progress on another front. I should change the name  of this thread. The profusion of identical threads in the 'ps' display is not the problem, only possible evidence pointing to the problem, which is memory squeeze. I focused on the processes and found  that the ones running immediately after startup did indeed occupy half of  my RAM (1.85 Gb remaining free). Here is how the processes rank after a few applications were loaded. (The choice of columns I took from the 'ps' man page, without exactly knowing what they mean.) The relevant columns are the two last ones: '%MEM' and 'Total'. The table is a ranking by '%MEM', and 'Total' is the running total of the '%MEM' columnl. Of the table's 200 records. I only show the top ones that indicate a non-negligible amount of memory.

```
$ ps -eo pid,tid,time,stime,class,ni,psr,pcpu,stat,wchan,comm -o %mem
(Edited output)
| PID  | TID  | TIME     | STIME | CLS| NI| PSR| %CPU | STAT | WCHAN  | COMMAND         | %MEM  ] Total |
| 4061 | 4061 | 00:00:20 | 11:11 | TS | 0 |  2 | 4.60 | Ssl  | -      | clamd           | 14.10 | 14.10 |
| 3250 | 3250 | 00:01:29 | 09:42 | TS | 0 |  2 | 1.50 | Sl   | poll_s | firefox         | 10.80 | 24.90 |
| 3832 | 3832 | 00:00:13 | 10:43 | TS | 0 |  3 | 0.60 | Sl   | futex_ | java            |  5.80 | 30.70 |
| 2161 | 2161 | 00:00:16 | 09:07 | TS | 0 |  1 | 0.20 | Sl   | poll_s | thunderbird     |  5.60 | 36.30 |
| 3302 | 3302 | 00:01:51 | 09:42 | TS | 0 |  2 | 1.90 | Sl   | poll_s | Web Content     |  5.10 | 41.40 |
|  996 |  996 | 00:00:04 | 09:06 | TS | 0 |  1 | 0.00 | Sl   | -      | mysqld          |  4.40 | 45.80 |
| 1039 | 1039 | 00:08:06 | 09:06 | TS | 0 |  3 | 6.10 | Ssl+ | -      | Xorg            |  3.90 | 49.70 |
| 1839 | 1839 | 00:04:22 | 09:06 | TS | 0 |  0 | 3.30 | Ssl  | poll_s | compiz          |  3.80 | 53.50 |
| 1887 | 1887 | 00:00:03 | 09:06 | TS | 0 |  1 | 0.00 | SLl  | poll_s | gnome-software  |  2.70 | 56.20 |
| 3468 | 3468 | 00:00:00 | 09:47 | TS | 0 |  1 | 0.00 | Sl   | poll_s | Web Content     |  2.30 | 58.50 |
| 1845 | 1845 | 00:00:00 | 09:06 | TS | 0 |  3 | 0.00 | Sl   | poll_s | evolution-calen |  1.50 | 60.00 |
| 1928 | 1928 | 00:00:00 | 09:06 | TS | 0 |  2 | 0.00 | Sl   | poll_s | nautilus        |  1.30 | 61.30 |
| 1956 | 1956 | 00:00:00 | 09:06 | TS | 0 |  1 | 0.00 | Sl   | poll_s | evolution-calen |  1.20 | 62.50 |
| 1978 | 1978 | 00:00:00 | 09:07 | TS | 0 |  0 | 0.00 | Sl   | poll_s | evolution-calen |  1.20 | 63.70 |
| 2674 | 2674 | 00:00:22 | 09:08 | TS | 0 |  1 | 0.20 | Sl   | poll_s | gnome-terminal- |  1.20 | 64.90 |
| 3893 | 3893 | 00:00:17 | 10:46 | TS | 0 |  1 | 0.80 | Sl   | poll_s | python2.7       |  1.20 | 66.10 |
. . .


```

Two thirds of 3.7 Gb are in use at this point. The System Monitor confirms. 'compiz' and 'gnome' are no heavyweights. If I start opening tabs in Firefox, I'd probably hit the top without trying hard. The top scorer is 'clamd', hogging over a half Gb! 'clamd', I understand, monitors all traffic all the time to intercept malware. I'm not aware that it has ever intercepted anything, so scheduled scans might seem more appropriate. I killed 'clamd' earlier today, but just notice that it has resurrected.

      Now to the problem: the odd behavior when all RAM is used up. The System Monitor shows 'Memory' (moving purple line) at the top and 'Swap' (moving green line) still at the bottom. Response times slow massively. The 'Memory' line creeps down a little and the 'Swap' up a little and response times are normal again. I continue and before long the same annoyance recurs. With every recurrence, 'Swap' goes up and eventually will also top out. When it gets close to the top, excessive response times persist with gray-outs on and off, until the user interface is dead and it's shutdown time the ungraceful way (power switch). Curiously, I noticed on one occasion that, while the user interface was completely frozen, the System Monitor displayed continuous network activity in and out, and the disk drive's pilot light was on solid, and stayed on after I pulled the network plug. Firefox was loaded and had a few open tabs. If memory serves I had disabled all add-ons. I failed to observe the network after pulling the plug, but don't see how it could possibly continue corresponding when disconnected.

There seems to be a problem with the management of swap memory. Swapping may cause perceptible delays, but should certainly not cause incapacitating ones. At some point, not very long ago, something must have changed, because I used to load applications and browser tabs with gay abandon and all was working just fine.

At this point I would appreciate suggestions that allowed me to narrow the focus of my investigations.

Thankful regards  

Frederic

---

### Post by TheFu on 2018-02-12
Installing Mate takes about 3 minutes. It isn't ADDING more to the system. It is replacing Unity with something 50% (or more) lighter. Or you could try LXDE or XFCE desktops. Completely up to you.  You have choices.  Use it for a week, see how you like the lighter desktop and better performance, then you purge Unity - which will be 50+ packages, if you like. If Unity (or mate) isn't being used, then it is just storage. Not RAM.  Unity has gotten larger and larger over the years because they target people with 16G of RAM and a Core i7 CPU.  People with expensive computers deserve a beautiful desktop with all the "cheese" possible too.

But for people with lessor computers, there are many, many, lighter options than Unity/KDE.

Web browsers got heavier when Google-chrome decided to start pre-loading linked pages automatically, before those links were requested.  This made all the webpages larger, with more dynamic content, since loading appears faster, at the cost of RAM use.  Firefox had little choice but to follow with the pre-loading links to remain competitive.

Clam really isn't needed for Linux.  There is a sticky thread in the Security subforum about AV. Purge the packages AFTER reading that sticky thread, if you agree.

Using almost all of swap WILL DEFINITELY slow a computer down.  Putting swap onto an SSD will drastically help.

Unity is a well-known hog on RAM and system resources.  The fix for Unity is LXDE, XFCE or Mate. That is well-know too.  Looking for other solutions without attacking the root issue (Unity) is futile.  IMHO.

Why use Thunderbird AND Evolution?  Thunderbird has calendaring.

---

### Post by again? on 2018-02-12
> **ffrr said:**
> 

My latest hunting efforts point to a Firefox Add-On. After disabling them all, memory ceased to hit the ceiling. It's still high at 68% with a relatively modest number of open apps and 9 tabs in Firefox. What surprised me when I fired up this morning and ran the system monitor first thing, memory was already up to 50% (1.85 Gb.)

Frederic
Using 1.85 Gb memory at boot is abnormal.
My 16.04 unity boots to about 700mb with several startup applications.
Can't find it anywhere in the thread but did you say what's using a lot of memory when you initially boot?

I have a an old pc with 4gb of ram and Unity runs fine with moderate use.
Even with 20 firefox tabs seeing about 2 gb of ram used.
I have vm.swappiness=10 (default is 60) and rarely see swap being used at all. [_What is swappiness and how do I change it?_]("https://help.ubuntu.com/community/SwapFaq#What_is_swappiness_and_how_do_I_change_it.3F")
```
glen@Xen2:~$ inxi -b
System:    Host: Xen2 Kernel: 4.13.0-32-generic x86_64 (64 bit) Desktop: Unity 7.4.0
           Distro: Ubuntu 16.04 xenial
Machine:   Mobo: Gigabyte model: GA-78LMT-USB3 v: x.x Bios: Award v: FA date: 04/23/2013
CPU:       Quad core AMD FX-4300 (-MCP-) speed/max: 1400/3800 MHz
Graphics:  Card: NVIDIA GF116 [GeForce GTX 550 Ti]
           Display Server: X.Org 1.19.5 driver: nvidia Resolution: 1680x1050@59.88hz
           GLX Renderer: GeForce GTX 550 Ti/PCIe/SSE2 GLX Version: 4.5.0 NVIDIA 384.111
Network:   Card: Realtek RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller driver: r8169
Drives:    HDD Total Size: 870.2GB (14.7% used)
Info:      Processes: 233 Uptime: 2 min Memory: 885.8/3927.0MB Client: Shell (bash) inxi: 2.2.35
```

> **TheFu said:**
> Clam really isn't needed for Linux.  There is a sticky thread in the Security subforum about AV. Purge the packages AFTER reading that sticky thread, if you agree.
I agree with this and think it may be where the problems lie.

---

### Post by ffrr on 2018-02-13
Thank you all for your information and suggestions.

TheFu
1. I installed 'mate'. It looks fine.I trust it uses less memory.
2. I removed clam.
3. Your question: "Why use Thunderbird AND Evolution?  Thunderbird has calendaring?" 
         Evolution must have come with Thunderbird. It wasn't my choice. If I  don't need Evolution, should I do 'apt-get remove evolution'?

guber2
1. I reduced swappiness to 10
2. Your question: "Can't find it anywhere in the thread but did you say what's using a lot of memory when you initially boot?"
        That is precisely what I hope to find out. With swappiness at 10 and  'clam' gone, the System Monitor gives a less hectic impression. It showed 45% (1.7 Gb) before I loaded anything (other than the System Monitor). Now I have two  terminals open, Firefox with four tabs, Jedit and python IDLE. The System Monitor shows 56% (2. Gb). The process list sorted by %mem now looks like this (I clip some one hundred lines with %mem 0.0). The running total comes up to 60%. ('free' reports 38%.)

```
fr@hatchbox-2:~$ ps -eo pid,tid,time,stime,class,ni,psr,pcpu,stat,wchan,comm -o %mem
(Edited output)
| PID  | TID  | TIME     | STIME | CLS | NI  | PSR | %CPU | STAT | WCHAN  | COMMAND         | %MEM | Total |
| 2345 | 2345 | 00:01:06 | 10:19 | TS  | 0   |   2 | 2.50 | Sl   | poll_s | firefox         | 8.90 |  8.90 |
| 2400 | 2400 | 00:01:14 | 10:19 | TS  | 0   |   1 | 2.90 | Sl   | poll_s | Web-Content     | 6.00 | 14.90 |
| 1105 | 1105 | 00:00:01 | 10:16 | TS  | 0   |   0 | 0.00 | Sl   | -      | mysqld          | 4.80 | 19.70 |
| 1832 | 1832 | 00:01:37 | 10:16 | TS  | 0   |   1 | 3.50 | Ssl  | poll_s | compiz          | 3.90 | 23.60 |
|  976 |  976 | 00:03:04 | 10:16 | TS  | 0   |   2 | 6.50 | Ssl+ | -      | Xorg            | 2.70 | 26.30 |
| 2464 | 2464 | 00:00:00 | 10:19 | TS  | 0   |   3 | 0.00 | Sl   | poll_s | Web-Content     | 2.50 | 28.80 |
| 1902 | 1902 | 00:00:01 | 10:16 | TS  | 0   |   2 | 0.00 | SLl  | poll_s | gnome-software  | 2.00 | 30.80 |
| 1853 | 1853 | 00:00:00 | 10:16 | TS  | 0   |   0 | 0.00 | Sl   | poll_s | evolution-calen | 1.50 | 32.30 |
| 1868 | 1868 | 00:00:01 | 10:16 | TS  | 0   |   0 | 0.00 | Sl   | poll_s | nautilus        | 1.30 | 33.60 |
| 1927 | 1927 | 00:00:00 | 10:16 | TS  | 0   |   3 | 0.00 | Sl   | poll_s | evolution-calen | 1.20 | 34.80 |
| 1943 | 1943 | 00:00:00 | 10:17 | TS  | 0   |   3 | 0.00 | Sl   | poll_s | evolution-calen | 1.20 | 36.00 |
| 2217 | 2217 | 00:01:22 | 10:17 | TS  | 0   |   0 | 3.00 | Sl   | poll_s | gnome-system-mo | 1.20 | 37.20 |
| 1900 | 1900 | 00:00:00 | 10:16 | TS  | 0   |   0 | 0.00 | Sl   | poll_s | evolution-alarm | 1.10 | 38.30 |
| 2287 | 2287 | 00:00:02 | 10:18 | TS  | 0   |   3 | 0.00 | Sl   | poll_s | gnome-terminal- | 1.00 | 39.30 |
| 1700 | 1700 | 00:00:00 | 10:16 | TS  | 0   |   1 | 0.00 | Ssl  | poll_s | hud-service     | 0.90 | 40.20 |
| 1660 | 1660 | 00:00:01 | 10:16 | TS  | 0   |   2 | 0.00 | Ssl  | poll_s | bamfdaemon      | 0.80 | 41.00 |
| 1702 | 1702 | 00:00:00 | 10:16 | TS  | 0   |   3 | 0.00 | Ssl  | poll_s | unity-settings- | 0.80 | 41.80 |
| 1720 | 1720 | 00:00:00 | 10:16 | TS  | 0   |   2 | 0.00 | Ssl  | poll_s | unity-panel-ser | 0.80 | 42.60 |
| 1842 | 1842 | 00:00:00 | 10:16 | TS  | 0   |   0 | 0.00 | Sl   | poll_s | goa-daemon      | 0.80 | 43.40 |
| 1901 | 1901 | 00:00:00 | 10:16 | TS  | 0   |   1 | 0.00 | Sl   | poll_s | nm-applet       | 0.80 | 44.20 |
| 1970 | 1970 | 00:00:00 | 10:17 | TS  | 0   |   0 | 0.00 | Sl   | -      | fwupd           | 0.80 | 45.00 |
| 1746 | 1746 | 00:00:00 | 10:16 | TS  | 0   |   0 | 0.00 | Ssl  | poll_s | indicator-keybo | 0.70 | 45.70 |
| 1878 | 1878 | 00:00:00 | 10:16 | TS  | 0   |   2 | 0.00 | Sl   | poll_s | tracker-store   | 0.70 | 46.40 |
| 2256 | 2256 | 00:00:00 | 10:17 | TS  | 0   |   0 | 0.00 | Sl   | poll_s | update-notifier | 0.60 | 47.00 |
|  914 |  914 | 00:00:00 | 10:15 | TS  | 0   |   2 | 0.00 | Ssl  | -      | snapd           | 0.50 | 47.50 |
| 1809 | 1809 | 00:00:00 | 10:16 | TS  | 0   |   3 | 0.00 | Sl   | poll_s | evolution-sourc | 0.50 | 48.00 |
| 1879 | 1879 | 00:00:00 | 10:16 | TS  | 0   |   3 | 0.00 | Sl   | poll_s | unity-fallback- | 0.50 | 48.50 |
| 1892 | 1892 | 00:00:00 | 10:16 | TS  | 0   |   3 | 0.00 | Sl   | poll_s | polkit-gnome-au | 0.50 | 49.00 |
| 2177 | 2177 | 00:00:00 | 10:17 | TS  | 0   |   3 | 0.00 | Sl   | poll_s | unity-scope-loa | 0.50 | 49.50 |
|  908 |  908 | 00:00:00 | 10:15 | TS  | 0   |   1 | 0.00 | Ssl  | -      | NetworkManager  | 0.40 | 49.90 |
| 1745 | 1745 | 00:00:00 | 10:16 | TS  | 0   |   3 | 0.00 | Ssl  | poll_s | indicator-datet | 0.40 | 50.30 |
| 1941 | 1941 | 00:00:00 | 10:17 | TS  | 0   |   1 | 0.00 | Sl   | poll_s | evolution-addre | 0.40 | 50.70 |
| 1967 | 1967 | 00:00:00 | 10:17 | TS  | 0   |   2 | 0.00 | Sl   | poll_s | evolution-addre | 0.40 | 51.10 |
| 2130 | 2130 | 00:00:00 | 10:17 | TS  | 0   |   1 | 0.00 | Sl   | poll_s | zeitgeist-datah | 0.40 | 51.50 |
| 2167 | 2167 | 00:00:00 | 10:17 | TS  | 0   |   3 | 0.00 | Sl   | poll_s | unity-scope-hom | 0.40 | 51.90 |
| 1273 | 1273 | 00:00:00 | 10:16 | TS  | 0   |   3 | 0.00 | Ssl  | -      | whoopsie        | 0.30 | 52.20 |
| 1716 | 1716 | 00:00:00 | 10:16 | TS  | 0   |   2 | 0.00 | Ssl  | poll_s | gnome-session-b | 0.30 | 52.50 |
| 1772 | 1772 | 00:00:00 | 10:16 | TS  | 0   |   2 | 0.00 | Ssl  | poll_s | indicator-appli | 0.30 | 52.80 |
| 1872 | 1872 | 00:00:00 | 10:16 | TS  | 19  |   1 | 0.00 | SNl  | poll_s | tracker-miner-f | 0.30 | 53.10 |
| 1874 | 1874 | 00:00:00 | 10:16 | TS  | 19  |   0 | 0.00 | SNl  | poll_s | tracker-extract | 0.30 | 53.40 |
| 2128 | 2128 | 00:00:00 | 10:17 | TS  | 0   |   0 | 0.00 | Sl   | poll_s | zeitgeist-fts   | 0.30 | 53.70 |
| 2179 | 2179 | 00:00:00 | 10:17 | TS  | 0   |   1 | 0.00 | Sl   | poll_s | unity-files-dae | 0.30 | 54.00 |
|  846 |  846 | 00:00:00 | 10:15 | TS  | 0   |   2 | 0.00 | Ssl  | -      | thermald        | 0.20 | 54.20 |
|  857 |  857 | 00:00:00 | 10:15 | TS  | 0   |   1 | 0.00 | Ss   | -      | cupsd           | 0.20 | 54.40 |
|  861 |  861 | 00:00:00 | 10:15 | TS  | 0   |   3 | 0.00 | Ssl  | -      | ModemManager    | 0.20 | 54.60 |
|  904 |  904 | 00:00:00 | 10:15 | TS  | 0   |   2 | 0.00 | Ssl  | -      | cups-browsed    | 0.20 | 54.80 |
|  929 |  929 | 00:00:00 | 10:15 | TS  | 0   |   2 | 0.00 | Ssl  | -      | polkitd         | 0.20 | 55.00 |
|  931 |  931 | 00:00:00 | 10:15 | TS  | 0   |   1 | 0.00 | Ssl  | -      | colord          | 0.20 | 55.20 |
| 1460 | 1460 | 00:00:00 | 10:16 | TS  | 0   |   0 | 0.00 | Ssl  | -      | upowerd         | 0.20 | 55.40 |
| 1606 | 1606 | 00:00:00 | 10:16 | TS  | 0   |   0 | 0.00 | Ss   | poll_s | window-stack-br | 0.20 | 55.60 |
| 1744 | 1744 | 00:00:00 | 10:16 | TS  | 0   |   1 | 0.00 | Ssl  | poll_s | indicator-power | 0.20 | 55.80 |
| 1747 | 1747 | 00:00:00 | 10:16 | TS  | 0   |   2 | 0.00 | Ssl  | poll_s | indicator-sound | 0.20 | 56.00 |
| 1795 | 1795 | 00:00:00 | 10:16 | TS  | -11 |   1 | 0.00 | S<l  | poll_s | pulseaudio      | 0.20 | 56.20 |
| 1865 | 1865 | 00:00:00 | 10:16 | IDL | -   |   3 | 0.00 | SNl  | poll_s | tracker-miner-u | 0.20 | 56.40 |
| 1912 | 1912 | 00:00:00 | 10:16 | IDL | -   |   2 | 0.00 | SNl  | poll_s | tracker-miner-a | 0.20 | 56.60 |
| 2031 | 2031 | 00:00:00 | 10:17 | TS  | 0   |   2 | 0.00 | Sl   | poll_s | mission-control | 0.20 | 56.80 |
| 2043 | 2043 | 00:00:00 | 10:17 | TS  | 0   |   1 | 0.00 | Ssl  | -      | udisksd         | 0.20 | 57.00 |
| 2070 | 2070 | 00:00:00 | 10:17 | TS  | 0   |   3 | 0.00 | Sl   | poll_s | gvfs-afc-volume | 0.20 | 57.20 |
|    1 |    1 | 00:00:01 | 10:15 | TS  | 0   |   2 | 0.00 | Ss   | -      | systemd         | 0.10 | 57.30 |
|  265 |  265 | 00:00:00 | 10:15 | TS  | 0   |   2 | 0.00 | Ss   | -      | systemd-journal | 0.10 | 57.40 |
|  280 |  280 | 00:00:00 | 10:15 | TS  | 0   |   3 | 0.00 | Ss   | -      | systemd-udevd   | 0.10 | 57.50 |
|  842 |  842 | 00:00:00 | 10:15 | TS  | 0   |   2 | 0.00 | Ssl  | -      | accounts-daemon | 0.10 | 57.60 |
|  863 |  863 | 00:00:00 | 10:15 | TS  | 0   |   0 | 0.00 | Ss   | -      | dbus-daemon     | 0.10 | 57.70 |
|  937 |  937 | 00:00:00 | 10:15 | TS  | 0   |   2 | 0.00 | SLsl | -      | lightdm         | 0.10 | 57.80 |
| 1080 | 1080 | 00:00:00 | 10:16 | TS  | 0   |   0 | 0.00 | Ss   | -      | wpa_supplicant  | 0.10 | 57.90 |
| 1103 | 1103 | 00:00:00 | 10:16 | TS  | 0   |   1 | 0.00 | S    | -      | dnsmasq         | 0.10 | 58.00 |
| 1373 | 1373 | 00:00:00 | 10:16 | TS  | 0   |   3 | 0.00 | Sl   | -      | lightdm         | 0.10 | 58.10 |
| 1506 | 1506 | 00:00:00 | 10:16 | TS  | 0   |   3 | 0.00 | Ss   | ep_pol | systemd         | 0.10 | 58.20 |
| 1513 | 1513 | 00:00:00 | 10:16 | TS  | 0   |   2 | 0.00 | Sl   | -      | gnome-keyring-d | 0.10 | 58.30 |
| 1515 | 1515 | 00:00:00 | 10:16 | TS  | 0   |   2 | 0.00 | Ss   | poll_s | upstart         | 0.10 | 58.40 |
| 1594 | 1594 | 00:00:00 | 10:16 | TS  | 0   |   1 | 0.00 | Ss   | ep_pol | dbus-daemon     | 0.10 | 58.50 |
| 1665 | 1665 | 00:00:00 | 10:16 | TS  | 0   |   0 | 0.00 | Sl   | poll_s | at-spi-bus-laun | 0.10 | 58.60 |
| 1670 | 1670 | 00:00:00 | 10:16 | TS  | 0   |   1 | 0.00 | S    | ep_pol | dbus-daemon     | 0.10 | 58.70 |
| 1673 | 1673 | 00:00:00 | 10:16 | TS  | 0   |   3 | 0.00 | Sl   | poll_s | at-spi2-registr | 0.10 | 58.80 |
| 1677 | 1677 | 00:00:00 | 10:16 | TS  | 0   |   3 | 0.00 | Sl   | poll_s | gvfsd           | 0.10 | 58.90 |
| 1682 | 1682 | 00:00:00 | 10:16 | TS  | 0   |   1 | 0.00 | Sl   | futex_ | gvfsd-fuse      | 0.10 | 59.00 |
| 1740 | 1740 | 00:00:00 | 10:16 | TS  | 0   |   3 | 0.00 | Ssl  | poll_s | indicator-messa | 0.10 | 59.10 |
| 1741 | 1741 | 00:00:00 | 10:16 | TS  | 0   |   3 | 0.00 | Ssl  | poll_s | indicator-bluet | 0.10 | 59.20 |
| 1748 | 1748 | 00:00:00 | 10:16 | TS  | 0   |   1 | 0.00 | Ssl  | poll_s | indicator-sessi | 0.10 | 59.30 |
| 1786 | 1786 | 00:00:00 | 10:16 | TS  | 0   |   1 | 0.00 | Sl   | poll_s | dconf-service   | 0.10 | 59.40 |
| 2029 | 2029 | 00:00:00 | 10:17 | TS  | 0   |   2 | 0.00 | Sl   | poll_s | goa-identity-se | 0.10 | 59.50 |
| 2040 | 2040 | 00:00:00 | 10:17 | TS  | 0   |   2 | 0.00 | Sl   | poll_s | gvfs-udisks2-vo | 0.10 | 59.60 |
| 2059 | 2059 | 00:00:00 | 10:17 | TS  | 0   |   2 | 0.00 | Sl   | poll_s | gvfs-gphoto2-vo | 0.10 | 59.70 |
| 2076 | 2076 | 00:00:00 | 10:17 | TS  | 0   |   3 | 0.00 | Sl   | poll_s | gvfs-goa-volume | 0.10 | 59.80 |
| 2081 | 2081 | 00:00:00 | 10:17 | TS  | 0   |   1 | 0.00 | Sl   | poll_s | gvfs-mtp-volume | 0.10 | 59.90 |
| 2093 | 2093 | 00:00:00 | 10:17 | TS  | 0   |   0 | 0.00 | Sl   | poll_s | gvfsd-trash     | 0.10 | 60.00 |
| 2100 | 2100 | 00:00:00 | 10:17 | TS  | 0   |   3 | 0.00 | Sl   | poll_s | gvfsd-burn      | 0.10 | 60.10 |
| 2121 | 2121 | 00:00:00 | 10:17 | TS  | 0   |   1 | 0.00 | Sl   | poll_s | zeitgeist-daemo | 0.10 | 60.20 |
| 2293 | 2293 | 00:00:00 | 10:18 | TS  | 0   |   1 | 0.00 | Ss   | wait   | bash            | 0.10 | 60.30 |
| 2318 | 2318 | 00:00:00 | 10:18 | TS  | 0   |   2 | 0.00 | Ss   | wait   | bash            | 0.10 | 60.40 |
| 2332 | 2332 | 00:00:00 | 10:18 | TS  | 0   |   3 | 0.00 | Sl   | poll_s | deja-dup-monito | 0.10 | 60.50 |
| 2340 | 2340 | 00:00:00 | 10:19 | TS  | 0   |   0 | 0.00 | S+   | wait_w | mysql           | 0.10 | 60.60 |
| . . .

```

'free' differs again at 38%

```
fr@hatchbox-2:~$ free
              total        used        free      shared  buff/cache   available
Mem:        3910876     1487532      742412      439028     1680932     1713988
Swap:       4064252           0     4064252

```

One more observation: It was a redone online magazine that really wreaked havoc, or triggered it. I believe it now requires the Flash Reader and I seem to vaguely remember a cautionary notice about the Flash Reader. I googled the topic and found that Shockwave has been causing some pain. But isn't Shockwave for movies? A magazine isn't a movie. As a subscriber I called the editor complaining and am now waiting for a response.

Regards

Frederic

---

### Post by again? on 2018-02-13
jedit being a java appplication uses a lot of memory.
My pic shows jedit using 378mb just opening it and firefox using 1.1gb with 4 tabs open.
[ATTACH=CONFIG]278515[/ATTACH]
Notice the "Web Content" entries in system monitor. These are your firefox tabs.
This command monitors your total firefox mem usage.
```
watch -d -n1 'ps -aux|awk '\''BEGIN{x=0;y=0;} /[f]irefox/{x=x+$4;y=y+$6} END{print(x"% Memory and "((y/1024)/1024)" Memory Size(GB)");}'\'''
```

At bootup in 16.04 Unity these are my top memory use applications. I chose "All Process" from the hamburger menu at top right.
The resource tab shows 25% or 1gb in total use although conky shows 800mb in use.
[ATTACH=CONFIG]278516[/ATTACH]

---

### Post by ffrr on 2018-02-15
Head-scratching time again. 'clamd' was back!. I thought I had apt-get  removed it. There it was, leading the pack of memory hogs. I took a  screenshot like yours, meaning to insert it here. Alas, the file name prompt asks for a url. Tried all variations I could think of: file name, file://filename . . . All it did was put what I wrote  between the [IMG] tags. Anyway, the matter was to whack clamd again.
  ```
fr@hatchbox-2:~$ ps -e | grep clam
  824 ?        00:00:24 clamd
  871 ?        00:00:03 freshclam
fr@hatchbox-2:~$ sudo kill 9 871
[sudo] password for fr: 
fr@hatchbox-2:~$ sudo kill 9 824
fr@hatchbox-2:~$ sudo apt-get remove freshclam
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package freshclam
fr@hatchbox-2:~$ sudo apt-get remove clamd
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package 'clamd' is not installed, so not removed
0 upgraded, 0 newly installed, 0 to remove and 31 not upgraded.

```
It is there and also is not there! Reconciling contradictions overexerts my modest mental capabilities.  
```
fr@hatchbox-2:~$ sudo find / -iwholename '*clam*' > /tmp/clam
[sudo] password for fr: 
find: ‘/run/user/1000/gvfs’: Permission denied

fr@hatchbox-2:~$ wc  /tmp/clam
  249   249 10274 /tmp/clam

fr@hatchbox-2:~$ grep bin /tmp/clam
/etc/apparmor.d/cache/usr.sbin.clamd
/etc/apparmor.d/cache/usr.bin.freshclam
/etc/apparmor.d/usr.sbin.clamd
/etc/apparmor.d/usr.bin.freshclam
/etc/apparmor.d/local/usr.sbin.clamd
/etc/apparmor.d/local/usr.bin.freshclam
/usr/sbin/clamd
/usr/bin/freshclam
/usr/bin/clamdtop
/usr/bin/clamconf

```
Quite a line-up for a removed package! What if I deleted all 249 files 'find' collected? Is there a good reason to not do that (after weeding out false matches, of course)? What next? I do need a virus police.

I use Jedit for its block-marking/editing features. I should look for an alternative. 

Your command 'watch . . .' is really cool

Frederic

---

### Post by again? on 2018-02-15
> **ffrr said:**
> I took a  screenshot like yours, meaning to insert it here. Alas, the file name prompt asks for a url. Tried all variations I could think of: file name, file://filename . . . All it did was put what I wrote  between the [IMG] tags.
Reply in advanced mode and hit the paper clip to browse your computer for images. Once selected hit the Upload button in the attachment window.
You can then insert images anywhere in your post by clicking on the arrow to the right of the paperclip and then the attachment.
[ATTACH=CONFIG]278537[/ATTACH]

Any attached images not inserted will be displayed at the bottom of your post 
in an " Attached Thumbnails" box.
As for clamd I would search in synaptic for "clam" and completely remove any relevant packages and then reboot.

---

### Post by ffrr on 2018-02-16
guber2

Thanks for the help. I removed 'clam' with synaptic. I now have to find an other virus scanner. 

Let's close this thread. It has been helpful in short-listing symptoms, as initially I had no idea where to start. Next I shall spend some time googling and scouring this forum. I believe to have isolated the relevant symptom. There must be something wrong with swap management. When RAM is full, response times become intolerably long (half a minute, one minute...), irrespective of free swap capacity. It will swap very slowly at the pace of the sluggish response. That's the way yesterday's session ended with Swap at only around ten percent used. When earlier that day I opened the session, I got an error message: "Ubuntu 16.04 LTS has experienced an internal error". I have seen this message many times in the past. It doesn't say what it means, nor does it suggest any action other than closing the message window. One should perhaps restart, which I never did and most of the time no further trouble occurred. The message details look arcane to me, except the list of obsolete packages, the only item I know how to act on. This last time, there was no such list. The topmost item of the details was a file name: /usr/bin/gnome-control-center.

So I shall search forums and google the internet for 'internal error' and find out more about 'gnome-control-center', and if that comes out to no avail, I'll start a new thread with a title more to the point.

Thanks all

Frederic

---

