---
title: "synaptic, document viewer, multimedia will not open/work"
date: 2016-05-10
forum: General Help
---

### Post by halfprice5 on 2016-05-10
Per the title these applications will not work. I have tried searching and have tried the solutions I have found, still not working

What I have tried,

sudo apt-get update && sudo apt-get upgrade
sudo dpkg --configure -a
sudo apt-get autoclean
sudo apt-get clean
sudo apt-get autoremove
sudo apt-get update && sudo apt-get upgrade

No joy, suggestions?

---

### Post by QDR06VV9 on 2016-05-10
Just a bit too vague..Some more relevant information will help you get the answer you need.
What version are you using.
```
lsb_release -a
```
And anything you did before this happened.

---

### Post by halfprice5 on 2016-05-10
14.04.4 LTS

Its my wife’s computer, so I do not know nor does she what might have caused the problem

It was a tough install, hardware conflict with the video card. That was solved by installing an nvidia video card.

Thank you for your help

---

### Post by halfprice5 on 2016-05-10
I have no reason to stay with 14.04.4 LTS if if 16.04 LTS would solve the problem by upgrading

---

### Post by QDR06VV9 on 2016-05-10
if 16.04 LTS would solve the problem by upgrading... and that would be a good question?
Are you setting in front of her machine now?

---

### Post by halfprice5 on 2016-05-10
can be its right here

---

### Post by halfprice5 on 2016-05-10
At the troubled computer now.

---

### Post by QDR06VV9 on 2016-05-10
Ok great.
Lets do this if you would.
```
sudo apt install inxi
```
and after it is installed post back the output of this in the terminal
```
inxi -Fxz 
```
Then we should have enough info for you to upgrade or not.

---

### Post by halfprice5 on 2016-05-10
done

---

### Post by halfprice5 on 2016-05-10
```
System:    Host: kep-HP-xw4600-Workstation Kernel: 3.19.0-59-generic i686 (32 bit, gcc: 4.8.2) 
           Desktop: Gnome Distro: Ubuntu 14.04 trusty
Machine:   System: Hewlett-Packard product: HP xw4600 Workstation
           Mobo: Hewlett-Packard model: 0AA0h Bios: Hewlett-Packard version: 786F3 v01.16 date: 02/19/2009
CPU:       Quad core Intel Core2 Quad CPU Q8300 (-MCP-) cache: 2048 KB flags: (lm nx pae sse sse2 sse3 sse4_1 ssse3) bmips: 19998.2 
           Clock Speeds: 1: 1998.00 MHz 2: 1998.00 MHz 3: 1998.00 MHz 4: 1998.00 MHz
Graphics:  Card: NVIDIA GT218 [GeForce 210] bus-ID: 01:00.0 
           X.Org: 1.17.1 drivers: nvidia (unloaded: fbdev,vesa,nouveau) Resolution: 1024x768@60.0hz, 1152x864@75.0hz 
           GLX Renderer: N/A GLX Version: N/A Direct Rendering: N/A
Audio:     Card-1: NVIDIA High Definition Audio Controller driver: snd_hda_intel bus-ID: 01:00.1 
           Card-2: C-Media driver: USB Audio usb-ID: 007-002 
           Sound: Advanced Linux Sound Architecture ver: k3.19.0-59-generic
Network:   Card: Broadcom NetXtreme BCM5755 Gigabit Ethernet PCI Express driver: tg3 ver: 3.137 bus-ID: 3f:00.0
           IF: eth0 state: up speed: 1000 Mbps duplex: full mac: <filter>
Drives:    HDD Total Size: 120.0GB (12.8% used) 1: id: /dev/sda model: CT120BX100SSD1 size: 120.0GB temp: 25C 
Partition: ID: / size: 103G used: 15G (15%) fs: ext4 ID: swap-1 size: 8.57GB used: 0.00GB (0%) fs: swap 
RAID:      No RAID devices detected - /proc/mdstat and md_mod kernel raid module present
Sensors:   System Temperatures: cpu: 36.0C mobo: N/A gpu: 0.0:52C 
           Fan Speeds (in rpm): cpu: N/A 
Info:      Processes: 196 Uptime: 2:45 Memory: 814.1/8082.8MB Runlevel: 2 Gcc sys: 4.8.4 
           Client: Shell (bash 4.3.11) inxi: 1.9.17
```

---

### Post by QDR06VV9 on 2016-05-10
Am I missing something here?
I do not see the out- put i need.
To copy from the terminal highlight the text in the terminal with your mouse and then using your keyboard pressing <Ctrl> and <Shift> and <c>
Then to paste it here in your post just use the keys <Ctrl +c>
Oh ok now I see it.

---

### Post by halfprice5 on 2016-05-10
```
System:    Host: kep-HP-xw4600-Workstation Kernel: 3.19.0-59-generic i686 (32 bit, gcc: 4.8.2) 
           Desktop: Gnome Distro: Ubuntu 14.04 trusty
Machine:   System: Hewlett-Packard product: HP xw4600 Workstation
           Mobo: Hewlett-Packard model: 0AA0h Bios: Hewlett-Packard version: 786F3 v01.16 date: 02/19/2009
CPU:       Quad core Intel Core2 Quad CPU Q8300 (-MCP-) cache: 2048 KB flags: (lm nx pae sse sse2 sse3 sse4_1 ssse3) bmips: 19998.2 
           Clock Speeds: 1: 1998.00 MHz 2: 1998.00 MHz 3: 1998.00 MHz 4: 1998.00 MHz
Graphics:  Card: NVIDIA GT218 [GeForce 210] bus-ID: 01:00.0 
           X.Org: 1.17.1 drivers: nvidia (unloaded: fbdev,vesa,nouveau) Resolution: 1024x768@60.0hz, 1152x864@75.0hz 
           GLX Renderer: N/A GLX Version: N/A Direct Rendering: N/A
Audio:     Card-1: NVIDIA High Definition Audio Controller driver: snd_hda_intel bus-ID: 01:00.1 
           Card-2: C-Media driver: USB Audio usb-ID: 007-002 
           Sound: Advanced Linux Sound Architecture ver: k3.19.0-59-generic
Network:   Card: Broadcom NetXtreme BCM5755 Gigabit Ethernet PCI Express driver: tg3 ver: 3.137 bus-ID: 3f:00.0
           IF: eth0 state: up speed: 1000 Mbps duplex: full mac: <filter>
Drives:    HDD Total Size: 120.0GB (12.8% used) 1: id: /dev/sda model: CT120BX100SSD1 size: 120.0GB temp: 25C 
Partition: ID: / size: 103G used: 15G (15%) fs: ext4 ID: swap-1 size: 8.57GB used: 0.00GB (0%) fs: swap 
RAID:      No RAID devices detected - /proc/mdstat and md_mod kernel raid module present
Sensors:   System Temperatures: cpu: 36.0C mobo: N/A gpu: 0.0:52C 
           Fan Speeds (in rpm): cpu: N/A 
Info:      Processes: 196 Uptime: 2:45 Memory: 814.1/8082.8MB Runlevel: 2 Gcc sys: 4.8.4 
           Client: Shell (bash 4.3.11) inxi: 1.9.17
```

---

### Post by QDR06VV9 on 2016-05-10
Your spec's show you should not have any problems installing 16.04
But before you do is her system fully updated? that might hold some answers.
```
sudo apt update
sudo apt upgrade
sudo apt full-upgrade
```
and post back any error's if there are any.
Also if there are no errors try running some of the broken apps you have mentioned to see if they now work.

---

### Post by halfprice5 on 2016-05-10
Looks to be up to date, i.e. 0 upgrades no errors apps sill do not run

---

### Post by QDR06VV9 on 2016-05-10
Hmm? That is very odd. Possibly a corrupt install then.
But if you wish to try 16.04 here is Ubuntu Unity download link [http://www.ubuntu.com/download/desktop](http://www.ubuntu.com/download/desktop)
Just choose the type you want 64 bit or 32 bit etc etc etc
Make sure you have a good back-up in place IE: any pictures, documents, music and family videos or anything you will miss.
if you have any other problems just post them here.

---

### Post by halfprice5 on 2016-05-10
I would believe a corrupt install it was difficult.

Thank you for your help

---

### Post by halfprice5 on 2016-05-11
16.04 installed without a problem.

Thanks again for your help

---

### Post by QDR06VV9 on 2016-05-11
> **halfprice5 said:**
> 16.04 installed without a problem.

Thanks again for your help

Nice.. very glad this was a good install.:D
If you would be kind enough to mark this as solved as to help others with similar problems.
Kind Regards

---

