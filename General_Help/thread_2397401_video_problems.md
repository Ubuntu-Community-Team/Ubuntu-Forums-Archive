---
title: "video problems"
date: 2018-07-29
forum: General Help
---

### Post by hmiersch on 2018-07-29
hi.  i recently bought a new computer and installed 18.04 on it. the problem is that when i try to watch youtube videos, sometimes firefox complains about video formats, and all i get is snow. i can't watch any live streams. do i need to install something?

---

### Post by mIk3_08 on 2018-07-29
let me check first the hardware you have in your machine by using the inxi command;
First we should have to install inxi in your system via terminal;
to open your terminal by pressing ctrl + alt + T
Then type the command;
```
sudo apt-get install inxi
```
when the installation is successful;
In your terminal type;
```
inxi -F
```
then copy and paste the result of inxi -F here in thread.

---

### Post by hmiersch on 2018-07-29
here is what inxi -F gives me: 
```

sysop@PC:~$ inxi -F
System:    Host: PC Kernel: 4.15.0-29-generic x86_64 bits: 64
           Desktop: Gnome 3.28.2 Distro: Ubuntu 18.04.1 LTS
Machine:   Device: desktop System: Gigabyte product: H110M-S2H serial: N/A
           Mobo: Gigabyte model: H110M-S2H-CF v: x.x serial: N/A
           UEFI: American Megatrends v: F24 date: 12/14/2017
Battery    hidpp__1: charge: 65% condition: NA/NA Wh
           hidpp__1: charge: 65% condition: NA/NA Wh
CPU:       Quad core Intel Core i7-7700 (-MT-MCP-) cache: 8192 KB
           clock speeds: max: 4200 MHz 1: 1505 MHz 2: 3580 MHz 3: 3525 MHz
           4: 3447 MHz 5: 3021 MHz 6: 3588 MHz 7: 3453 MHz 8: 3425 MHz
Graphics:  Card: Intel HD Graphics 630
           Display Server: x11 (X.Org 1.19.6 ) driver: i915
           Resolution: 1920x1080
           OpenGL: renderer: Mesa DRI Intel HD Graphics 630 (Kaby Lake GT2)
           version: 4.5 Mesa 18.0.5
Audio:     Card Intel Sunrise Point-H HD Audio driver: snd_hda_intel
           Sound: Advanced Linux Sound Architecture v: k4.15.0-29-generic
Network:   Card: Realtek RTL8111/8168/8411 PCIE Gigabit Ethernet Controller
           driver: r8169
           IF: enp1s0 state: up speed: 100 Mbps duplex: full
           mac: e0:d5:5e:66:56:61
Drives:    HDD Total Size: 4000.8GB (0.3% used)
           ID-1: /dev/sda model: TOSHIBA_DT01ACA1 size: 1000.2GB
           ID-2: USB /dev/sdb model: My_Passport_25E1 size: 1000.2GB
           ID-3: USB /dev/sdc model: External_USB_3.0 size: 2000.4GB
Partition: ID-1: / size: 914G used: 12G (2%) fs: ext4 dev: /dev/dm-1
           ID-2: /boot size: 705M used: 146M (23%) fs: ext4 dev: /dev/sda2
           ID-3: swap-1 size: 1.02GB used: 0.00GB (0%)
           fs: swap dev: /dev/dm-2
RAID:      No RAID devices: /proc/mdstat, md_mod kernel module present
Sensors:   System Temperatures: cpu: 29.8C mobo: 27.8C
           Fan Speeds (in rpm): cpu: N/A
Info:      Processes: 378 Uptime: 5 min Memory: 1559.4/15927.0MB
           Client: Shell (bash) inxi: 2.3.56 

```

---

### Post by mIk3_08 on 2018-07-29
try to visit this link. maybe it will help; [Click Here]("https://www.ubuntuupdates.org/package/core/bionic/main/base/intel-gpu-tools")
and [Click Here]("https://01.org/linuxgraphics/downloads/firmware")
[Linuxgraphics]("https://01.org/linuxgraphics")
some article maybe it will help; [Click Here]("https://forums.linuxmint.com/viewtopic.php?t=261389")
[ubuntuforums post]("https://ubuntuforums.org/showthread.php?t=2386282")
Read instructions carefully.

---

### Post by hmiersch on 2018-07-29
i installed intel-gpu-tools, but now what? how do i use it?

---

### Post by hmiersch on 2018-07-29
i'm beginning to think that we're barking up the wrong tree here. when i try to watch certain youtube videos, firefox says "your browser does not currently recognize any of the video formats available."

---

### Post by #&amp;thj^% on 2018-07-29
> **hmiersch said:**
> i installed intel-gpu-tools, but now what? how do i use it?

intel-gpu-tools. It is actually meant for debugging the Intel graphics driver
To use:
```
sudo intel_gpu_top
```
And I agree barking up the wrong tree.
And for live streams you would have to show us a link to the problem video to better help you.

---

### Post by Yellow Pasque on 2018-07-29
Is everything checked here?: [https://www.youtube.com/html5](https://www.youtube.com/html5)

---

### Post by hmiersch on 2018-07-29
I tried to play one of my videos using the videos app, and I had the same problem. But unlike Firefox, videos offered me a solution: install gstreamer.  I did that, and now it works. Problem solved. YouTube videos work now, even the ones that have been livestreamed. Haven't tried watching a stream live yet...

---

### Post by QIII on 2018-07-31
I have removed a number of posts with advice of dubious value and some others to maintain continuity.

Please.  If you have solid advice to offer you are free to provide it.  Otherwise, withhold comment.

Thanks.

---

