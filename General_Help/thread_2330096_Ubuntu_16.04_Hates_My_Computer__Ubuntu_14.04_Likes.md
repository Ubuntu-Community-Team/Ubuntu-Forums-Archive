---
title: "Ubuntu 16.04 Hates My Computer / Ubuntu 14.04 Likes My Computer"
date: 2016-07-07
forum: General Help
---

### Post by poorguy on 2016-07-07
Hey All,

I have tried to install different Ubuntu 16.04 versions on a Dell XPS 200 (DXCO51) and no success at all. Gets to the Ubuntu screen with the dots and will stay there forever if I let it. 

Ubuntu 14.04 will install and runs like a champ on this computer and I have no problem with that as Ubuntu 14.04 was my first Linux distro.

My question is Ubuntu 16.04 more resource demanding that it won't install?

Here are the system specs and yes it is 10+ years old.

thomas@Dell-XPS-200:~$ inxi -Fx
System:    Host: Dell-XPS-200 Kernel: 3.13.0-91-generic i686 (32 bit, gcc: 4.8.4) Desktop: Gnome Distro: Ubuntu 14.04 trusty
Machine:   System: Dell product: Dell DXC051
           Mobo: Dell model: 0DD431 Bios: Dell version: A03 date: 10/28/2005
CPU:       Dual core Intel Pentium D CPU (-MCP-) cache: 1024 KB flags: (lm nx pae sse sse2 sse3) bmips: 11171.7 
           Clock Speeds: 1: 2792.931 MHz 2: 2792.931 MHz
Graphics:  Card: NVIDIA GT216 [GeForce 210] bus-ID: 01:00.0 
           X.Org: 1.15.1 drivers: nouveau (unloaded: fbdev,vesa) Resolution: 1280x720@60.0hz 
           GLX Renderer: Gallium 0.4 on NVA5 GLX Version: 3.0 Mesa 10.1.3 Direct Rendering: Yes
Audio:     Card-1: Intel NM10/ICH7 Family High Definition Audio Controller driver: snd_hda_intel bus-ID: 00:1b.0 
           Card-2: NVIDIA GT216 HDMI Audio Controller driver: snd_hda_intel bus-ID: 01:00.1 
           Sound: Advanced Linux Sound Architecture ver: k3.13.0-91-generic
Network:   Card: Intel NM10/ICH7 Family LAN Controller driver: e100 ver: 3.5.24-k2-NAPI port: ccc0 bus-ID: 03:08.0
           IF: eth0 state: up speed: 100 Mbps duplex: full mac: 00:12:3f:b1:6a:ab
Drives:    HDD Total Size: 80.0GB (5.6% used) 1: id: /dev/sda model: ST380819AS size: 80.0GB 
Partition: ID: / size: 71G used: 4.2G (7%) fs: ext4 ID: swap-1 size: 3.22GB used: 0.00GB (0%) fs: swap 
RAID:      No RAID devices detected - /proc/mdstat and md_mod kernel raid module present
Sensors:   System Temperatures: cpu: No active sensors found. Have you configured your sensors yet? mobo: N/A gpu: 60.0 
Info:      Processes: 167 Uptime: 38 min Memory: 622.2/3028.3MB Runlevel: 2 Gcc sys: 4.8.4 
           Client: Shell (bash 4.3.11) inxi: 1.9.17 

Thanks

---

### Post by mastablasta on 2016-07-08
try nomodeset boot option at boot and then install nvidia drivers once system is up and running.

more on boot options: [https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

---

### Post by poorguy on 2016-07-08
Hey mastablasta,

This was originally posted in the Ubuntu Linux and OS Chat section and was moved to the General Help section.  
 This is my fault for not stating in my original post that I have Ubuntu 14.04 installed and running happily and wasn't seeking help for installing Ubuntu 16.04. 

I was just wondering as to what the reason may be as to why Ubuntu 16.04 was not getting past the start up screen as most of my computers are five to ten years old this is a first time I have encountered this problem.

I'm wondering if my old hardware may not be supported by the 16.04 kernel since Ubuntu 14.04 installed and runs great with just the open source Nouveau graphics driver. 
Even Google Earth runs excellent and for me that is a plus since Ubuntu 16.04 doesn't appear to support Google Earth in my experience.

Thanks for the input to try nomodeset boot option as I have never have had to use that option.
I will say I am learning a lot about new Linux releases and problems that can occur with them.

Thanks.

The PoorGuy

---

