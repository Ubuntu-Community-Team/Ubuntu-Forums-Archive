---
title: "[SOLVED] Newb needs help"
date: 2007-11-17
forum: General Help
---

### Post by dudeirock on 2007-11-17
I'm rather new to the world of Linux, so take it easy and bear with me. I'm running Ubuntu Dapper 6.06 on a failry decent system, so I'll post this first:

CPU - Pentium 4 2.793 GHz
Mem - 1.792 GB
Video - 128MB GeForce FX 5200
HDD - 250 GB (doesnt matter, but oh well)
If you're wondering about bandwidth after you finish reading -           [http://www.speedtest.net/result/203014111.png](http://www.speedtest.net/result/203014111.png)

fairly recent install of Dapper, ~2 weeks or so. At first, this system ran with impeccable performance. All apps and web pages opened in the blink of an eye. But, now it is the complete opposite. Running very few applications (currently Amarok, Firefox, and GAIM). I clear cache and reboot the system on a regular basis. I'm just so new to Linux I don't know how to tweak it and no one on these forms have the problem I'm having with the comparable hardware. This problem usually occurs on a system with 256mb RAM or a 1 GHZ CPU. 

ALL, yes all, apps take way to long to open, and it gets worse day by day, no matter how often I reboot. I was trying to peruse through google maps, and I can't even view the maps without having to buffer forever. they take so long to load. A simple hyperlink on a web page takes 5-10 seconds to load, Even just trying to open up a new tab in Firefox takes 5-10 seconds. Amarok takes about 5-10 seconds to skip to the next song. I have a lot of things that take 5-10 seconds in case you haven't noticed the trend.

Here is the output of 'free -m' console command after 4 hour uptime:

matt@######:~$ free -m
                  total        used     free     shared    buffers     cached
Mem:          1773        889       883     0            40            519
-/+ buffers/cache:       329       1443
Swap:         4996         0          4996


'TOP' Command:

Tasks:  98 total,   1 running,  96 sleeping,   0 stopped,   1 zombie
Cpu(s):  7.3% us,  0.3% sy,  0.0% ni, 92.3% id,  0.0% wa,  0.0% hi,  0.0% si
Mem:   1815868k total,   909416k used,   906452k free,    40868k buffers
Swap:  5116660k total,        0k used,  5116660k free,   531044k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND
10735 matt      15   0  132m  41m  25m S  5.0  2.3   2:45.62 amarokapp
 4420 root      15   0  205m  54m 7840 S  2.3  3.1   9:01.36 Xorg
11029 matt      15   0  212m 123m  24m S  0.3  7.0   2:04.32 firefox-bin
11293 matt      15   0 46204  13m 8848 S  0.3  0.8   0:01.48 gnome-terminal
    1 root      16   0  1564  528  460 S  0.0  0.0   0:01.25 init
    2 root      34  19     0    0    0 S  0.0  0.0   0:00.00 ksoftirqd/0
    3 root      RT   0     0    0    0 S  0.0  0.0   0:00.00 watchdog/0
    4 root      10  -5     0    0    0 S  0.0  0.0   0:00.20 events/0
    5 root      10  -5     0    0    0 S  0.0  0.0   0:00.00 khelper
    6 root      10  -5     0    0    0 S  0.0  0.0   0:00.00 kthread

Any ideas or tips? Please!!!!

---

### Post by forestpixie on 2007-11-17
This might help , but then again...

I have seen in the 6 months I've been here a few threads where the lack of a restricted driver for a graphics card, or it not being installed quite right, has caused a general slow down - have you got the driver enabled?

Perhaps you'd be better off with Feisty or Gutsy.

Also it seems that you have nearly 5Gb of swap - don't think that'd cause a problem, but I'm interested to know why.

---

### Post by knutschr on 2007-11-17
```

sudo apt-get remove xserver-xgl

```

I don't know why xserver-xgl is such a disaster in many machines, but it often certainly helps to remove it.

---

### Post by dudeirock on 2007-11-17
> **forestpixie said:**
> This might help , but then again...

I have seen in the 6 months I've been here a few threads where the lack of a restricted driver for a graphics card, or it not being installed quite right, has caused a general slow down - have you got the driver enabled?

Perhaps you'd be better off with Feisty or Gutsy.

Also it seems that you have nearly 5Gb of swap - don't think that'd cause a problem, but I'm interested to know why.

First off, thanks for the quick response.......After looking around for the last hour, I can't seem to locate a more up to date driver than what I already have, and mine is a pretty old version. This would be a good time to upgrade to Gutsy (might as well go to the newest). Not sure if that will rid me of this issue, or if it will re-occur, but I'll at least be up to speed in regards to the OS.

About the swap.... During the install of Ubuntu I figured I had the disk space to spare so I just picked 5GB for the swap space. Is that bad? I know what swap is, but wasn't sure if there was such a thing as too much.

---

### Post by forestpixie on 2007-11-17
well I can't imagine it'll ever get used so it's a bit of a waste of space - if you've got 32bit motherboard etc - you're only going to be able to use 4Gb at the most and that includes the physical RAM and you've got 1.8 of that - ~I'd make it 1Gb of swap myself - I have 1 of each and rarely use more than 100Mb of the swap.

---

### Post by mike555 on 2007-11-17
I also have the 5200 , you might need to install "envy " to get the right drivers for it ...... ( the built-in restricted drivers thing didn't work for me )  if you can't get a GUI , you can install it (by command line) .

---

### Post by dudeirock on 2007-11-17
Issue solved. I gave Envy a try before upgrading the OS and that seems to have done the trick. I'll probably update the OS sometime down the road. 

Thanks everybody

---

