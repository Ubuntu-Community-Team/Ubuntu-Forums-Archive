---
title: "Multiple computers locking up with 20.04LTS"
date: 2021-10-02
forum: General Help
---

### Post by WB0HYQ on 2021-10-02
I posted a while back about one of my computers locking up unexpectedly. Now I have 4 of them doing the same thing. One is a desktop (homebuilt) and the other three are laptops (Two models of Asus and an HP). All four are running Ubuntu (or XUbuntu in one case). All of them were upgraded around the same time from 18.04LTS. Previously, they ran solidly with no freezing. Since upgraded, they freeze randomly.

I downloaded an ISO copy of MEMTest from the source and burned it to a bootable CD. It ran in all four computers overnight with no failures, yet within ten minutes of starting up, two laptops froze. One was at the purple logon screen, the other was playing an MP3 song using VLC. The odd thing was the music never stopped, but everything else locked up: mouse, keyboard, and even the power button (which was supposed to power down when pressed). Sometimes, the mouse keeps going. There are times (on the XUbuntu machine, where Cairo-Dock and the mouse were moving, but the dock didn't respond to a mouse click.

This cannot be a coincidence. There has to be some commonality other than running the same OS. It is driving me around the bend in its randomness. I can find no clues in any of the log files. Right up the instant of failure, it was business as normal.

Can someone suggest a different point of attack here?

Bill

---

### Post by dragonfly41 on 2021-10-03
> [COLOR=#000000]There has to be some commonality other than running the same OS. 

In your shoes I would come to the same conclusion. But I would then ask myself do these freezes all occur at the same time on all four systems? The only commonality I can think of is common power supply or LAN. Do they work separately (i.e. only one tested at a time)?  A process of elimination is needed to pin it down further.[/COLOR]

---

### Post by WB0HYQ on 2021-10-03
No. I usually run with only one or two of the computers powered up at any time. The time between boot and freeze may vary by as much as an hour or even a day, but eventually they will lock up. As far as connections go, they are all hooked into my house LAN either by wi-fi or hardwire. One of the laptops froze when I was at a book signing and totally away from my house. The other froze during a flight to San Francisco. The desktop runs 24/7/365. I did recently up the power supply from 450w to a 780w unit, but the freezes continued even after the upgrade.

I feel the freezes are due to something in the way Ubuntu handles RAM. If I am not doing anything, and the computer is simply idling on a desktop with the screensaver running, it tends not to freeze. When I run multiple apps, this increases the probability of a freeze. Note that I did run MEMTEST from a bootable CD and it found no flaws in RAM.

The desktop is a dual-boot machine, running Windows 7 and Ubuntu. Both have their own hard drives. When in Windows, I can do anything and everything I need to do with no failures. It will run for weeks and not freeze. It is something in Ubuntu that is causing the lockup.

One of the four, a laptop, was upgraded to Ubuntu 21.04 yesterday. I've left it running overnight and so far this morning it is still running. This will be my control computer. If it keeps running even after I subject it to some rather strenuous testing (such as running multiple VLC apps as well as opening many tabs (say, 10) in Firefox) to see if it will freeze.

Bill

---

### Post by dragonfly41 on 2021-10-03
Intuitively .. you may have setup swap on all systems.
I would next explore [that option]("https://www.reddit.com/r/archlinux/comments/k1bqj0/how_to_avoid_system_freeze_when_ram_is_full_swap/").
And/or increase RAM.
I usually suggest Stacer for monitoring processes/memory usage.
...

---

### Post by WB0HYQ on 2021-10-03
Every computer is at its maximum RAM size. The laptops especially.

I read through the linked thread, but the terminology simply overwhelmed me. It was over my head mostly. I will investigate the swap situation. Actually, swap is the only thing (memory-wise) that is handled differently than Windows (I think). Since the computers all tend to freeze when a lot is going on, the swap sounds like the likely culprit since the MEMTEST went smoothly. BTW, the MEMTEST offered by GRUB will fail almost immediately, locking up the computer so that only a hard power down will let me recover. Does it use swap?

Bill

---

### Post by Autodave on 2021-10-03
I have 11 computers, some desktops and some laptops, all running Xubuntu 20.04.  These range from very low powered machines to quite good ones.  The only difference between yours and mine is this: all of mine had clean installs of 20.04: no upgrading to 20.04.  None of mine have locked up at any time.

You may want to take one of those machines and boot it from a USB stick and run it off of that just to see if the problem persists.

I have been using Linux for about 13 years now and if there is one thing that I have learned it is this: don't waste time upgrading.  Back up what you need and do a clean install.

---

### Post by ajgreeny on 2021-10-03
What graphics hardware do you have in these machines?  Do they all use integrated graphic chips, eg in the CPU, or have you separate graphic cards that may need drivers to run properly?

It may be of interest if you could show us the output in all four machines of the command ```
inxi -Fzx
```
Please use **Code-Tags** for terminal output as it makes that output much more easily read and understood, formatting the text as seen in terminal, not as plain text when it is copied and pasted. See my signature below for a **How-to**

---

### Post by TheFu on 2021-10-03
Why guess. Just check the system log files.
**journalctl -b -1 **will show the prior boot and other hardware messages for that boot on each machine.  If you know about the time it happened, you can use a filter to get close or put in a range.

If all the system have the same type of GPU, that could be a common issue too. What is common for all the systems.  Lots of people use 18.04 and don't have any crashes or lockups. I generally go 2-4 weeks between reboots with my systems. No lockups during those times.

---

### Post by WB0HYQ on 2021-10-03
@Autodave: At one time or another all four machines were booted up with a Ubuntu Live DVD. Since the OS at that point is pretty bare bones, I haven't been able to get much running to try and overload it enough to cause the problem. It hasn't happened, but the time the systems were run off the DVD was rarely over a day. One of the laptops was a clean install of 20.04. In fact, the hard drive was a new one I had to format first.

@Aigreeny: I believe all four are running NVIDIA GPUs, but I will find out for sure. I used to run the NVIDIA drivers, but reverted all four to the default video drivers a while back. I will also run the command on the four and show the results. May have to wait for one of them as I loaned it out to a friend for his vacation trip and he won't be back for two weeks. He uses the Windows side, not the Linux.

@Thefu: I've run journalctl on all four machines. The results were inconclusive with none showing anything out of sorts. The log simply ends then begins with the next boot. When I ran 18.04 I could run for weeks without rebooting except for the ones commanded by the software updater. With no rebootable updates, the systems ran great. Perhaps my upgrade to 21.04 might do the trick. Time will tell.

Bill

---

### Post by WB0HYQ on 2021-10-03
Here's the first "inxi" report. This one is from my HP G60"

```

bill@bill-hp-g60:~$ inxi -Fzx
System:
  Kernel: 5.11.0-37-generic x86_64 bits: 64 compiler: gcc v: 10.2.1 
  Desktop: Xfce 4.16.0 Distro: Ubuntu 21.04 (Hirsute Hippo)        <<<----------------------this is the one I just upgraded from 20.04
Machine:
  Type: Laptop System: Hewlett-Packard product: HP G60 Notebook PC v: F.25 
  serial: <filter> 
  Mobo: Wistron model: 303C v: 08.45 serial: <filter> BIOS: Hewlett-Packard 
  v: F.25 date: 10/03/2008                                                       <<<<<-------- I realize this is ***way ***out of date. I have no idea how to get/install a newer BIOS.
Battery:
  ID-1: BAT0 charge: 81.1 Wh condition: 90.3/97.7 Wh (92%) 
  model: Hewlett-Packard Primary status: Discharging 
CPU:
  Info: Dual Core model: AMD Turion RM-70 bits: 64 type: MCP 
  arch: Turion X2 Ultra rev: 1 L2 cache: 1024 KiB 
  flags: lm nx pae sse sse2 sse3 svm bogomips: 7999 
  Speed: 500 MHz min/max: 500/2000 MHz Core speeds (MHz): 1: 500 2: 500     <<<<<-------------- I'd love to figure out how to increase this speed.
Graphics:
  Device-1: NVIDIA C77 [GeForce 8200M G] vendor: Hewlett-Packard 
  driver: nouveau v: kernel bus ID: 02:00.0                                                <<<<<-------- NVIDIA card, but with nouveau driver.
  Device-2: Chicony Webcam type: USB driver: uvcvideo bus ID: 2-2:2 
  Display: x11 server: X.Org 1.20.11 driver: loaded: modesetting 
  unloaded: fbdev,vesa resolution: 1366x768~60Hz 
  OpenGL: renderer: NVAA v: 3.3 Mesa 21.0.3 direct render: Yes 
Audio:
  Device-1: NVIDIA MCP72XE/MCP72P/MCP78U/MCP78S High Definition Audio 
  vendor: Hewlett-Packard driver: snd_hda_intel v: kernel bus ID: 00:07.0 
  Sound Server: ALSA v: k5.11.0-37-generic 
Network:
  Device-1: NVIDIA MCP77 Ethernet vendor: Hewlett-Packard driver: forcedeth 
  v: kernel port: 30f8 bus ID: 00:0a.0 
  IF: enp0s10 state: down mac: <filter> 
  Device-2: Qualcomm Atheros AR928X Wireless Network Adapter 
  vendor: Hewlett-Packard driver: ath9k v: kernel port: 4000 bus ID: 07:00.0 
  IF: wlp7s0 state: up mac: <filter> 
Drives:
  Local Storage: total: 232.89 GiB used: 16.53 GiB (7.1%) 
  ID-1: /dev/sdb vendor: Toshiba model: MK2552GSX size: 232.89 GiB 
Partition:
  ID-1: / size: 227.74 GiB used: 16.53 GiB (7.3%) fs: ext4 dev: /dev/sdb5 
  ID-2: /boot/efi size: 511 MiB used: 4 KiB (0.0%) fs: vfat dev: /dev/sdb1 
Swap:
  ID-1: swap-1 type: file size: 2 GiB used: 0 KiB (0.0%) file: /swapfile     <<<<<------------ according to what I've read, this should be sufficient. However, I raised it to 4G
Sensors:
  System Temperatures: cpu: 58.2 C mobo: 52.0 C gpu: nouveau temp: 62.0 C 
  Fan Speeds (RPM): N/A 
Info:
  Processes: 205 Uptime: 20m Memory: 3.59 GiB used: 935.8 MiB (25.5%)     <<<---------- only has 4G of RAM and no room for more.
  Init: systemd runlevel: 5 Compilers: gcc: N/A 
  clang: 12.0.0-3ubuntu1~21.04.2 Packages: 2771 Shell: Bash v: 5.1.4 
  inxi: 3.3.01 
bill@bill-hp-g60:~$

```

I also tweaked the "swappiness" value from the default of 60 to 70, to see if it would cause the OS to use swapfile more. I'm hoping this will cause the computer to freeze ***more ***often. If it does, then I've probably found my culprit and can lower the value to 30 or 40.

All the above changes were also set into "fstab" and the system config file.

There was one puzzling bit in the fstab though:

```

bill@bill-hp-g60:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sda5 during installation
UUID=1b35c21c-a55d-428a-990a-c10e218bc5c8 /               ext4    errors=remount-ro 0       1
# /boot/efi was on /dev/sda1 during installation
UUID=4646-30CD  /boot/efi       vfat    umask=0077      0       1
/swapfile                                 none            swap    sw              0       0                <<<<< ------------- this is NOT what was indicated in the inxi report above. Should I change it to:
bill@bill-hp-g60:                                                                                                                                /swapfile      swap    swap     sw       0       0             ????

```

Bill

---

### Post by ajgreeny on 2021-10-04
Your fstab file reads exactly like mine, except for the UUID of course, so I don't think that is wrong.

---

### Post by WB0HYQ on 2021-10-04
I plan on working over the desktop machine today. I'll post the things others have asked me to.

@AJGreeny: This is encouraging. The indication there is no mount point for the swapfile is a concern for me though. The articles/threads I've seen all have as a last item:

sudo nano /etc/fstab      and to add:  /swapfile    swap    swap    defaults    0    0

I wonder why.

Bill

PS: Why in the world would this forum have to connect to Facebook? The Firefox status line keeps saying it is waiting for Facebook--sometimes for as long as 30 seconds.

---

### Post by ajgreeny on 2021-10-04
There should not be a mount point for the swapfile and I think your system will have a delay as it tries to mount it at boot.
The swap**file** is just that, a file, and files do not have mountpoints, only devices such as partitions have them in normal situations.

PS.
I am also seeing the facebook connect delay at present no doubt due to the fact that facebook, instagram and whatsapp have all crashed gone down at present (in UK and probably worldwide).

---

### Post by WB0HYQ on 2021-10-04
Five minutes after I posted my last, I remembered that files don't have mount points. Oops.

Found some really strange stuff in my desktop machine. 

The results of the 'inxi' command:

```

bill@bill-UBU:~$ inxi -Fzx
System:
  Kernel: 5.11.0-37-generic x86_64 bits: 64 compiler: N/A 
  Desktop: Gnome 3.36.9 Distro: Ubuntu 20.04.3 LTS (Focal Fossa) 
Machine:
  Type: Desktop Mobo: MSI model: 760GM-P23(FX) (MS-7641) v: 3.0 
  serial: <filter> BIOS: American Megatrends v: 17.2 date: 09/30/2011 
CPU:
  Topology: Triple Core model: AMD Athlon II X3 460 bits: 64 type: MCP 
  arch: K10 rev: 3 L2 cache: 1536 KiB 
  flags: lm nx pae sse sse2 sse3 sse4a svm bogomips: 20400 
  Speed: 800 MHz min/max: 800/3400 MHz Core speeds (MHz): 1: 800 2: 800 
  3: 800 
Graphics:
  Device-1: NVIDIA GK208B [GeForce GT 710] vendor: Micro-Star MSI 
  driver: nouveau v: kernel bus ID: 01:00.0 
  Display: x11 server: X.Org 1.20.11 driver: modesetting 
  unloaded: fbdev,vesa resolution: 1920x1080~60Hz 
  OpenGL: renderer: NV106 v: 4.3 Mesa 21.0.3 direct render: Yes 
Audio:
  Device-1: AMD SBx00 Azalia vendor: Micro-Star MSI driver: snd_hda_intel 
  v: kernel bus ID: 00:14.2 
  Device-2: NVIDIA GK208 HDMI/DP Audio vendor: Micro-Star MSI 
  driver: snd_hda_intel v: kernel bus ID: 01:00.1 
  Sound Server: ALSA v: k5.11.0-37-generic 
Network:
  Device-1: Realtek RTL8111/8168/8411 PCI Express Gigabit Ethernet 
  driver: r8169 v: kernel port: d800 bus ID: 02:00.0 
  IF: enp2s0 state: up speed: 1000 Mbps duplex: full mac: <filter> 
  Device-2: Realtek RTL8111/8168/8411 PCI Express Gigabit Ethernet 
  vendor: Micro-Star MSI driver: r8169 v: kernel port: e800 bus ID: 03:00.0 
  IF: enp3s0 state: down mac: <filter> 
Drives:
  Local Storage: total: 3.87 TiB used: 529.02 GiB (13.4%) 
  ID-1: /dev/sda vendor: Hitachi model: HDP725025GLA380 size: 232.89 GiB 
  temp: 41 C 
  ID-2: /dev/sdb vendor: Western Digital model: WD20EZAZ-00GGJB0 
  size: 1.82 TiB temp: 31 C 
  ID-3: /dev/sdc vendor: Western Digital model: WD10EZEX-22MFCA0 
  size: 931.51 GiB temp: 40 C 
  ID-4: /dev/sdd type: USB vendor: Western Digital model: WD10EADS-11P8B1 
  size: 930.86 GiB 
Partition:
  ID-1: / size: 228.23 GiB used: 21.92 GiB (9.6%) fs: ext4 dev: /dev/sda1 
Sensors:
  System Temperatures: cpu: 22.8 C mobo: N/A gpu: nouveau temp: 44 C 
  Fan Speeds (RPM): N/A 
Info:
  Processes: 215 Uptime: 14m Memory: 15.63 GiB used: 777.7 MiB (4.9%) 
  Init: systemd runlevel: 5 Compilers: gcc: N/A Shell: bash v: 5.0.17 
  inxi: 3.0.38 
bill@bill-UBU:~$ 
-----------------------

bill@bill-UBU:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sda1 during installation
UUID=31c0f701-8970-4605-8097-061f624e4cd3 /               ext4    errors=remount-ro 0       1
/swapfile                                 none            swap    sw              0       0
bill@bill-UBU:

```

And the 'swapon' command:

```

bill@bill-UBU:~$ sudo swapon --show        <<<<< - before
NAME      TYPE SIZE USED PRIO
/swapfile file   2G   0B   -2                                     <<<<---- my system has 16G of RAM
bill@bill-UBU:~$ grep SwapTotal /proc/meminfo
SwapTotal:       2097148 kB

```

So, I created a bigger swapfile:

```

bill@bill-UBU:~$ sudo swapoff -a
bill@bill-UBU:~$ sudo dd if=/dev/zero of=/swapfile bs=1G count=16
16+0 records in
16+0 records out
17179869184 bytes (17 GB, 16 GiB) copied, 215.904 s, 79.6 MB/s
bill@bill-UBU:~$ sudo chmod 600 /swapfile
bill@bill-UBU:~$ sudo mkswap /swapfile
Setting up swapspace version 1, size = 16 GiB (17179865088 bytes)
no label, UUID=412f62e4-f39f-4116-a5fb-fc16af8505ef
bill@bill-UBU:~$ sudo swapon /swapfile
bill@bill-UBU:~$ grep SwapTotal /proc/meminfo
SwapTotal:      16777212 kB



bill@bill-UBU:~$ sudo swapon --show        <<<<<<<<------- after (I fully realize this swapfile is probably overly huge, but when you have a lot of gigs to play with......)
NAME      TYPE SIZE USED PRIO
/swapfile file  16G   0B   -2
bill@bill-UBU:~$ 


```

So far, the computer (after a reboot) has been running all afternoon doing all sorts of stuff. I leave every window open and move on to yet another application. Plus I have 6 workspaces to use.

I am fairly sure now my freezes have been because of the swap process getting hung up by a slow processor and perhaps a smaller swapfile. All four of my computers are pretty old (greater than 5 years) so have older CPUs. The examination of 3 computers using journalctl show quite a few places where the CPU is shown to be slow.

Bill

---

### Post by WB0HYQ on 2021-10-06
Apparently I was right. My desktop computer has bee running now for 3 days with no freezes since I upped the swap space and changed the "swappiness" value. I can have all six workspaces full of items and have to failures. In fact, the computer seems even faster than before. This is true of three of my four problem computers. Once they were more stable, I upped the distro number to 21.04 with no ill effects.

I'm going to mark this Solved. My thanks to those who helped me with this.

Bill

---

