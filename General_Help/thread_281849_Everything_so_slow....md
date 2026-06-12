---
title: "Everything so slow..."
date: 2006-10-21
forum: General Help
---

### Post by conjurer on 2006-10-21
Hi I've been running Ubuntu for a year now and everything was pretty smooth.

Recently however, the system has become much slower than before. For example, I click on firefox, and it takes several minutes for it to start running. Maximizing and minimizing windows also causes some major lags. It seems that anything that involves graphics is lagging horribly.

If I do glxgears -printfps I get like 800.000 FPS (the wheels are hardly moving at all...) even though I did the same thing a year ago and the wheels were turning super fast and I remember having like 2000.000 FPS or something.

I'm not sure but I think this all started to happen after I upgraded to Dapper. I think it has something to do with my nvidia driver since I remember having to re-install it when upgrading to Dapper. I don't think its a memory leak since it doesn't make any difference whether I restart the computer or not. The hardware is fine and doesn't seem to be overheating.

I have a 1GHz Intel Pentium III processor, 512 MB memory and a NVIDIA GeForce 2 MX/MX 400 graphic card. Can anyone help me?

---

### Post by conjurer on 2006-10-21
Oh and I don't know if it helps but,

Here's what I get when I type 'free' in the terminal:

             total       used       free     shared    buffers     cached
Mem:        515920     406840     109080          0      14836     205316
-/+ buffers/cache:     186688     329232
Swap:      1510068          0    1510068


Here's what I get when I type 'top' in the terminal:

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND
 4303 root      15   0 47704  32m 8932 S 15.0  6.4   2:49.22 Xorg
 6473 bchen     15   0 40788  15m 9700 S  6.6  3.0   0:04.37 gnome-terminal
 4946 bchen     15   0  165m  70m  17m S  5.0 14.1   4:10.90 firefox-bin
 4852 bchen     15   0 40372  21m  11m S  1.7  4.3   0:22.31 gnome-panel
 4846 bchen     15   0 14892 8776 5984 S  1.0  1.7   0:11.44 metacity
 4918 bchen     15   0 29056 9068 6672 S  0.3  1.8   0:00.75 gnome-netstatus
 4933 bchen     16   0 14612 2776 1860 S  0.3  0.5   0:02.77 gnome-screensav
 6508 bchen     16   0  2192 1108  856 R  0.3  0.2   0:00.65 top
    1 root      16   0  1568  528  460 S  0.0  0.1   0:02.07 init
    2 root      34  19     0    0    0 S  0.0  0.0   0:00.00 ksoftirqd/0
    3 root      RT   0     0    0    0 S  0.0  0.0   0:00.00 watchdog/0
    4 root      10  -5     0    0    0 S  0.0  0.0   0:00.11 events/0
    5 root      10  -5     0    0    0 S  0.0  0.0   0:00.00 khelper
    6 root      10  -5     0    0    0 S  0.0  0.0   0:00.00 kthread
    8 root      10  -5     0    0    0 S  0.0  0.0   0:00.04 kblockd/0
    9 root      20  -5     0    0    0 S  0.0  0.0   0:00.00 kacpid
  101 root      20   0     0    0    0 S  0.0  0.0   0:00.00 pdflush
  102 root      15   0     0    0    0 S  0.0  0.0   0:00.00 pdflush
  104 root      17  -5     0    0    0 S  0.0  0.0   0:00.00 aio/0
  103 root      25   0     0    0    0 S  0.0  0.0   0:00.00 kswapd0
  691 root      10  -5     0    0    0 S  0.0  0.0   0:00.00 kseriod
 1814 root      10  -5     0    0    0 S  0.0  0.0   0:00.00 khubd
 1890 root      15   0     0    0    0 S  0.0  0.0   0:00.12 kjournald
 2123 root      12  -4  2428  920  368 S  0.0  0.2   0:00.71 udevd
 2914 root      20   0     0    0    0 S  0.0  0.0   0:00.00 shpchpd_event
 3051 root      11  -5     0    0    0 S  0.0  0.0   0:00.00 kgameportd
 3765 root      16   0  2156 1200  644 S  0.0  0.2   0:00.01 acpid
 3858 syslog    16   0  1768  672  548 S  0.0  0.1   0:00.03 syslogd
 3884 root      16   0  1676  492  412 S  0.0  0.1   0:00.05 dd
 3886 klog      17   0  2424 1352  388 S  0.0  0.3   0:00.12 klogd
 3905 messageb  16   0  2188  860  668 S  0.0  0.2   0:00.10 dbus-daemon
 3920 haldaemo  16   0  6760 5356 1556 S  0.0  1.0   0:01.98 hald
 3921 root      19   0  2720  980  836 S  0.0  0.2   0:00.06 hald-runner
 3926 haldaemo  17   0  2004  792  696 S  0.0  0.2   0:00.00 hald-addon-acpi
 3976 haldaemo  16   0  2000  788  692 S  0.0  0.2   0:00.12 hald-addon-keyb
 3987 haldaemo  16   0  2008  816  716 S  0.0  0.2   0:00.26 hald-addon-stor
 3988 haldaemo  16   0  2004  816  716 S  0.0  0.2   0:00.31 hald-addon-stor
 3990 haldaemo  16   0  2008  816  716 S  0.0  0.2   0:00.07 hald-addon-stor
 3991 haldaemo  16   0  2008  816  716 S  0.0  0.2   0:00.08 hald-addon-stor
 4012 avahi     16   0  2536 1308 1128 S  0.0  0.3   0:00.01 avahi-daemon
 4013 avahi     22   0  2536  432  284 S  0.0  0.1   0:00.00 avahi-daemon
 4269 root      15   0 10908 1792 1212 S  0.0  0.3   0:00.00 gdm
 4292 root      16   0 11260 2556 1912 S  0.0  0.5   0:00.02 gdm
 4312 hplip     16   0 12872  920  696 S  0.0  0.2   0:00.00 hpiod
 4319 hplip     15   0  9416 4668 1092 S  0.0  0.9   0:00.02 python
 4366 cupsys    16   0  4208 1800 1312 S  0.0  0.3   0:00.05 cupsd

---

### Post by MWAAAHAAA on 2006-10-21
Have you recently changed your display manager?

---

### Post by conjurer on 2006-10-21
I don't think I changed my display manager because, well, I don't really know what it is... (so maybe I changed it inadvertently?)

---

### Post by MWAAAHAAA on 2006-10-22
GNOME is the standard window manager for Ubuntu, have you always used thsi one, or did you ever use another one? If you changed from a lightweight window manager to a heavier one, such as GNOME or KDE, then that might explain your problems.

---

### Post by conjurer on 2006-10-22
I have always been using Gnome as my display manager. I'm pretty sure I didn't change it.

---

### Post by Kateikyoushi on 2006-10-22
Did you upgrade the kernel recently with auto updater ?

---

### Post by conjurer on 2006-10-22
I'm not sure if it was with auto-updater, but when I upgraded to dapper (using apt-get update/upgrade/dist-upgrade) I think it upgraded the kernel too.

---

### Post by Kateikyoushi on 2006-10-22
What is the output of this command ?
Replace "hda" with the hard drive ubuntu is installed on.

```
sudo hdparm -i /dev/hda
```

---

### Post by conjurer on 2006-10-22
This is what I get:

~$ sudo hdparm -i /dev/hda

/dev/hda:

 Model=HDS722580VLAT20, FwRev=V32OA6MA, SerialNo=VN621ECBEJJS6D
 Config={ HardSect NotMFM HdSw>15uSec Fixed DTR>10Mbs }
 RawCHS=16383/16/63, TrkSize=0, SectSize=0, ECCbytes=52
 BuffType=DualPortCache, BuffSize=1794kB, MaxMultSect=16, MultSect=off
 CurCHS=16383/16/63, CurSects=16514064, LBA=yes, LBAsects=160836480
 IORDY=on/off, tPIO={min:240,w/IORDY:120}, tDMA={min:120,rec:120}
 PIO modes:  pio0 pio1 pio2 pio3 pio4
 DMA modes:  mdma0 mdma1 mdma2
 UDMA modes: udma0 udma1 udma2 udma3 udma4 *udma5
 AdvancedPM=yes: disabled (255) WriteCache=enabled
 Drive conforms to: ATA/ATAPI-6 T13 1410D revision 3a:  ATA/ATAPI-2 ATA/ATAPI-3 ATA/ATAPI-4 ATA/ATAPI-5 ATA/ATAPI-6

 * signifies the current active mode

---

### Post by podunk on 2006-10-22
Try this
```
glxinfo
```

You'll get a bunch of gibberish but at the top there should be a line:
direct rendering: Yes

if it says
direct rendering: no
then something is wrong with your video driver. In my computer xorg (the video and desktop control sort of) only uses around 2 to 3% of the resources when it's sitting on terminal.

---

### Post by conjurer on 2006-10-25
It says direct rendering: yes

bummer...

---

### Post by conjurer on 2006-10-28
*bump

---

### Post by fazza on 2006-10-29
useful, but what do i do if it says no?
cheers if you can help... (still on dapper)

---

### Post by conjurer on 2006-11-02
Anyone?

---

### Post by podunk on 2006-11-02
I don't know very much about Linux. This is the reason I'm so good and fast at backing my data up and reinstalling. :-D

About a month or so ago there was a kernel update that had an error in it. It was fixed in just a few hours - but those of us who did the update has stuff broken all over the place. It seemed particularly sever for folks with ATI video (like me!).

I spent several hours trying to fix stuff. I decided that I could do a new set up much faster than this and started over. I hate to say stuff like that - but everything you've posted has been OK, no hard drive problem, video drivers enabled, it's just your xorg and CPU useage looks out of line for some reason, and everything is slow.

I only know to check for stupid stuff so far. Like - do I have the right kernel installed for my CPU? 
```
uname -r
``` (my first set up I put the AMD 64 on a 32 bit processor for some reason)

In desperation I'd likely try booting up with one of the older kernels listed in my grub boot up menu to see if it was any better. I have an ATI card so I would type
```
fglrxinfo
``` to make sure the ATI string was returned instead of Mesa.

But when all that failed I'd set the sucker back up from my Live DVD. Hate to say crap like that, I know it's frustrating.

Hey Fazza, if you get direct rendering No it means you either have a very old card with no 3D capabilities or your video driver is not installed properly.

---

