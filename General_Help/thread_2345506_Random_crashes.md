---
title: "Random crashes"
date: 2016-12-04
forum: General Help
---

### Post by eduardoflsantos on 2016-12-04
Hi,

My Ubuntu 16.04 is crashing all the time. 3 or 4 times a day, sometimes more. I've lost count how many time it crashed today. 

The computer just freezes. It freezes when I'm playing a game, or when I'm just browsing the web, so I can't figure out what exactly causes the crash/freeze. It seems random, but I'm not sure.

I changed my graphic card this weekend and the problem continued, so I know the problem isn't there.

I have a dual-boot with Windows 7, where I have no crashes (I almost don't use it anymore, but this weekend I spent several hours there playing a game, with no crashes at all) . This Windows installation is on a different drive though, so I figured that the problem must come from the Linux (6 month old) SSD. But the SMART diagnosis from the Ubuntu says the SSD is just fine.

Can you help me figure this out?

Would you say it's a hardware problem, or a software problem?

Thank you.

---

### Post by cariboo on 2016-12-05
It would help if you let us know what type of hardware you are using. Install inxi if you haven't got it install:

```
sudo apt-get install inxi
```

then run the following command:

```
inxi -b
```

copy and paste the output in your next post. It should look something like this:

```
 inxi -b
System:    Host: alexis Kernel: 4.9.0-3-generic x86_64 (64 bit)
           Desktop: Unity 7.5.0
           Distro: Ubuntu Zesty Zapus (development branch)
Machine:   Device: laptop System: TOSHIBA product: Satellite C50-B v: PSCMLC-02Y00T
           Mobo: TOSHIBA model: ZBWAA v: 1.00
           UEFI: TOSHIBA v: 1.70 date: 12/11/2014
Battery    BAT1: charge: 20.1 Wh 100.0% condition: 20.1/22.0 Wh (91%)
CPU:       Quad core Intel Pentium N3530 (-MCP-) speed/max: 809/2582 MHz
Graphics:  Card: Intel Atom Processor Z36xxx/Z37xxx Series Graphics & Display
           Display Server: X.Org 1.18.4 drivers: (unloaded: fbdev,vesa)
           Resolution: 1366x768@60.00hz
           GLX Renderer: Mesa DRI Intel Bay Trail GLX Version: 3.0 Mesa 13.0.2
Network:   Card-1: Realtek RTL8101/2/6E PCI Express Fast/Gigabit Ethernet controller
           driver: r8169
           Card-2: Qualcomm Atheros AR9485 Wireless Network Adapter
           driver: ath9k
Drives:    HDD Total Size: 750.2GB (19.9% used)
Info:      Processes: 270 Uptime: 2 days Memory: 2109.6/3838.0MB
           Client: Shell (bash) inxi: 2.3.4 
```

---

### Post by eduardoflsantos on 2016-12-05
Hi,

Here it is

```
System:    Host: eduardo-desktop Kernel: 4.4.0-51-generic x86_64 (64 bit)
           Desktop: Unity 7.4.0  Distro: Ubuntu 16.04 xenial
Machine:   Mobo: ASRock model: FM2A88M-HD+
           Bios: American Megatrends v: P2.60 date: 08/01/2014
CPU:       Quad core AMD A10-7850K Radeon R7 12 Compute Cores 4C+8G (-MCP-)
           speed/max: 1700/3700 MHz
Graphics:  Card: NVIDIA GM206 [GeForce GTX 960]
           Display Server: X.Org 1.18.4 drivers: nvidia (unloaded: fbdev,vesa,nouveau)
           Resolution: 1920x1080@60.00hz
           GLX Renderer: GeForce GTX 960/PCIe/SSE2
           GLX Version: 4.5.0 NVIDIA 367.57
Network:   Card: Realtek RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
           driver: r8169
Drives:    HDD Total Size: 1250.3GB (16.3% used)
Info:      Processes: 230 Uptime: 5 min Memory: 1832.8/7905.6MB
           Client: Shell (bash) inxi: 2.2.35 
```


Thank you

---

### Post by BlueAZ on 2016-12-05
Hi,   I believe this is a memory problem in 16.04, especially on 64-bit systems.  See Launchpad: 
[h=1][SIZE=3]     Ubuntu 16.04 Unity desktop uses much more ram      [/SIZE][SIZE=3]Bug #1572801[/SIZE][/h]
Many people are having these problems, due to something gobbling up our RAM.  But I see no real solutions as yet.  I hope someone who's qualified to solve such a problem comes up with a workable answer for us!!

---

### Post by eduardoflsantos on 2016-12-05
> **BlueAZ said:**
> Hi,   I believe this is a memory problem in 16.04, especially on 64-bit systems.  See Launchpad: 
**[SIZE=3]     Ubuntu 16.04 Unity desktop uses much more ram      [/SIZE][SIZE=3]Bug #1572801[/SIZE]**


Many people are having these problems, due to something gobbling up our RAM.  But I see no real solutions as yet.  I hope someone who's qualified to solve such a problem comes up with a workable answer for us!!

Maybe it's time to try OpenSuse, then :P . Any way I can confirm your suspicions? Keep an eye on Ram usage, maybe?


@all
Ubuntu's SSD health report from HDSentinel: 

```
    Health  . . . . . . . . . . . . . . . . . . . . . : #################### 100 % (Excellent)
    Performance . . . . . . . . . . . . . . . . . . . : #################### 100 % (Excellent)

    The status of the solid state disk is PERFECT. Problematic or weak sectors were not found.
      No actions needed. 

```
I think we can scratch the hard drive problem hypothesis.

Oddly, I've been using the PC for over 2h and no freezes at all today. This seems so random!

---

### Post by karl96 on 2016-12-05
Might just be Firefox being naughty. Sometimes it seg faults on me but it's an upstream issue and pretty much the same on every distro that ships it. Low performance can be caused by lots of things, but excessive RAM usage and buggy video drivers are likely the cause. It's a bit late where I am and the only solution I can think of is to run it from a terminal, it'll hopefully tell you why it crashed, and if not you should be able to debug it. Run ```
top
``` see what is using so much.

---

### Post by BlueAZ on 2016-12-05
Eduardo,  I use Indicator-Multiload to monitor system loads in real time.  It works great!  It lives in the top bar with other indicators and shows usage levels in graphic form.  You can choose which components you want to monitor and even what color to show!
And I find it easier than 'top' to use System Monitor, which also lists the individual processes and how much cpu and ram they are each using.
Good luck!

---

### Post by eduardoflsantos on 2016-12-05
No resets today, at all. Go figure...

Ok, I'll keep an eye on Firefox.

btw, I checked the logs (which are like chinese to me),and most of yesterdays information was already gone, but I found something that mentions a crash. "GPU has fallen off the bus"

[http://pastebin.com/fzpbARLK](http://pastebin.com/fzpbARLK)

---

### Post by eduardoflsantos on 2016-12-06
Just happened again.

It's some problem with the GPU driver, I believe...

```
Dec  6 17:49:03 eduardo-desktop kernel: [ 8659.726052] NVRM: GPU at PCI:0000:01:00: GPU-c4a80165-86e4-bfbb-ecfa-1d81a70b138a
Dec  6 17:49:03 eduardo-desktop kernel: [ 8659.726062] NVRM: Xid (PCI:0000:01:00): 79, GPU has fallen off the bus.
Dec  6 17:49:03 eduardo-desktop kernel: [ 8659.726062] 
Dec  6 17:49:03 eduardo-desktop kernel: [ 8659.726067] NVRM: GPU at 0000:01:00.0 has fallen off the bus.
Dec  6 17:49:03 eduardo-desktop kernel: [ 8659.726078] NVRM: A GPU crash dump has been created. If possible, please run
Dec  6 17:49:03 eduardo-desktop kernel: [ 8659.726078] NVRM: nvidia-bug-report.sh as root to collect this data before
Dec  6 17:49:03 eduardo-desktop kernel: [ 8659.726078] NVRM: the NVIDIA kernel module is unloaded.
Dec  6 17:49:04 eduardo-desktop gnome-session[1771]: [2016-12-06T17:49:04] [ERR] nvctrl: Failed to retrieve measure of type 10201 for NVIDIA GPU 0
Dec  6 17:49:04 eduardo-desktop gnome-session[1771]: [2016-12-06T17:49:04] [ERR] nvctrl: Failed to retrieve measure of type 50204 for NVIDIA GPU 0
Dec  6 17:49:04 eduardo-desktop gnome-session[1771]: [2016-12-06T17:49:04] [ERR] nvctrl: Failed to retrieve measure of type 90204 for NVIDIA GPU 0
Dec  6 17:49:04 eduardo-desktop gnome-session[1771]: [2016-12-06T17:49:04] [ERR] nvctrl: Failed to retrieve measure of type 210204 for NVIDIA GPU 0
Dec  6 17:49:04 eduardo-desktop gnome-session[1771]: [2016-12-06T17:49:04] [ERR] nvctrl: Failed to retrieve measure of type 110204 for NVIDIA GPU 0
Dec  6 17:49:04 eduardo-desktop gnome-session[1771]: [2016-12-06T17:49:04] [ERR] nvctrl: Failed to retrieve measure of type 20202 for NVIDIA GPU 0
Dec  6 17:49:04 eduardo-desktop gnome-session[1771]: [2016-12-06T17:49:04] [ERR] nvctrl: Failed to retrieve measure of type 20204 for NVIDIA GPU 0
```

Any advice?

---

### Post by karl96 on 2016-12-06
Three things;

Firstly, which GPU driver are you using? Try switching to Nouveau, NVIDIA drivers are a pain.
Secondly, try switching the GPU into a different slot, or giving it a clean.
Thirdly, you can try analysing the GPU crash dump with the GNU Debugger ```
 apt install gdb 
```

Then ```
gdb program core
``` (edit as needed, it should dump a .core file when crashing)
Then once in gdb do ```
 where 
``` It'll tell you where the program crashed.

Alternatively, if the issue does turn out to be memory related you can use a profiler like valgrind.

---

### Post by eduardoflsantos on 2016-12-06
I spend quite some time playing videogames, so I'd prefer to use Nvidia drivers (if they stop doing this, anyway).

I'm sorry, which program should I debbug? You lost me in here:

```
 gdb program core
```

Thanks

PS: Happened 2 times in under 10 minutes. This is so annoying.

---

