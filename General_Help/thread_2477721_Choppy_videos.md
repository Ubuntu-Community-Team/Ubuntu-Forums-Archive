---
title: "Choppy videos"
date: 2022-08-04
forum: General Help
---

### Post by flexeed on 2022-08-04
Videos are choppy at resolutions higher than 240p. I don't know what problem it could be. Attached image of the characteristics of the pc.

Also, is there a way to make the windows smaller? Since I have a maximum resolution of 1024x600 and the buttons to activate a window are hidden without being able to do anything.

Someone told me to run this command to share the result "inxi -Fxxxzr"

```

System:    Kernel: 5.4.0-122-generic x86_64 bits: 64 compiler: gcc v: 9.4.0 
           Desktop: LXQt 0.14.1 info: lxqt-panel wm: Openbox 3.6.1 dm: LightDM 1.30.0 
           Distro: Ubuntu 20.04.4 LTS (Focal Fossa) 
Machine:   Type: Laptop System: Coradir S.A. product: Coradir/ES10IS5 v: Clamshell 
           serial: <filter> Chassis: Intel Corporation type: 9 v: 0.1 serial: <filter> 
           Mobo: Intel model: Intel powered classmate PC v: Clamshell serial: <filter> 
           UEFI [Legacy]: Phoenix v: SPCDV10L.91A.0045.2013.0315.1545 date: 03/15/2013 
Battery:   ID-1: BAT1 charge: 20.9 Wh condition: 46.4/47.5 Wh (98%) volts: 10.7/10.8 
           model: ECS CMPC type: Li-ion serial: <filter> status: Discharging 
CPU:       Topology: Dual Core model: Intel Atom N2600 bits: 64 type: MT MCP arch: Saltwell 
           rev: 1 L2 cache: 512 KiB 
           flags: lm nx pae sse sse2 sse3 ssse3 bogomips: 12768 
           Speed: 639 MHz min/max: 600/1600 MHz Core speeds (MHz): 1: 1088 2: 864 3: 1119 
           4: 1190 
Graphics:  Device-1: Intel Atom Processor D2xxx/N2xxx Integrated Graphics vendor: Elite Systems 
           driver: gma500 v: N/A bus ID: 00:02.0 chip ID: 8086:0be1 
           Display: x11 server: X.Org 1.20.13 driver: modesetting unloaded: fbdev,vesa 
           resolution: 1024x600~60Hz 
           OpenGL: renderer: llvmpipe (LLVM 12.0.0 128 bits) v: 4.5 Mesa 21.2.6 compat-v: 3.1 
           direct render: Yes 
Audio:     Device-1: Intel NM10/ICH7 Family High Definition Audio vendor: Elite Systems 
           driver: snd_hda_intel v: kernel bus ID: 00:1b.0 chip ID: 8086:27d8 
           Sound Server: ALSA v: k5.4.0-122-generic 
Network:   Device-1: Realtek RTL810xE PCI Express Fast Ethernet vendor: Elite Systems 
           driver: r8169 v: kernel port: 3000 bus ID: 01:00.0 chip ID: 10ec:8136 
           IF: enp1s0 state: down mac: <filter> 
           Device-2: Realtek RTL8188CE 802.11b/g/n WiFi Adapter 
           vendor: AzureWave AW-NE139H Half-size Mini PCIe Card driver: rtl8192ce v: kernel 
           port: 2000 bus ID: 02:00.0 chip ID: 10ec:8176 
           IF: wlp2s0 state: up mac: <filter> 
Drives:    Local Storage: total: 298.09 GiB used: 25.27 GiB (8.5%) 
           ID-1: /dev/sda vendor: Toshiba model: MQ01ABF032 size: 298.09 GiB speed: 3.0 Gb/s 
           rotation: 5400 rpm serial: <filter> rev: 1A scheme: MBR 
Partition: ID-1: / size: 292.35 GiB used: 25.27 GiB (8.6%) fs: ext4 dev: /dev/sda1 
Sensors:   System Temperatures: cpu: 51.0 C mobo: N/A 
           Fan Speeds (RPM): N/A 
Repos:     Active apt repos in: /etc/apt/sources.list 
           1: deb [http://ar.archive.ubuntu.com/ubuntu/](http://ar.archive.ubuntu.com/ubuntu/) focal main restricted
           2: deb [http://ar.archive.ubuntu.com/ubuntu/](http://ar.archive.ubuntu.com/ubuntu/) focal-updates main restricted
           3: deb [http://ar.archive.ubuntu.com/ubuntu/](http://ar.archive.ubuntu.com/ubuntu/) focal universe
           4: deb [http://ar.archive.ubuntu.com/ubuntu/](http://ar.archive.ubuntu.com/ubuntu/) focal-updates universe
           5: deb [http://ar.archive.ubuntu.com/ubuntu/](http://ar.archive.ubuntu.com/ubuntu/) focal multiverse
           6: deb [http://ar.archive.ubuntu.com/ubuntu/](http://ar.archive.ubuntu.com/ubuntu/) focal-updates multiverse
           7: deb [http://ar.archive.ubuntu.com/ubuntu/](http://ar.archive.ubuntu.com/ubuntu/) focal-backports main restricted universe multiverse
           8: deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) focal-security main restricted
           9: deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) focal-security universe
           10: deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) focal-security multiverse
           No active apt repos in: /etc/apt/sources.list.d/jtaylor-ubuntu-keepass-bionic.list 
           No active apt repos in: /etc/apt/sources.list.d/teejee2008-ubuntu-ppa-bionic.list 
           Active apt repos in: /etc/apt/sources.list.d/vscode.list 
           1: deb [arch=amd64,arm64,armhf] [http://packages.microsoft.com/repos/code](http://packages.microsoft.com/repos/code) stable main
Info:      Processes: 203 Uptime: 3h 41m Memory: 1.92 GiB used: 1.52 GiB (79.0%) Init: systemd 
           v: 245 runlevel: 5 Compilers: gcc: N/A Shell: bash v: 5.0.17 running in: qterminal 
           inxi: 3.0.38

```

Thanks.

---

### Post by Holger_Gehrke on 2022-08-04
Most Desktop Environments for Ubuntu allow Alt-dragging windows - put the pointer somewhere in the window you want to move, hold the Alt-key, hold the left mouse button and drag the window; rinse and repeat until you can access whatever part of the window you need to access. Some Environments also allow Alt-right-dragging (same procedure but with the right mouse button) to resize windows even if none of the edges is on screen. Don't know whether LXQt is one of those.

If the video driver doesn't support hardware accelerated decoding of whatever codec your videos are encoded in then decoding will be done by the CPU, and even with highly optimized code there are limits ... You don't mention what video player(s) you've tried, there are differences. I believe you're running LUbuntu and that comes with VLC as it's standard video and audio player. VLC is quite good, but on weaker machines 'mpv' - possibly with 'smplayer' as a frontend (mpv is a keyboard controlled player that's normally started from the command line with (lots and lots of) options; smplayer gives it a slightly friendlier interface) - might perform a bit better.

Holger

---

### Post by Yellow Pasque on 2022-08-04
Ughhh. GMA3600/Cedarview graphics. Unfortunately, there is not much you can do other than getting a better device or running Windows. Intel licensed PowerVR graphics for this series of chips, and they didn't provide any kind of video decode acceleration, which is badly needed on a CPU so weak.

Sorry to be the bearer of bad news..

---

### Post by guiverc on 2022-08-04
Check you have ***swap*** enabled on your system?

Your details imply a *[heavily*] modified Lubuntu 20.04 LTS system to me, possibly even a 18.04/LXDE system that was *release-upgraded* to *modern *Lubuntu/LXQt thus containing extra GUI/desktop problems that can cause *degraded *performance (*why release notes said to clean install*).  Note: I don't know, just some of your details match a Lubuntu 20.04 LTS, other details don't instead matching an *unsupported* upgrade which could also just be you replacing *default* components with ones you prefer too.

Do you have ***swap*** enabled & running.  It wasn't *default* for a Lubuntu 20.04 LTS install, but was available if users manually used it on releases from 18.10 -> 20.10.  Enabling swap can improve performance too (*quite significantly too if your machine lacks resources*).  The following maybe helpful - [https://discourse.lubuntu.me/t/how-to-create-a-swapfile-in-lubuntu-20-04-20-10/1959](https://discourse.lubuntu.me/t/how-to-create-a-swapfile-in-lubuntu-20-04-20-10/1959)

---

### Post by TheFu on 2022-08-05
> **Yellow Pasque said:**
> Ughhh. GMA3600/Cedarview graphics. Unfortunately, there is not much you can do other than getting a better device or running Windows. Intel licensed PowerVR graphics for this series of chips, and they didn't provide any kind of video decode acceleration, which is badly needed on a CPU so weak.

Sorry to be the bearer of bad news..

Atom CPUs are crap for video stuff. That leaves the hardware and drivers to handle it, which requires that the video stream/format/codec be one that can be decoded for playback in the GPU hardware AND supported by the driver. That iGPU is from the 2014 timeframe when most computers had moved to much better iGPUs (using the i915 driver).  That's why chromebooks from 2012 can platback 720p hidef video extremely well.  It is all in the iGPU + drivers that support hardware decoding of h.264 or mpeg2 video.

So, you need to figure out what the source video uses for the storage video codec and see if there isn't a way to ask the streaming service to convert those videos to a supported format for your system.

Or course, there is an easier answer.  For US$75, you can buy a used chromebook which is faster than the computer you have now and designed to play most h.264/vp8 video.  Any raspberry pi v2 or v3 can play h.264 videos at 1080p resolutions too.  The r-pi gpu has that support built-into the hardware.

I had an Atom N2700 Asus Eee back in 2011 and all the video decoding was performed by the CPU.  The iGPU was nearly useless.  The best it could handle was DVD resolution (480p).  I got a Celeron 2995U based chromebook and it easily handled all 720p video in mpeg2 or h.264/vp8 formats. Easily.  I wiped ChromeOS and put Lubuntu on it. Worked great and was a 3x performance increase over the Eee.

As for moving windows around, just grab any of the non-corner window borders and drag them where you like.  Openbox is the WM being used and it works this way. Resizing can only happen in the corners, but moving can be on any of the 4 sides, away from the corners.

---

### Post by poorguy on 2022-08-05
> **flexeed said:**
> 

```


Info:      Processes: 203 Uptime: 3h 41m Memory: 1.92 GiB used: 1.52 GiB (79.0%) Init: systemd 
          

```



The first problem I see is only 1.92 GB of memory and in my experience that just ain't enough to run a browser streaming videos.

I would also go into the browser settings and disable hardware acceleration.

---

### Post by TheFu on 2022-08-05
> **poorguy said:**
> The first problem I see is only 1.92 GB of memory and in my experience that just ain't enough to run a browser streaming videos.

I would also go into the browser settings and disable hardware acceleration.

Depends on the browser and the amount of swap.  With 4.1G of swap, I never had issues with most streaming video on a 2011 Acer C720 chromebook with 2GB of RAM.

---

