---
title: "No video thumnails"
date: 2017-10-31
forum: General Help
---

### Post by meetdilip on 2017-10-31
Unity + 16.04. I cannot see any video thumbnails. Also, image thumbnails are also missing while browsing mounted devices like smart phone. Any work around available ?

---

### Post by ajgreeny on 2017-10-31
In nautilus the file manager go to the Edit menu (in the top bar, not in the window decoration title bar) and Preferences.
In the Preview tab you can choose to change the probable normal thumbnail setting from **Local files only** to **Always**.

That ought to change what you see, as far as I'm aware.

---

### Post by meetdilip on 2017-10-31
Thanks @ajgreeny

I just tried it. Set enable thumbnails for all files and for files less than 4GB. Restarted the PC a couple of times. Still, I am not getting video thumbnails. Neither on PC nor on mounted devices. :(

---

### Post by ajgreeny on 2017-10-31
In that case I have no idea what is not working for you, and unfortunately no way to test it.

---

### Post by meetdilip on 2017-11-01
I see. Hopefully, someone else would figure out. Thanks for trying.

---

### Post by vasa1 on 2017-11-01
I don't know what to make of it but:> Thumbnailing not working for video files
There is an ongoing issue with totem (the video thumbnailer for Nautilus) on computers with Intel GPUs. It will crash if gstreamer-vaapi is installed. Until this issue is resolved, it is recommended to remove this package.from [https://wiki.archlinux.org/index.php/GNOME/Files#Thumbnailing_not_working_for_video_files](https://wiki.archlinux.org/index.php/GNOME/Files#Thumbnailing_not_working_for_video_files)

I have Ubuntu 16.04 on a Dell laptop and that has an integrated GPU from Intel. I don't see thumbnails for videos either.

---

### Post by meetdilip on 2017-11-01
1. How to check whether gstreamer-vaapi is installed on my laptop ? It's a Dell as well running 16.04 + Unity. Will it break any other software if removed ? I don't know how to remove it either.

I think mine has an integrated GPU as well. It runs on an Intel i5 processor with 2 threads.

Thanks.

---

### Post by vasa1 on 2017-11-01
Install *inxi* and then post the output from ```
inxi -Fxzc0
```here.

I tried nemo and still no luck with video thumbnails.```
$ apt policy nemo
nemo:
  Installed: 2.8.6-2
  Candidate: 2.8.6-2
  Version table:
 *** 2.8.6-2 500
        500 http://archive.ubuntu.com/ubuntu xenial/universe amd64 Packages
        100 /var/lib/dpkg/status$ 
``````
apt list --installed | grep -i gstreamer
```will list all packages containing the string "gstreamer".

---

### Post by meetdilip on 2017-11-01
inxi output


```
$ inxi -Fxc0
System:    Host: dna-Vostro-3550 Kernel: 4.4.0-98-generic x86_64 (64 bit gcc: 5.4.0)
           Desktop: Unity 7.4.0 (Gtk 3.20.8-1ubuntu0~ppa1)
           Distro: Ubuntu 16.04 xenial
Machine:   System: Dell (portable) product: Vostro 3550
           Mobo: Dell model: 0PD77K v: A12 Bios: Dell v: A12 date: 02/18/2014
CPU:       Dual core Intel Core i5-2430M (-HT-MCP-) cache: 3072 KB
           flags: (lm nx sse sse2 sse3 sse4_1 sse4_2 ssse3 vmx) bmips: 9579
           clock speeds: max: 3000 MHz 1: 1482 MHz 2: 1631 MHz 3: 1227 MHz
           4: 2085 MHz
Graphics:  Card-1: Intel 2nd Generation Core Processor Family Integrated Graphics Controller
           bus-ID: 00:02.0
           Card-2: Advanced Micro Devices [AMD/ATI] Whistler [Radeon HD 6630M/6650M/6750M/7670M/7690M]
           bus-ID: 01:00.0
           Display Server: X.Org 1.18.4 drivers: ati,radeon,intel (unloaded: fbdev,vesa)
           Resolution: 1366x768@60.00hz
           GLX Renderer: Mesa DRI Intel Sandybridge Mobile
           GLX Version: 3.0 Mesa 17.0.7 Direct Rendering: Yes
Audio:     Card Intel 6 Series/C200 Series Family High Definition Audio Controller
           driver: snd_hda_intel bus-ID: 00:1b.0
           Sound: Advanced Linux Sound Architecture v: k4.4.0-98-generic
Network:   Card-1: Realtek RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
           driver: r8169 v: 2.3LK-NAPI port: d000 bus-ID: 05:00.0
           IF: eth0 state: down mac: <>
           Card-2: Broadcom BCM4313 802.11bgn Wireless Network Adapter
           driver: wl bus-ID: 09:00.0
           IF: wlan0 state: up mac: <>
Drives:    HDD Total Size: 500.1GB (56.6% used)
           ID-1: /dev/sda model: ST500LT012 size: 500.1GB
Partition: ID-1: / size: 129G used: 80G (66%) fs: ext4 dev: /dev/sda6
           ID-2: swap-1 size: 44.55GB used: 0.20GB (0%) fs: swap dev: /dev/sda5
RAID:      No RAID devices: /proc/mdstat, md_mod kernel module present
Sensors:   System Temperatures: cpu: 53.0C mobo: N/A gpu: N/A
           Fan Speeds (in rpm): cpu: N/A
Info:      Processes: 264 Uptime: 2:36 Memory: 2993.0/3857.3MB
           Init: systemd runlevel: 5 Gcc sys: 5.4.0
           Client: Shell (bash 4.3.481) inxi: 2.2.35


```

---

### Post by mc4man on 2017-11-01
If you don't have some of the gstreamer plugins installed then totem-thumbnailer can't decode so no thumbnails.
So install the main 3 - 
```
sudo apt install gstreamer1.0-libav gstreamer1.0-plugins-bad gstreamer1.0-plugins-ugly
```
After install go to ~/.cache/thumbnails & delete the fail folder.
Then check your video folder again, ect.

---

### Post by meetdilip on 2017-11-02
@mc4man , I tried the above and got the same situation again

While trying the command on terminal, I got this

> gstreamer1.0-libav is already the newest version (1.8.3-1ubuntu0.2).
gstreamer1.0-plugins-bad is already the newest version (1.8.3-1ubuntu0.2).
gstreamer1.0-plugins-bad set to manually installed.
gstreamer1.0-plugins-ugly is already the newest version (1.8.3-1ubuntu0.1).

---

