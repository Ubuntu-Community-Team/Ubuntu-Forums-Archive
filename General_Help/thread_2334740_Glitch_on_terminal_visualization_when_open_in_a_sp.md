---
title: "Glitch on terminal visualization when open in a specific folder"
date: 2016-08-22
forum: General Help
---

### Post by alessandro-mininno on 2016-08-22
Good morning,
I have Ubuntu 16.04 LTS on a Toshiba Satellite and for a while I have this problem on the terminal. When I am in a specific folder on my computer I have the terminal which show me 

myname (green) mypath (blue) $ mystring (white)

The problem is that when I press the up arrow to scroll the previous command, these command are not shown overwritten each one each times I press up arrow, but they are shown one on the left and one on the other side right (as in the figure) and I do not know how to fix this problem. 
Some of you have the solution to this problem?

Thanks in advance

---

### Post by MAFoElffen on 2016-08-23
???

Okay... Need more info. This is a Virtualization Support Section. Which would imply that you are using some kind of Hypervisor Host to run a VM Guest.

So, off the top of my head, the Toshiba Satellite family of laptops had over 10 models in that family that I know of. Whic model is yous and what are it's spec's? What is the OS of that Laptop?

Is the problem you are experiencing on that host, or in a VM Guest runing in a Hypervisor? If the later, what is the hypervisor? That later answer will give us an idea of what kind of remote display of the (possible) VM Guest.

---

### Post by alessandro-mininno on 2016-08-23
I'm sorry, maybe I chose the wrong section, because I have a dual-boot computer with a partition of Ubuntu 16.04 LTS. My computer is:

[h=1]Toshiba Satellite L50T-A-11P[/h]

[LIST]
[*]Windows 8 64-bit (pre-installato)

[*]Processore Intel® Core&#8482; i5-3230M di 3a generazione con Intel® Turbo Boost Technology 2.0
[*]39.6cm (15.6&#8221;)  , Toshiba TruBrite® HD TFT High Brightness touch display with 16 : 9 aspect ratio and LED backlighting
[*]Hard disk 500 GB
[*]Shining silver finish with stripe pattern, black keyboard
[*]4,096 (1x) MB, DDR3 RAM (1,600 MHz)
[*]NVIDIA® GeForce® GT 740M con Tecnologia CUDA&#8482; e Tecnologia NVIDIA® Optimus&#8482;
[*]massima durata : fino a 4h00min (Mobile Mark&#8482; 2012)
[*]Peso : starting at 2.55 kg
[*]lxpxh : 377.8 x 244.0 x 30.19 mm
[/LIST]

Tell me if I have to change section for my post. I'm sorry for this misunderstanding.

---

### Post by alessandro-mininno on 2016-08-23
Good morning,
I have Ubuntu 16.04 LTS on a Toshiba Satellite and for a while I have  this problem on the terminal. When I am in a specific folder on my  computer I have the terminal which show me 

myname (green) mypath (blue) $ mystring (white)

The problem is that when I press the up arrow to scroll the previous  command, these command are not shown overwritten each one each times I  press up arrow, but they are shown one on the left and one on the other  side right (as in the figure) and I do not know how to fix this problem.  
Some of you have the solution to this problem?

I have a dual-boot computer with a partition of Ubuntu 16.04 LTS. My computer is:

**Toshiba Satellite L50T-A-11P**


[LIST]
[*]Windows 8 64-bit (pre-installato) 
[*]Processore Intel® Core™ i5-3230M di 3a generazione con Intel® Turbo Boost Technology 2.0 
[*]39.6cm (15.6”)  , Toshiba TruBrite® HD TFT High Brightness touch display with 16 : 9 aspect ratio and LED backlighting 
[*]Hard disk 500 GB 
[*]Shining silver finish with stripe pattern, black keyboard 
[*]4,096 (1x) MB, DDR3 RAM (1,600 MHz) 
[*]NVIDIA® GeForce® GT 740M con Tecnologia CUDA™ e Tecnologia NVIDIA® Optimus™ 
[*]massima durata : fino a 4h00min (Mobile Mark™ 2012) 
[*]Peso : starting at 2.55 kg 
[*]lxpxh : 377.8 x 244.0 x 30.19 mm 
[/LIST]


Thanks in advance

---

### Post by wildmanne39 on 2016-08-23
Please do not post duplicates, it dilutes community effort. Threads merged

If you want to move a thread use the report button in the lower left hand corner of your post and the staff will review your request.
Thanks

---

### Post by alessandro-mininno on 2016-08-23
Ok, I'm sorry, I'm a beginner in this forum. I should have read better the rules. Thanks to have moved my post in General Help and I hope some of you will find a solution to this "problem"

Thanks

---

### Post by ventrical on 2016-08-23
Are you using nVidia driver or nouveau?

Seeing that you have Optimus is that may be a problem.

Regards..

```

sudo apt-get install inxi

```

run 

inxi -Fxz 

and try to copy and paste to forums.

---

### Post by alessandro-mininno on 2016-08-25
System:    Host: alessandro-SATELLITE-L50t-A Kernel: 4.4.0-34-generic x86_64 (64 bit gcc: 5.3.1)
           Desktop: Unity 7.4.0 (Gtk 3.18.9-1ubuntu3.1)
           Distro: Ubuntu 16.04 xenial
Machine:   System: TOSHIBA (portable) product: SATELLITE L50t-A v: PSKL6E-00J00NIT
           Mobo: TOSHIBA model: Portable PC v: MP
           Bios: Insyde v: 1.40 date: 04/28/2014
CPU:       Dual core Intel Core i5-3230M (-HT-MCP-) cache: 3072 KB
           flags: (lm nx sse sse2 sse3 sse4_1 sse4_2 ssse3 vmx) bmips: 10375
           clock speeds: max: 3200 MHz 1: 1199 MHz 2: 1199 MHz 3: 1202 MHz
           4: 1201 MHz
Graphics:  Card-1: Intel 3rd Gen Core processor Graphics Controller
           bus-ID: 00:02.0
           Card-2: NVIDIA GK208M [GeForce GT 740M] bus-ID: 07:00.0
           Display Server: X.Org 1.18.3 driver: nvidia
           Resolution: 1366x768@60.00hz
           GLX Renderer: GeForce GT 740M/PCIe/SSE2
           GLX Version: 4.5.0 NVIDIA 361.45.18 Direct Rendering: Yes
Audio:     Card Intel 7 Series/C210 Series Family High Definition Audio Controller
           driver: snd_hda_intel bus-ID: 00:1b.0
           Sound: Advanced Linux Sound Architecture v: k4.4.0-34-generic
Network:   Card-1: Qualcomm Atheros AR8161 Gigabit Ethernet
           driver: alx port: 2000 bus-ID: 08:00.0
           IF: enp8s0 state: down mac: <filter>
           Card-2: Qualcomm Atheros QCA9565 / AR9565 Wireless Network Adapter
           driver: ath9k bus-ID: 09:00.0
           IF: wlp9s0 state: up mac: <filter>
Drives:    HDD Total Size: 500.1GB (8.9% used)
           ID-1: /dev/sda model: HGST_HTS545050A7 size: 500.1GB temp: 37C
Partition: ID-1: / size: 37G used: 16G (47%) fs: ext4 dev: /dev/sda8
           ID-2: /home size: 101G used: 25G (26%) fs: ext4 dev: /dev/sda11
           ID-3: swap-1 size: 1.00GB used: 0.00GB (0%) fs: swap dev: /dev/sda9
RAID:      No RAID devices: /proc/mdstat, md_mod kernel module present
Sensors:   System Temperatures: cpu: 61.0C mobo: N/A gpu: 0.0:55C
           Fan Speeds (in rpm): cpu: N/A
Info:      Processes: 241 Uptime: 1:14 Memory: 1734.9/3833.8MB
           Init: systemd runlevel: 5 Gcc sys: 5.4.0
           Client: Shell (bash 4.3.461) inxi: 2.2.35

---

