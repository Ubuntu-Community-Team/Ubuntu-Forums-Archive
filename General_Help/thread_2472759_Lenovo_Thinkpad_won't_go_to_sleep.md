---
title: "Lenovo Thinkpad won't go to sleep"
date: 2022-03-11
forum: General Help
---

### Post by geosebastian on 2022-03-11
I saw some threads of people having similar issues but none of the solutions that were posted seemed to work for me. I'm not very technical and new to ubuntu (20.04) so maybe I'm doing something wrong. Simple explanations appreciated. 

So far I've tried going in the settings and selecting "suspend" under Power Button Action (that did nothing) and going in the terminal and typing:

#!/bin/sh
#Disable XHC wake
#case "$1" in start)   sudo sh -c "echo XHC >/proc/acpi/wakeup" ;; stop) sudo sh -c "echo XHC >procacpi/wakeup" ;; esac exit 0

when I clicked enter, nothing seemed to happen. I was supposed to somehow link "rc5.d" after that but when I copied what I found online all I got was this 

/etc/rc0.d/K*
Usage: /etc/init.d/alsa-utils {start [CARD]|stop [CARD]|restart [CARD]|reset [CARD]}

and nothing had changed. 

Someone also said that typing:

sh -c "echo XHC > /proc/acpi/wakeup" 

worked for them, but when I tried typing that in the terminal, I got:

sh: 1: cannot create /proc/acpi/wakeup: Permission denied

What am I doing wrong? 


George

---

### Post by #&amp;thj^% on 2022-03-11
> **geosebastian said:**
> I saw some threads of people having similar issues but none of the solutions that were posted seemed to work for me. I'm not very technical and new to ubuntu (20.04) so maybe I'm doing something wrong. Simple explanations appreciated. 

So far I've tried going in the settings and selecting "suspend" under Power Button Action (that did nothing) and going in the terminal and typing:

#!/bin/sh
#Disable XHC wake
#case "$1" in start)   sudo sh -c "echo XHC >/proc/acpi/wakeup" ;; stop) sudo sh -c "echo XHC >procacpi/wakeup" ;; esac exit 0

when I clicked enter, nothing seemed to happen. I was supposed to somehow link "rc5.d" after that but when I copied what I found online all I got was this 

/etc/rc0.d/K*
Usage: /etc/init.d/alsa-utils {start [CARD]|stop [CARD]|restart [CARD]|reset [CARD]}

and nothing had changed. 

Someone also said that typing:

sh -c "echo XHC > /proc/acpi/wakeup" 

worked for them, but when I tried typing that in the terminal, I got:

sh: 1: cannot create /proc/acpi/wakeup: Permission denied

What am I doing wrong? 


George
Post the link your following and ThinkPad what model
Show this:
```
 inxi -Fz
```
The most useful command is:
```


pm-suspend (aka sleep. Fast wake.)

The following commands may not be supported.

    pm-hibernate (save most power. Slow wake.)
    pm-suspend-hybrid (a combination of sleep and hibernate.)
    pm-is-supported (test which is supported)
    pm-powersave

man pm-suspend to see its doc.
```

---

### Post by geosebastian on 2022-03-11
Hi there. Thanks for the reply. I tried typing what you said and I got:

Command 'inxi' not found, but can be installed with:

sudo apt install inxi

oem@oem-Latitude-E6410:~$ sudo apt install inxi
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following additional packages will be installed:
  hddtemp lm-sensors tree
Suggested packages:
  libcpanel-json-xs-perl | libjson-xs-perl libxml-dumper-perl fancontrol
  read-edid i2c-tools
The following NEW packages will be installed:
  hddtemp inxi lm-sensors tree
0 upgraded, 4 newly installed, 0 to remove and 4 not upgraded.
Need to get 361 kB of archives.
After this operation, 1,527 kB of additional disk space will be used.
Do you want to continue? [Y/n] y
Get:1 [http://ca.archive.ubuntu.com/ubuntu](http://ca.archive.ubuntu.com/ubuntu) focal/universe amd64 tree amd64 1.8.0-1 [43.0 kB]
Get:2 [http://ca.archive.ubuntu.com/ubuntu](http://ca.archive.ubuntu.com/ubuntu) focal/universe amd64 hddtemp amd64 0.3-beta15-53 [47.7 kB]
Get:3 [http://ca.archive.ubuntu.com/ubuntu](http://ca.archive.ubuntu.com/ubuntu) focal/universe amd64 inxi all 3.0.38-1-0ubuntu1 [182 kB]
Get:4 [http://ca.archive.ubuntu.com/ubuntu](http://ca.archive.ubuntu.com/ubuntu) focal/universe amd64 lm-sensors amd64 1:3.6.0-2ubuntu1 [87.4 kB]
Fetched 361 kB in 2s (149 kB/s)       
Preconfiguring packages ...
Selecting previously unselected package tree.
(Reading database ... 181200 files and directories currently installed.)
Preparing to unpack .../tree_1.8.0-1_amd64.deb ...
Unpacking tree (1.8.0-1) ...
Selecting previously unselected package hddtemp.
Preparing to unpack .../hddtemp_0.3-beta15-53_amd64.deb ...
Unpacking hddtemp (0.3-beta15-53) ...
Selecting previously unselected package inxi.
Preparing to unpack .../inxi_3.0.38-1-0ubuntu1_all.deb ...
Unpacking inxi (3.0.38-1-0ubuntu1) ...
Selecting previously unselected package lm-sensors.
Preparing to unpack .../lm-sensors_1%3a3.6.0-2ubuntu1_amd64.deb ...
Unpacking lm-sensors (1:3.6.0-2ubuntu1) ...
Setting up inxi (3.0.38-1-0ubuntu1) ...
Setting up tree (1.8.0-1) ...
Setting up lm-sensors (1:3.6.0-2ubuntu1) ...
Created symlink /etc/systemd/system/multi-user.target.wants/lm-sensors.service &#8594;
 /lib/systemd/system/lm-sensors.service.
Setting up hddtemp (0.3-beta15-53) ...
Processing triggers for man-db (2.9.1-1) ...
Processing triggers for systemd (245.4-4ubuntu3.15) ...

Not sure what that was supposed to do though. 

When I tried typing pm-suspend I got:

Command 'pm-suspend' not found, but can be installed with:

sudo apt install molly-guard  # version 0.7.2, or
sudo apt install pm-utils     # version 1.4.1-19

so I tried the first option. Is that right? Then it said:

oem@oem-Latitude-E6410:~$ sudo apt install molly-guard #version 0.7.2

Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following NEW packages will be installed:
  molly-guard
0 upgraded, 1 newly installed, 0 to remove and 4 not upgraded.
Need to get 12.3 kB of archives.
After this operation, 57.3 kB of additional disk space will be used.
Get:1 [http://ca.archive.ubuntu.com/ubuntu](http://ca.archive.ubuntu.com/ubuntu) focal/universe amd64 molly-guard all 0.7.2 [12.3 kB]
Fetched 12.3 kB in 1s (11.8 kB/s)      
Selecting previously unselected package molly-guard.
(Reading database ... 181172 files and directories currently installed.)
Preparing to unpack .../molly-guard_0.7.2_all.deb ...
No diversion 'diversion of /sbin/pm-hibernate by molly-guard', none removed.
No diversion 'diversion of /sbin/pm-suspend by molly-guard', none removed.
No diversion 'diversion of /sbin/pm-suspend-hybrid by molly-guard', none removed
.
Adding 'diversion of /sbin/halt to /lib/molly-guard/halt by molly-guard'
Adding 'diversion of /sbin/poweroff to /lib/molly-guard/poweroff by molly-guard'
Adding 'diversion of /sbin/reboot to /lib/molly-guard/reboot by molly-guard'
Adding 'diversion of /sbin/shutdown to /lib/molly-guard/shutdown by molly-guard'
Adding 'diversion of /sbin/coldreboot to /lib/molly-guard/coldreboot by molly-gu
ard'
Adding 'diversion of /usr/sbin/pm-hibernate to /lib/molly-guard/pm-hibernate by 
molly-guard'
Adding 'diversion of /usr/sbin/pm-suspend to /lib/molly-guard/pm-suspend by moll
y-guard'
Adding 'diversion of /usr/sbin/pm-suspend-hybrid to /lib/molly-guard/pm-suspend-
hybrid by molly-guard'
Unpacking molly-guard (0.7.2) ...
Setting up molly-guard (0.7.2) ...
Processing triggers for man-db (2.9.1-1) ...

None of that seems to have made any difference though. When I try to suspend it, it just shuts down for a few seconds then turns back on. 

Here's the thread I've been looking at. [https://askubuntu.com/questions/980453/ubuntu-17-10-on-thinkpad-yoga-wont-sleep](https://askubuntu.com/questions/980453/ubuntu-17-10-on-thinkpad-yoga-wont-sleep)

I also found someone in another thread who said that they managed to fix the same problem on their yoga slim 7 (mine is a yoga *20CD00BYUS*) by going into the advanced bios and changing some settings there, but I can't figure out how to get into advanced bios so that's not working for me either. 

[https://forums.lenovo.com/t5/Other-Linux-Discussions/Yoga-Slim-7-cannot-enter-deep-sleep-S3-state-aka-Suspend-to-RAM-on-Linux/m-p/5039060?page=2](https://forums.lenovo.com/t5/Other-Linux-Discussions/Yoga-Slim-7-cannot-enter-deep-sleep-S3-state-aka-Suspend-to-RAM-on-Linux/m-p/5039060?page=2)

---

### Post by geosebastian on 2022-03-11
This is what it says now when I try "pm-suspend":

oem@oem-Latitude-E6410:~$ pm-suspend
E: not a regular file: /lib/molly-guard/pm-suspend

---

### Post by geosebastian on 2022-03-11
suspend hybrid got me the same "not a regular file" message as before. 

then pm is supported got me this:

Command 'pm-is-supported' not found, but can be installed with:

sudo apt install pm-utils

oem@oem-Latitude-E6410:~$ sudo apt install pm-utils
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following additional packages will be installed:
  ethtool libx86-1 vbetool
Suggested packages:
  cpufrequtils radeontool
The following NEW packages will be installed:
  ethtool libx86-1 pm-utils vbetool
0 upgraded, 4 newly installed, 0 to remove and 4 not upgraded.
Need to get 269 kB of archives.
After this operation, 997 kB of additional disk space will be used.
Do you want to continue? [Y/n] y
Get:1 http://ca.archive.ubuntu.com/ubuntu focal/main amd64 ethtool amd64 1:5.4-1 [134 kB]
Get:2 http://ca.archive.ubuntu.com/ubuntu focal/universe amd64 libx86-1 amd64 1.1+ds1-11 [76.1 kB]
Get:3 http://ca.archive.ubuntu.com/ubuntu focal/universe amd64 pm-utils all 1.4.1-19 [48.1 kB]
Get:4 http://ca.archive.ubuntu.com/ubuntu focal/universe amd64 vbetool amd64 1.1-4 [11.5 kB]
Fetched 269 kB in 1s (307 kB/s)     
Selecting previously unselected package ethtool.
(Reading database ... 181277 files and directories currently installed.)
Preparing to unpack .../ethtool_1%3a5.4-1_amd64.deb ...
Unpacking ethtool (1:5.4-1) ...
Selecting previously unselected package libx86-1:amd64.
Preparing to unpack .../libx86-1_1.1+ds1-11_amd64.deb ...
Unpacking libx86-1:amd64 (1.1+ds1-11) ...
Selecting previously unselected package pm-utils.
Preparing to unpack .../pm-utils_1.4.1-19_all.deb ...
Unpacking pm-utils (1.4.1-19) ...
Selecting previously unselected package vbetool.
Preparing to unpack .../vbetool_1.1-4_amd64.deb ...
Unpacking vbetool (1.1-4) ...
Setting up libx86-1:amd64 (1.1+ds1-11) ...
Setting up vbetool (1.1-4) ...
Setting up pm-utils (1.4.1-19) ...
Setting up ethtool (1:5.4-1) ...
Processing triggers for man-db (2.9.1-1) ...
Processing triggers for libc-bin (2.31-0ubuntu9.7) ...
oem@oem-Latitude-E6410:~$ pm-is-supported
pm-is-supported [--suspend | --hibernate | --suspend-hybrid ]

and pm-powersave got me:

mkdir: cannot create directory ‘/var/run/pm-utils’: Permission denied
touch: cannot touch '/var/run/pm-utils/locks/pm-powersave.lock': No such file or directory
/usr/sbin/pm-powersave: 30: cannot open /var/run/pm-utils/locks/pm-powersave.lock: No such file

---

### Post by geosebastian on 2022-03-11
Oh, I just noticed that I made a typo when I tried the "inxi" thing. Here's what I got when I did it again just now. 

System:
  Kernel: 5.13.0-35-generic x86_64 bits: 64 Desktop: Gnome 3.36.9 
  Distro: Ubuntu 20.04.4 LTS (Focal Fossa) 
Machine:
  Type: Laptop System: LENOVO product: 20CD00BYUS v: ThinkPad S1 Yoga 
  serial: <filter> 
  Mobo: LENOVO model: 20CD00BYUS v: SDK0E50510 Pro serial: <filter> 
  UEFI: LENOVO v: B0ET42WW (1.29 ) date: 05/29/2018 
Battery:
  ID-1: BAT0 charge: 39.0 Wh condition: 39.0/47.1 Wh (83%) 
CPU:
  Topology: Dual Core model: Intel Core i7-4600U bits: 64 type: MT MCP 
  L2 cache: 4096 KiB 
  Speed: 931 MHz min/max: 800/3300 MHz Core speeds (MHz): 1: 949 2: 937 
  3: 1406 4: 898 
Graphics:
  Device-1: Intel Haswell-ULT Integrated Graphics driver: i915 v: kernel 
  Display: x11 server: X.Org 1.20.13 driver: i915 resolution: 1366x768~60Hz 
  OpenGL: renderer: Mesa DRI Intel HD Graphics 4400 (HSW GT2) 
  v: 4.5 Mesa 21.2.6 
Audio:
  Device-1: Intel Haswell-ULT HD Audio driver: snd_hda_intel 
  Device-2: Intel 8 Series HD Audio driver: snd_hda_intel 
  Sound Server: ALSA v: k5.13.0-35-generic 
Network:
  Device-1: Intel Wireless 7260 driver: iwlwifi 
  IF: wlp4s0 state: up mac: <filter> 
Drives:
  Local Storage: total: 465.76 GiB used: 12.31 GiB (2.6%) 
  ID-1: /dev/sda vendor: Hitachi model: HTS725050A7E630 size: 465.76 GiB 
Partition:
  ID-1: / size: 456.96 GiB used: 12.31 GiB (2.7%) fs: ext4 dev: /dev/sda2 
Sensors:
  System Temperatures: cpu: 45.0 C mobo: N/A 
  Fan Speeds (RPM): cpu: 0 
Info:
  Processes: 327 Uptime: 1h 30m Memory: 7.66 GiB used: 1.59 GiB (20.7%) 
  Shell: bash inxi: 3.0.38

---

### Post by #&amp;thj^% on 2022-03-11
Some modern Lenovo laptops lack S3 support, which leads to issues such as a black screen after you try to wake up the laptop after suspend. It's caused by amdgpu problems with Modern Standby. Luckily, Lenovo hides some BIOS options, but there's the possibility to unlock them and enable the S3 mode under the "S3/Modern Standby Support" Section. 
See if this is what your after: [https://github.com/jrandiny/yoga-slim7-ubuntu#bios-unlock](https://github.com/jrandiny/yoga-slim7-ubuntu#bios-unlock)
I knew I had seen that mollygaurd before, you may find this useful as well: [https://manpages.ubuntu.com/manpages/focal/man8/molly-guard.8.html](https://manpages.ubuntu.com/manpages/focal/man8/molly-guard.8.html)
BTW: Whens the last time you upgraded your firmware EX:>>UEFI: LENOVO v: B0ET42WW (1.29 ) date: 05/29/2018

---

### Post by geosebastian on 2022-03-11
Thanks again for the help. Still don't seem to be having much luck though. The molly guard "halt" made the screen go dark but the computer was still running, and everything else got me the same error message:

oem@oem-Latitude-E6410:~$ pm-hibernate
This utility may only be run by the root user.
oem@oem-Latitude-E6410:~$ pm-suspend-hybrid
This utility may only be run by the root user.
oem@oem-Latitude-E6410:~$  pm-suspend
This utility may only be run by the root user.

As for the advanced bios thing, I saw that page before but I must be missing something. When I type in "# ./yoga-bios-unlock --unlock" and hit enter, nothing happens.

As I understand it, it's supposed to give me something like this:
Run in unlock mode
WARNING: use at your own risk!
Agree? (y/n) y
Port 0x72 is 0xf4 and will be set to 0xf7

I can't figure out what I'm doing wrong.

---

### Post by #&amp;thj^% on 2022-03-11
> **geosebastian said:**
> Thanks again for the help. Still don't seem to be having much luck though. The molly guard "halt" made the screen go dark but the computer was still running, and everything else got me the same error message:

oem@oem-Latitude-E6410:~$ pm-hibernate
This utility may only be run by the root user.
oem@oem-Latitude-E6410:~$ pm-suspend-hybrid
This utility may only be run by the root user.
oem@oem-Latitude-E6410:~$  pm-suspend
This utility may only be run by the root user.



As it said run by root user:
```
sudo pm-suspend
```
Now dose it sleep.
I'm not touching your Bios settings, I just don't have firsthand knowledge on that machine.

---

### Post by geosebastian on 2022-03-11
No, it still does the same thing when I enter sudo pm-suspend as it does when I hit suspend. It just turns off for a second then turns right back on.

---

### Post by #&amp;thj^% on 2022-03-12
> **geosebastian said:**
> No, it still does the same thing when I enter sudo pm-suspend as it does when I hit suspend. It just turns off for a second then turns right back on.

Yep you need the unlock.
Disclaimer I 1fallen really hate posting things of this nature on a public forum, as it's meant for highly advanced operations. READ THE BELOW!

   ** This tool may eat your cat, burn your house or do anything else beside the expected task. So use it at your own risk and be aware that you're playing around with your BIOS which may end in a bricked device. I'll offer no help there.**

Build from source
```

git clone https://github.com/esno/yoga-bios-unlock.git
cd ./yoga-bios-unlock
make
```
It will look like:
```
Cloning into 'yoga-bios-unlock'...
remote: Enumerating objects: 190, done.
remote: Counting objects: 100% (190/190), done.
remote: Compressing objects: 100% (104/104), done.
remote: Total 190 (delta 97), reused 140 (delta 54), pack-reused 0
Receiving objects: 100% (190/190), 27.35 KiB | 6.84 MiB/s, done.
Resolving deltas: 100% (97/97), done.

```
Once that has completed:
```
cd ./yoga-bios-unlock
```
And final run:
```
make
```
Example:
```
cc -o ./yoga-bios-unlock ./src/yoga-bios-unlock.c -O2 -Wall -Wextra -Wfloat-equal -Wshadow -Wstrict-prototypes -Wstrict-overflow=5 -Wcast-qual -Wconversion -Wunreachable-code

```
The rest should be clear enough.
Unlock your BIOS
```

sudo ./yoga-bios-unlock --unlock
Run in unlock mode
WARNING: use at your own risk!
Agree? (y/n) y
Port 0x72 is 0xf4 and will be set to 0xf7
```

Lock your BIOS
```

sudo ./yoga-bios-unlock --lock
Run in lock mode
WARNING: use at your own risk!
Agree? (y/n) y
Port 0x72 is 0xf4 and will be set to 0xf7
```

Ignore platform check results I'm not sure if you neeed this or not.

If you know that you're on Lenovo Yoga Slim 7 (14ARE05) but either board version might differ or BIOS version is currently not supported by this tool you can enforce an unlock. If you do please open a [ticket/PR]("https://github.com/esno/yoga-bios-unlock") to notify me that your current BIOS version/board version works well.

Enforce unlock your BIOS
```

sudo ./yoga-bios-unlock --unlock --force
Run in unlock mode
Platform checks are disabled - hopefully you know what you do
WARNING: use at your own risk!
Agree? (y/n) y
Port 0x72 is 0xf4 and will be set to 0xf7
```

---

### Post by themrinalsinha on 2022-08-16
I'm facing the same issue the system doesn't go to sleep. Tried mentioned solutions none of them worked.
system details mentioned below:
```

&#10140;  ~ inxi -Fz
System:
  Kernel: 5.15.0-46-generic x86_64 bits: 64 Desktop: GNOME 42.2
    Distro: Ubuntu 22.04.1 LTS (Jammy Jellyfish)
Machine:
  Type: Laptop System: LENOVO product: 82L7 v: IdeaPad 5 Pro 14ACN6
    serial: <superuser required>
  Mobo: LENOVO model: LNVNB161216 v: SDK0T76485 WIN
    serial: <superuser required> UEFI: LENOVO v: GECN26WW(V1.10)
    date: 08/23/2021
Battery:
  ID-1: BAT1 charge: 54.4 Wh (98.9%) condition: 55.0/56.5 Wh (97.3%)
CPU:
  Info: 8-core model: AMD Ryzen 7 5800U with Radeon Graphics bits: 64
    type: MT MCP cache: L2: 4 MiB
  Speed (MHz): avg: 1707 min/max: 400/4507 cores: 1: 1547 2: 1545 3: 1547
    4: 1547 5: 1546 6: 1545 7: 1854 8: 1855 9: 1857 10: 1856 11: 1544 12: 1547
    13: 1856 14: 1854 15: 1959 16: 1854
Graphics:
  Device-1: AMD Cezanne driver: amdgpu v: kernel
  Device-2: Chicony Integrated Camera type: USB driver: uvcvideo
  Display: x11 server: X.Org v: 1.21.1.3 driver: X: loaded: amdgpu,ati
    unloaded: fbdev,modesetting,radeon,vesa gpu: amdgpu
    resolution: 2240x1400~60Hz
  OpenGL: renderer: AMD RENOIR (LLVM 13.0.1 DRM 3.42 5.15.0-46-generic)
    v: 4.6 Mesa 22.0.5
Audio:
  Device-1: AMD Renoir Radeon High Definition Audio driver: snd_hda_intel
  Device-2: AMD Raven/Raven2/FireFlight/Renoir Audio Processor
    driver: snd_rn_pci_acp3x
  Device-3: AMD Family 17h HD Audio driver: snd_hda_intel
  Sound Server-1: ALSA v: k5.15.0-46-generic running: yes
  Sound Server-2: PulseAudio v: 15.99.1 running: yes
  Sound Server-3: PipeWire v: 0.3.48 running: yes
Network:
  Device-1: Qualcomm Atheros QCA6174 802.11ac Wireless Network Adapter
    driver: ath10k_pci
  IF: wlp1s0 state: up mac: <filter>
  IF-ID-1: br-e2b0d6b57521 state: down mac: <filter>
  IF-ID-2: br-f0406cd3b186 state: down mac: <filter>
  IF-ID-3: docker0 state: down mac: <filter>
Bluetooth:
  Device-1: Qualcomm Atheros QCA61x4 Bluetooth 4.0 type: USB driver: btusb
  Report: hciconfig ID: hci0 state: up address: <filter> bt-v: 2.1
Drives:
  Local Storage: total: 953.87 GiB used: 65.77 GiB (6.9%)
  ID-1: /dev/nvme0n1 vendor: Samsung model: MZVLB1T0HBLR-000L2
    size: 953.87 GiB
Partition:
  ID-1: / size: 937.33 GiB used: 65.76 GiB (7.0%) fs: ext4
    dev: /dev/nvme0n1p2
  ID-2: /boot/efi size: 511 MiB used: 5.2 MiB (1.0%) fs: vfat
    dev: /dev/nvme0n1p1
Swap:
  ID-1: swap-1 type: file size: 2 GiB used: 0 KiB (0.0%) file: /swapfile
Sensors:
  System Temperatures: cpu: 43.0 C mobo: N/A gpu: amdgpu temp: 40.0 C
  Fan Speeds (RPM): N/A
Info:
  Processes: 431 Uptime: 2h 42m Memory: 13.51 GiB used: 2.99 GiB (22.1%)
  Shell: Zsh inxi: 3.3.13

```

---

