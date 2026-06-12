---
title: "Google display getting cut"
date: 2018-11-21
forum: General Help
---

### Post by dilip.h.n on 2018-11-21
Hi,
I am using Ubuntu 18.04 version and now when i am browsing, very often the display gets broken as shown in screenshots.
How can i solve this issue..??

Any suggestions are highly appreciated.
Thank you.

---

### Post by HermanAB on 2018-11-21
Screen tearing is due to a bad video device driver.

---

### Post by dilip.h.n on 2018-11-21
How do i fix this issue..?

---

### Post by ajgreeny on 2018-11-21
You may need a better graphic driver but need to know what hardware you have if we are to help you more.

Show us the output of terminal command ```
inxi -F
```
Please use **Code-Tags** for terminal output as it makes that output much more easily read and understood, formatting the text as seen in terminal, not as plain text when it is copied and pasted. See my signature below for a **How-to**

---

### Post by dilip.h.n on 2018-11-21
Here is the output after ```
 inxi -F 
``` command

```

dilip@Dilip:~$ inxi -F
System: Host: Dilip Kernel: 4.15.0-39-generic x86_64 bits: 64 Desktop: Gnome 3.28.3
Distro: Ubuntu 18.04.1 LTS
Machine: Device: desktop System: HP product: HP Z238 Microtower Workstation serial: N/A
Mobo: HP model: 8183 serial: N/A UEFI [Legacy]: HP v: N51 Ver. 01.63 date: 10/05/2017
CPU: Quad core Intel Core i7-7700 (-MT-MCP-) cache: 8192 KB
clock speeds: max: 4200 MHz 1: 900 MHz 2: 940 MHz 3: 923 MHz 4: 934 MHz 5: 966 MHz 6: 900 MHz
7: 909 MHz 8: 984 MHz
Graphics: Card: NVIDIA GK208 [GeForce GT 730]
Display Server: x11 (X.Org 1.19.6 ) drivers: fbdev,nouveau (unloaded: modesetting,vesa)
Resolution: 1366x768@59.79hz
OpenGL: renderer: NV106 version: 4.3 Mesa 18.0.5
Audio: Card-1 NVIDIA GK208 HDMI/DP Audio Controller driver: snd_hda_intel Sound: ALSA v: k4.15.0-39-generic
Card-2 Intel Sunrise Point-H HD Audio driver: snd_hda_intel
Network: Card: Intel Ethernet Connection (2) I219-LM driver: e1000e
IF: eno1 state: up speed: 1000 Mbps duplex: full mac: a0:8c:fd:c3:79:16
Drives: HDD Total Size: 1000.2GB (53.0% used)
ID-1: /dev/sda model: ST1000DM003 size: 1000.2GB
Partition: ID-1: / size: 916G used: 495G (57%) fs: ext4 dev: /dev/sda1
RAID: No RAID devices: /proc/mdstat, md_mod kernel module present
Sensors: System Temperatures: cpu: 58.0C mobo: N/A
Fan Speeds (in rpm): cpu: N/A
Info: Processes: 380 Uptime: 2 days Memory: 5841.5/40153.3MB Client: Shell (bash) inxi: 2.3.56 

```

Any suggestions??
Thank you.

---

### Post by deadflowr on 2018-11-21
You're running the open source nouveau graphics driver.
You might get a cleaner result if you try the proprietary driver
You can install the driver by opening Software and Updates and got to the section Additional Drivers.
I think nvidia-390 supports your card.
Select a driver (your choice, as you might have more than one option, but as stated the 390 version should be supported for your card) and click Apply at the bottom of the box.
When done restart the system.

If it requires further tweaking, you should have a new program called nvidia server settings or something to that affect.
(It will show as a regular program in the program menu system)
If you open that you can set various options, then click on the save configuration button to save the settings.

---

### Post by dilip.h.n on 2018-11-21
I tried to install the driver by[COLOR=#000000] opening Software and Updates and got to the section Additional Drivers and after that, it is showing error as (image attached):

Even after typing the command 
```
 
sudo apt-get install -f
sudo dpkg --configure -a 
sudo apt-get clean

``` 

I get an error as:
[/COLOR]
```

dpkg: dependency problems prevent configuration of nvidia-driver-390:
nvidia-driver-390 depends on libnvidia-gl-390 (= 390.77-0ubuntu0.18.04.1); however:
Package libnvidia-gl-390:amd64 is not installed.


dpkg: error processing package nvidia-driver-390 (--configure):
dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libnvidia-ifr1-390:amd64:
libnvidia-ifr1-390:amd64 depends on libnvidia-gl-390; however:
Package libnvidia-gl-390:amd64 is not installed.


dpkg: error processing package libnvidia-ifr1-390:amd64 (--configure):
dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libnvidia-ifr1-390:i386:
libnvidia-ifr1-390:i386 depends on libnvidia-gl-390; however:
Package libnvidia-gl-390:i386 is not installed.


dpkg: error processing package libnvidia-ifr1-390:i386 (--configure):
dependency problems - leaving unconfigured
Errors were encountered while processing:
nvidia-driver-390
libnvidia-ifr1-390:amd64
libnvidia-ifr1-390:i386

```[COLOR=#000000]

I am getting the same error as "The package system is broken" in Software and Updates 

How to solve this.?

Any suggestions..??


[/COLOR]

---

