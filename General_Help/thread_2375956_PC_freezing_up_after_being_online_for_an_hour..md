---
title: "PC freezing up after being online for an hour."
date: 2017-10-29
forum: General Help
---

### Post by cheapodonuts on 2017-10-29
Software updated itself yesterday but it hasn't improved anything after the last several times.
I've let this get to the point where I would normally just re-install Ubuntu. But I really should find out what's hap with this machine as it always seems to. slow down after a while. 
 This install is approx 3 months old and just recently has been more annoying than usual when I'm watching videos. Most Youtube vids viewed at 720p or higher will slow down and stop, though the sound keeps going, but some won't play at all and freeze the screen if I don't react quickly. Going to something like an anime site has me looking for the lowest resolution possible. But even then, after letting something play  for a while it may hesitate occasionally and at the end my screen has become very unresponsive. Not just the video site, but everything to do with the PC.
 This morning, after about an hour from powering up, checking the BBC news then letting an online anime play for 30 mins, everything had slowed down once it ended. Closing the page took ages and after that I tried to open Firefox preferences, and had a blank about/preferences screen permanently. After making some toast and doing other stuff for 10 mins it was still blank.
I couldn't even close the page and couldn't reboot the PC. Had to do a hard reset.
 I have no addons installed and Ubuntu modifications currently disabled, though it's no different when enabled.
 No other browsers installed and I don't use this machine for anything except surfing the web. So I can't say if the same thing would happen without going online. I have installed Gimp, but almost never use it.
I did run apt update the other day after reading something on the forum, but little change was seen.
 I clear my browser cache and cookies daily. It does make a difference, but today I cleared both of them and my history early in the session and the slow down was after just one hour and one anime. 

Thanks in advance for any assistance guys. :)

-Computer-
```
Processor        : 2x AMD Athlon(tm) 64 X2 Dual Core Processor 4600+
Memory        : 1915MB (673MB used)
Operating System        : Ubuntu 17.04
User Name        : cheapo (cheapo)
Date/Time        : Sun 29 Oct 2017 08:54:06 GMT
-Display-
Resolution        : 1280x1024 pixels
OpenGL Renderer        : Unknown
X11 Vendor        : The X.Org Foundation
-Multimedia-
Audio Adapter        : HDA-Intel - HDA NVidia
-Input Devices-
 Power Button
 Power Button
 AT Translated Set 2 keyboard
 Primax Kensington Eagle Trackball
 HDA NVidia Front Mic
 HDA NVidia Rear Mic
 HDA NVidia Line
 HDA NVidia Line Out Front
 HDA NVidia Line Out Surround
 HDA NVidia Line Out CLFE
 HDA NVidia Line Out Side
 HDA NVidia Front Headphone
-Printers (CUPS)-
EPSON-Stylus-SX200        : <i>Default</i>
-SCSI Disks-
ATA WDC WD3200AAJS-6
TSSTcorp CDDVDW TS-H653Q
Generic USB SD Reader
Generic USB CF Reader
Generic USB SM Reader
Generic USB MS Reader
```

Tried to upload dsmeg text, but the attachment app says it's too big. How can i make it smaller?

---

### Post by kc1di on 2017-10-29
It sounds like it may be overheating. can you install inxi and then in a terminal type ```
inxi -F
```
post the output here.  Do this while your watching a video and when the system seems slow.

---

### Post by cheapodonuts on 2017-10-29
More than a hour this time, but it's starting to mess about, 

```
cheapo@cheapo-KX733AA-ABU-a6511-uk:~$ inxi -F
System:    Host: cheapo-KX733AA-ABU-a6511-uk Kernel: 4.10.0-37-generic x86_64 (64 bit)
           Desktop: LXDE (Openbox 3.6.1) Distro: Ubuntu 17.04
Machine:   Device: desktop System: HP-Pavilion product: KX733AA-ABU a6511.uk
           Mobo: PEGATRON model: NARRA3 v: 3.02
           BIOS: Phoenix v: 5.14 date: 06/20/2008
CPU:       Dual core AMD Athlon 64 X2 4600+ (-MCP-) cache: 1024 KB 
           clock speeds: max: 2400 MHz 1: 2000 MHz 2: 2000 MHz
Graphics:  Card: NVIDIA C61 [GeForce 6150SE nForce 430]
           Display Server: X.Org 1.19.3 drivers: nvidia (unloaded: modesetting,fbdev,vesa,nouveau)
           Resolution: 1280x1024@60.02hz
           GLX Renderer: GeForce 6150SE nForce 430/integrated/SSE2
           GLX Version: 2.1.2 NVIDIA 304.135
Audio:     Card NVIDIA MCP61 High Definition Audio driver: snd_hda_intel
           Sound: Advanced Linux Sound Architecture v: k4.10.0-37-generic
Network:   Card: NVIDIA MCP61 Ethernet driver: forcedeth
           IF: enp0s7 state: up speed: 100 Mbps duplex: full
           mac: 00:22:15:25:dc:0a
Drives:    HDD Total Size: 320.1GB (2.6% used)
           ID-1: /dev/sda model: WDC_WD3200AAJS size: 320.1GB
Partition: ID-1: / size: 293G used: 7.7G (3%) fs: ext4 dev: /dev/sda1
RAID:      No RAID devices: /proc/mdstat, md_mod kernel module present
Sensors:   System Temperatures: cpu: 26.0C mobo: N/A
           Fan Speeds (in rpm): cpu: N/A
Info:      Processes: 152 Uptime: 3:35 Memory: 1291.7/1871.0MB
           Client: Shell (bash) inxi: 2.3.8 
cheapo@cheapo-KX733AA-ABU-a6511-uk:~$
```

---

### Post by cheapodonuts on 2017-10-29
And again a few mins later

```
cheapo@cheapo-KX733AA-ABU-a6511-uk:~$ inxi -F
System:    Host: cheapo-KX733AA-ABU-a6511-uk Kernel: 4.10.0-37-generic x86_64 (64 bit)
           Desktop: LXDE (Openbox 3.6.1) Distro: Ubuntu 17.04
Machine:   Device: desktop System: HP-Pavilion product: KX733AA-ABU a6511.uk
           Mobo: PEGATRON model: NARRA3 v: 3.02 BIOS: Phoenix v: 5.14 date: 06/20/2008
CPU:       Dual core AMD Athlon 64 X2 4600+ (-MCP-) cache: 1024 KB 
           clock speeds: max: 2400 MHz 1: 2200 MHz 2: 2200 MHz
Graphics:  Card: NVIDIA C61 [GeForce 6150SE nForce 430]
           Display Server: X.Org 1.19.3 drivers: nvidia (unloaded: modesetting,fbdev,vesa,nouveau)
           Resolution: 1280x1024@60.02hz
           GLX Renderer: GeForce 6150SE nForce 430/integrated/SSE2 GLX Version: 2.1.2 NVIDIA 304.135
Audio:     Card NVIDIA MCP61 High Definition Audio driver: snd_hda_intel Sound: ALSA v: k4.10.0-37-generic
Network:   Card: NVIDIA MCP61 Ethernet driver: forcedeth
           IF: enp0s7 state: up speed: 100 Mbps duplex: full mac: 00:22:15:25:dc:0a
Drives:    HDD Total Size: 320.1GB (2.3% used)
           ID-1: /dev/sda model: WDC_WD3200AAJS size: 320.1GB
Partition: ID-1: / size: 293G used: 6.9G (3%) fs: ext4 dev: /dev/sda1
RAID:      No RAID devices: /proc/mdstat, md_mod kernel module present
Sensors:   System Temperatures: cpu: 56.0C mobo: N/A
           Fan Speeds (in rpm): cpu: N/A
Info:      Processes: 151 Uptime: 3:42 Memory: 1516.7/1871.0MB Client: Shell (bash) inxi: 2.3.8 
cheapo@cheapo-KX733AA-ABU-a6511-uk:~$ 

```

temperature has jumped up by 30deg

---

### Post by kc1di on 2017-10-29
The first time it said your cpu  temp was **Sensors: System Temperatures: cpu: 26.0C**
and the second one says** Sensors: System Temperatures: cpu: 56.0C mobo: N/A**

I would say that's quite a rise in Temp but do not think it is extrem so not sure that's what the problem is my laptop runs a constant 59c to 62c.

What the cpu load according to the system monitor?  or you may wish to install htop ```
sudo apt-get install htop
``` then
run in terminal with the command ```
htop
```
the top line on htop wiill show which process is using the most of the cpu %. 

I suspect that  if watching video the cpu is being maxed out.

---

### Post by slickymaster on 2017-10-29
@cheapodonuts:

Please [use code tags]("https://ubuntuforums.org/showthread.php?t=2171721&p=12776168&viewfull=1#post12776168") when posting output. Output posted as plain text loses its formatting and parts of it sometimes turn into smileys making it difficult to read and understand. The use of code tags makes the post clean, compact and more appealing, thus getting more attention from readers.

---

### Post by cheapodonuts on 2017-10-29
Thanx for your assistance KC
CPU's bouncing between 10% and 105% with the vid not loading. Those were min and max seen in about 2 mins, but I haven't seen the 105% again in the last five.
 Got the vid running now and CPU usage is between 40% and 60%. Also, I left the side cover off the PC and it's running about 35C now

---

### Post by cheapodonuts on 2017-10-29
> **slickymaster said:**
> @cheapodonuts:

Please [use code tags]("https://ubuntuforums.org/showthread.php?t=2171721&p=12776168&viewfull=1#post12776168") when posting output. Output posted as plain text loses its formatting and parts of it sometimes turn into smileys making it difficult to read and understand. The use of code tags makes the post clean, compact and more appealing, thus getting more attention from readers.


Thanx sensei. Got it! :)

---

### Post by cheapodonuts on 2017-10-29
Here's the dmesg result,

[https://paste.ubuntu.com/25847167/](https://paste.ubuntu.com/25847167/)

---

