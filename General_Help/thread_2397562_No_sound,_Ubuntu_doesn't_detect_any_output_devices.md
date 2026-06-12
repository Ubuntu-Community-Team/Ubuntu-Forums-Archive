---
title: "No sound, Ubuntu doesn't detect any output devices"
date: 2018-07-31
forum: General Help
---

### Post by merkur0 on 2018-07-31
Hi.

So I just installed Ubuntu on my laptop (originally running Win 10) and since I installed it I had no sound in any app. When I go to "Settings" > "Sound" > "Output", it's empty, I don't see any devices there.How would I fix this?

Thanks in advance!

---

### Post by mIk3_08 on 2018-08-01
Hi merkur0. just want to know all about your hardware and what Ubuntu O.S you install in your machine so other people here in the Ubuntuforums may knows where to start fixing your system.
First, you have to install inxi in your Ubuntu system, to do that;
Open your terminal by pressing;
Ctrl + Alt + T
then type;
```
sudo apt-get install inxi
```
after successful installation of inxi;
in your terminal type the following command;
```
inxi -F
```
Then copy and paste the result of inxi -F here in thread wrap it with code.

---

### Post by merkur0 on 2018-08-02
Hi.

First of all, thanks for your reply. I was really starting to lose hope here.

Here is the output I get:
[HTML]
System:    Host: ondra-Lenovo-MIIX-320-10ICR Kernel: 4.15.0-29-generic x86_64           bits: 64           Desktop: Gnome 3.28.2 Distro: Ubuntu 18.04.1 LTSMachine:   Device: un-determined System: LENOVO product: 80XF v: Lenovo MIIX 320-10ICR serial: N/A           Mobo: LENOVO model: LNVNB161216 v: SDK0J91196WIN serial: N/A           UEFI: LENOVO v: 5HCN29WW date: 06/28/2017CPU:       Quad core Intel Atom x5-Z8350 (-MCP-) cache: 1024 KB           clock speeds: max: 1920 MHz 1: 1163 MHz 2: 1406 MHz 3: 922 MHz           4: 912 MHzGraphics:  Card: Intel Atom/Celeron/Pentium Processor x5-E8000/J3xxx/N3xxx Series PCI Configuration Registers           Display Server: x11 (X.Org 1.19.6 )           drivers: fbdev (unloaded: modesetting,vesa)           Resolution: 1200x1920@60.00hz           OpenGL: renderer: Mesa DRI Intel HD Graphics (Cherrytrail)           version: 4.5 Mesa 18.0.5Audio:     Card-1 Intel HDMI/DP LPE Audio driver: HdmiLpeAudio           Card-2 chtrt5645 driver: chtrt5645           Sound: Advanced Linux Sound Architecture v: k4.15.0-29-genericNetwork:   Card: Intel Wireless 3165 driver: iwlwifi           IF: wlp1s0 state: up mac: b0:35:9f:cc:ca:77Drives:    HDD Total Size: NA (-)           ID-1: /dev/mmcblk0 model: N/A size: 125.1GBPartition: ID-1: / size: 114G used: 9.1G (9%) fs: ext4 dev: /dev/mmcblk0p2RAID:      No RAID devices: /proc/mdstat, md_mod kernel module presentSensors:   System Temperatures: cpu: 63.0C mobo: N/A           Fan Speeds (in rpm): cpu: N/AInfo:      Processes: 270 Uptime: 42 min Memory: 1658.5/3808.6MB           Client: Shell (bash) inxi: 2.3.56 [/HTML]

---

### Post by Yellow Pasque on 2018-08-03
There's some discussion here:
[https://machek.systems/debian-buster-on-lenovo-miix-320/](https://machek.systems/debian-buster-on-lenovo-miix-320/)
This page suggests sound works without modification:
[https://esc.sh/blog/linux-on-lenovo-miix-320/](https://esc.sh/blog/linux-on-lenovo-miix-320/)
*Shrug*

---

