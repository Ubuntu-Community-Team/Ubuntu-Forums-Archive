---
title: "Can't Display 1080p in Multi Monitor"
date: 2018-08-09
forum: General Help
---

### Post by blue822 on 2018-08-09
I have a All-in-One PC and i have it connected to my TV that displays 1080p.  I can't get Ubuntu to get passed 1024X768, there's no option for it.

---

### Post by NM5TF on 2018-08-09
more info is needed to even begin to help you....we do not have access to your PC, so you must help us help you...

specifically:
    what hardware do you have ?
    graphics card ???
    OS version ???
etc....

can you post the output of

```
inxi -F
```

you will most likely have to install inxi first...

```
sudo apt-get install inxi
```

tommy

---

### Post by blue822 on 2018-08-09
```
Host: BLUE Kernel: 4.15.0-30-generic x86_64 bits: 64
           Desktop: Gnome 3.28.2 Distro: Ubuntu 18.04.1 LTS
Machine:   Device: desktop System: Sony product: VPCL135FX v: C6U1JUTN serial: N/A
           Mobo: Sony model: VAIO serial: N/A
           BIOS: American Megatrends v: R2040T5 date: 05/14/2010
CPU:       Quad core Intel Core2 Quad Q8400 (-MCP-) cache: 2048 KB
           clock speeds: max: 2670 MHz 1: 1992 MHz 2: 1992 MHz 3: 2006 MHz
           4: 2002 MHz
Graphics:  Card: NVIDIA GT216M [GeForce GT 330M]
           Display Server: x11 (X.Org 1.19.6 )
           drivers: nvidia (unloaded: modesetting,fbdev,vesa,nouveau)
           Resolution: 1024x768@60.00hz
           OpenGL: renderer: GeForce GT 330M/PCIe/SSE2
           version: 3.3.0 NVIDIA 340.106
Audio:     Card-1 Intel 82801JI (ICH10 Family) HD Audio Controller
           driver: snd_hda_intel
           Card-2 DisplayLink driver: USB Audio
           Sound: Advanced Linux Sound Architecture v: k4.15.0-30-generic
Network:   Card-1: Intel 82567V-2 Gigabit Network Connection driver: e1000e
           IF: enp0s25 state: up speed: 1000 Mbps duplex: full
           mac: 54:42:49:69:3f:13
           Card-2: Qualcomm Atheros AR9285 Wireless Network Adapter (PCI-Express)
           driver: ath9k
           IF: wlp2s0 state: up mac: 78:dd:08:ea:53:6e
Drives:    HDD Total Size: 2000.4GB (1.2% used)
           ID-1: /dev/sda model: ST2000DX001 size: 2000.4GB
Partition: ID-1: / size: 459G used: 23G (6%) fs: ext4 dev: /dev/sda6
RAID:      No RAID devices: /proc/mdstat, md_mod kernel module present
Sensors:   System Temperatures: cpu: 36.0C mobo: N/A gpu: 45C
           Fan Speeds (in rpm): cpu: N/A
Info:      Processes: 259 Uptime: 54 min Memory: 2338.4/5896.6MB
           Client: Shell (bash) inxi: 2.3.56
```

---

### Post by QIII on 2018-08-09
Hello!

Please use code tags when posting terminal commands and output.

To do so, either:

1.  Click the # button above the text entry box, place your cursor between the code tags that appear, and type or paste your text.  Alternatively, type or paste your text, highlight it, and click the # button.

2.  Type [noparse]```
[/noparse] before your text and [noparse]
```[/noparse] following your text.  The square brackets are required.

Thanks!

---

### Post by NM5TF on 2018-08-09
I thought so.....you have a nvidia graphics card from 2010 with an out of date driver...think current driver is 390.xxx

look in the menu for something like "additional drivers" or whatever it's called now....see if there is a newer driver listed....if so, try it....

I had a similar problem with my old nvidia card as they have dropped support for their older cards....they want you to buy a newer card of course...

problem was solved by using the nouveau driver which is now standard for older cards....maybe it is listed in the "additional drivers" menu

tommy

---

### Post by blue822 on 2018-08-09
i switched to nouveau driver and it got even worse. any clues???

---

### Post by NM5TF on 2018-08-09
> **blue822 said:**
> i switched to nouveau driver and it got even worse. any clues???

very strange...my card is even older than yours (2007) & nouveau solved my display resolution that was stuck at 1024x768.....

post the output of 

```
xrandr
```

it should look something like this

```
[tommy@tommy ~]$ xrandr
Screen 0: minimum 320 x 200, current 1920 x 1080, maximum 4096 x 4096
VGA-1 connected 1920x1080+0+0 (normal left inverted right x axis y axis) 1600mm x 900mm
   1920x1080     60.00*+
   1366x768      59.79  
   1280x800      59.81  
   1280x720      60.00  
   1024x768      75.03    70.07    60.00  
   800x600       72.19    75.00    60.32  
   640x480       75.00    72.81    59.94  
   720x400       70.08  

```

depending upon the result, you might be able to force another resolution using xrandr options...

read about xrandr here [https://xorg-team.pages.debian.net/xorg/howto/use-xrandr.html]("https://xorg-team.pages.debian.net/xorg/howto/use-xrandr.html")

tommy

---

### Post by blue822 on 2018-08-09
Because im using a All-in-one PC i don't get HDMI output, only input.  Im using a adapter that connects usb to hdmi.  Originally i was using Ubuntu 14.xxx  and i would get 1080p on my TV but it was very sluggish so i used a low Resolution like 800x600 and that would fix the lag.  Couple of months ago i installed Ubuntu 18.xxx and when i connect y adapter, i dont get 720p or 1080p.  It works on the PC but when i connect to TV it wont get good resolutions which is weird cuz the older version 14.xx got 1080p, but it just lagged like crazy.  Also on Ubuntu 18.xx if i use proprietary video drivers and connect my adapter and try changing to the nouveau drivers it wont connect to my TV any more and vise versa.  I just Reinstalled Ubuntu right now so i think im just ganna quit right now and maybe get a PC next year; unless someone knows how to fix this.  Also i tried a bit of that xrandr but it did not display any HD resolutions.

---

### Post by blue822 on 2018-08-09
BTW aslo the adapter works on Windows completely fine. (Windows 7) i have dual boot

---

### Post by blue822 on 2018-08-09
Ok, so i was just ganna use the 1024x768 and i restarted and my TV would not pic up the HDMI Signal.  I must of messed with my PC for an hour trying to figure out what went wrong.  I disconnected my cables and restarted the whole procedure of connecting my adapter and choosing propriety drivers and screen resolution back again to 1024x768.  It was as if Ubuntu didnt save my settings or forgot???.  Then since i had did a reinstall my sound was not working for my headphones.  I checked for updates but nothing showed up.After another hour of messing around there was an update for my audio so i DLed it and my headphones worked again.  I restarted and my headphones stopped working.  

I have Ubuntu running right now with my TV and im ganna  leave it on over night and see if any updates pop up that will maybe fix the sound and maybe resolution.  I am so lost on what to do right now.

---

### Post by NM5TF on 2018-08-09
sorry I couldn't help more.....

according to the GEForce web site, your card has the capability to do what you want, but the OEM decides which
functions are included in their hardware....all comes down to the price as usual....

their web page also states you need an internal DVI to HDMI dongle and a special SPDIF audio cable from MOBO to graphics card

[https://www.geforce.com/hardware/notebook-gpus/geforce-gt-330m/specifications]("https://www.geforce.com/hardware/notebook-gpus/geforce-gt-330m/specifications")

tommy

---

