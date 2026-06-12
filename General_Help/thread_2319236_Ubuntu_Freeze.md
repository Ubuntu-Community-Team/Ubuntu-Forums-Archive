---
title: "Ubuntu Freeze"
date: 2016-04-02
forum: General Help
---

### Post by ads4 on 2016-04-02
Hi!

System: Ubuntu 14.04, AMD X2, 4GB RAM.

Ok so my OS is freezing from time to time, for example if use libre office or software manager installed tab etc. 

I found out that cpu is working 100% during freezes for about 10-15 seconds or so, and ram is low about 20%.

And I also found out that this is a very common problem, both on forum and google, and also obviosly for older systems such as 12.04.

I also found out that this problem did not occur at my former computer that was intel x2 on 14.04.

However I havent found a soulution, wich in my opinion either should be a manufacturing amd cpu problem, or more likely at ubuntu system.

Could someone please explain if this is occuring on other linux distro? and if this is some kind of "reported" bug for ubuntu? and what they are doing about it? and when it is to be solved?

---

### Post by v3.xx on 2016-04-02
Sounds like your running the Unity desktop.  I would of thought it to be ok on your system, but since its not..

Try installing a different desktop to test with. The Flashback desktop.
```
sudo apt-get install gnome-panel
```

And at the login screen choose Flashback (metacity) by clicking on the icon.  See if it will run any smoother.

I understand your equipment is old, but have you checked for additional video drivers?

---

### Post by ads4 on 2016-04-02
Thank you, I will try and see if it helps.

No all is by standard, settings and comupter is about 4 years old.

---

### Post by X-RED_Tech on 2016-04-02
What is the graphics card (or onboard)?

---

### Post by mikewhatever on 2016-04-02
> **ads4 said:**
> Hi!
...
Could someone please explain if this is occuring on other linux distro? and if this is some kind of "reported" bug for ubuntu? and what they are doing about it? and when it is to be solved?
Not sure what you want us to do:
Want to know if it happens with other distros? Test other distros.
What to know if it is a bug? Search for bugs, and read bug reports.

---

### Post by v3.xx on 2016-04-02
> **ads4 said:**
> comupter is about 4 years old.

Look for a video driver, it may be all you need.

Open up your sources and go to the additional driver tab.  Its in your menu or in terminal..

```
software-properties-gtk
```

---

### Post by him610 on 2016-04-02
Hello, and welcome to Ubuntu Forums. I too have a system with Athlon X2 and 4GB RAM.

When your system seems to freeze or lock up for short periods of time, it is an indication your system is stressed - having more demands on it than it is capable of handling in a timely fashion. 
This is not normal behavior, but in older systems using applications that place large demands on the cpu/gpu/ram, it is not uncommon.
Do you know if your AMD X2 CPU and your GPU happen to use shared system memory?

Could you please post the results of this command -
```
inxi -F
```

---

### Post by ads4 on 2016-04-08
> **hgh9mrp said:**
> Hello, and welcome to Ubuntu Forums. I too have a system with Athlon X2 and 4GB RAM.

When your system seems to freeze or lock up for short periods of time, it is an indication your system is stressed - having more demands on it than it is capable of handling in a timely fashion. 
This is not normal behavior, but in older systems using applications that place large demands on the cpu/gpu/ram, it is not uncommon.
Do you know if your AMD X2 CPU and your GPU happen to use shared system memory?

Could you please post the results of this command -
```
inxi -F
```



System:    Host: du Kernel: 3.19.0-56-generic x86_64 (64 bit) Desktop: Gnome Distro: Ubuntu 14.04 trusty
Machine:   System: Hewlett-Packard product: p6-2001sc
           Mobo: PEGATRON model: 2ACF version: 1.01 Bios: AMI version: 7.06 date: 08/16/2011
CPU:       Dual core AMD A4-3400 APU with Radeon HD Graphics (-MCP-) cache: 1024 KB flags: (lm nx sse sse2 sse3 sse4a svm) 
           Clock Speeds: 1: 800.00 MHz 2: 800.00 MHz
Graphics:  Card: Advanced Micro Devices [AMD/ATI] Caicos [Radeon HD 6450/7450/8450 / R5 230 OEM] 
           X.Org: 1.17.1 drivers: ati,radeon (unloaded: fbdev,vesa) Resolution: 1680x1050@59.9hz 
           GLX Renderer: Gallium 0.4 on AMD CAICOS GLX Version: 3.0 Mesa 10.5.9
Audio:     Card-1: Advanced Micro Devices [AMD] FCH Azalia Controller driver: snd_hda_intel 
           Card-2: Advanced Micro Devices [AMD/ATI] Caicos HDMI Audio [Radeon HD 6400 Series] driver: snd_hda_intel 
           Sound: Advanced Linux Sound Architecture ver: k3.19.0-56-generic
Network:   Card-1: Realtek RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller driver: r8169 
           IF: eth0 state: up speed: 100 Mbps duplex: full mac: 38:60:77:77:dd:cf
           Card-2: Ralink RT5390 Wireless 802.11n 1T/1R PCIe driver: rt2800pci 
           IF: wlan0 state: down mac: 74:de:2b:b0:cb:6e
Drives:    HDD Total Size: 750.2GB (0.8% used) 1: id: /dev/sda model: ST3750525AS size: 750.2GB 
Partition: ID: / size: 684G used: 5.7G (1%) fs: ext4 
RAID:      No RAID devices detected - /proc/mdstat and md_mod kernel raid module present
Sensors:   System Temperatures: cpu: 9.6C mobo: N/A gpu: 41.5 
           Fan Speeds (in rpm): cpu: N/A 
Info:      Processes: 195 Uptime: 4 min Memory: 587.5/3939.6MB Client: Shell (bash) inxi: 1.9.17

---

### Post by X-RED_Tech on 2016-04-13
It's an AMD APU (Integrated CPU+GPU on chip) so the proprietary drivers aren't exactly an option (you're running with the old open source Radeon which doesn't work properly with such hardware).
Now, read the post #6 again and install the recommended fglrx. People have been trying to make you understand this simple issue since last week.

---

### Post by ads4 on 2016-04-16
Ok thank you I will try it :)

---

