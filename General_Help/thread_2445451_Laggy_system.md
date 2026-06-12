---
title: "Laggy system"
date: 2020-06-14
forum: General Help
---

### Post by ff300 on 2020-06-14
Hello everyone, this is my first time posting here so I hope I'm in the right section.

So, my problem. When I power on my pc everything's fine, and there's no sign of lag at all. I can use any program without an issue, including the terminal, file manager, the text editor Atom, PDF viewer and even Firefox. The problem is that, after some time, the system get "compromised" and anything becomes laggy. Lighter programs are less laggy, so the terminal almost doesn't lag at all, while graphical applications lags in rendering, and Firefox takes seconds to react (for instance, changing tab, or opening a mail on Gmail). The only way I found to get rid of this lag is a reboot, but the issue is back in no time.

What I found so far (I know it's a wot, but I've tried and learned a lot of things).

[LIST]
[*]The main cause of "compromision" (is that even a word?) are graphical intensive programs. I can use the pc for hours without any sign of such lag, but limiting my usage to terminal, file browsing, easy-to-render PDFs, and so on. Once I open Firefox and render some "heavy" page (Gmail is enough) the system is gone, and at that point anything suffers, even terminal (sometimes I see the classical sliding horizontal line when rendering htop, even though it's fully reactive). Another way to "compromise" it is opening a PDF of images: for instances, one made of about 30-40 scans "compromised" the system the same as Firefox. I think that's because it tries to load all the images/create thumbnails, and this causes the issue. 
[*]The "compromision" manifest in high and odd CPU usage. When running smoothly, Firefox on idle takes about 5% CPU on each core (I have 4), but when the system is "compromised" it takes about 40% of a single CPU. Similarly, on rendering it may take a lot of processing power, but way more compressed on a single CPU when the system is compromised (some approximate figures: normally it takes 70-80% of each processor, but when "compromised" it takes 100% of one and about 20-30% of the others. This my be the cause of the lag, too). This behavior applies for other programs as well: mpv (a video player), Atom, Evince. Important notes: the figures are taken empirically looking at htop, and the CPU usage displayed by htop is far higher than the sum of the CPU% column. I have no idea as how to interpret this. Another possibly important point is that the CPU temperature increases: is around 40°C in "normal" state, but never goes below 50°C when the system is "compromised". 
[*]The "compromision" doesn't go away when I close the program that caused it. Even if log out and in again, the problem persists. I even tried a "killall -u <my username>", but that didn't work either. 
[*]The "compromision" is not an hardware (only) problem: I have dual boot, and Windows runs smoothly. Moreover, I've used this laptop for about 4 years with various Ubuntu and Debian releases, and this problem showed only in the last year. However I can't exclude any hardware compatibility problem. I also have a GPU, but as I said I had no such issue even with Debian 9 without its drivers. 
[*]It's not a problem of my installation, of the specific OS flavor nor of the DE. I started having this problem with Kubuntu 19.04, so I tried Debian 10 (with both KDE and Xfce), Xubuntu 18.04 (both Xfce and Openbox) and now I'm running Lubuntu 20.04. All these showed the very same issue. Right now I'm on Openbox, but also Lxqt and the default Lubuntu session have it. 
[*]I don't think it's a graphical issue, because it slows down everything (for instance, also starting a new shell takes some time, while normally it doesn't); graphics is just the thing on which the laggyness is more evident. 
[*]The problem isn't fully deterministic: there have been (incredibly rare) times where everything ran smoothly until the poweroff, but on the next boot the issue was back. 
[/LIST]
 
What I haven't checked yet: if non-graphical heavy programs can "compromise" the system as well, and if non Debian-based distributions have the same problem.

I've been looking into this for a lot of time, but on the web I couldn't find anything useful, mainly because I couldn't really find my specific issue (I don't know how to search for it), so I decided to ask here. Any proposal is welcome, and thanks in advance for whoever will read the whole wot.

---

### Post by CelticWarrior on 2020-06-14
Welcome.

I think the main question to start is do you have Nvidia graphics? If you do then whether or not you have the Nvidia proprietary drivers installed.

---

### Post by ajgreeny on 2020-06-14
As CelticWarrior has suggested but not specifically asked for, it will be extremely helpful to know a lot more about your hardware, so please show us the output of terminal command ***inxi -Fzx***

Please use **Code-Tags** for terminal output as it makes that output much more easily read and understood, formatting the text as seen in terminal, not as plain text when it is copied and pasted. See my signature below for a **How-to**

---

### Post by ff300 on 2020-06-15
Thanks a lot for the replies! Here's my hardware:
```

System:    Kernel: 5.4.0-33-generic x86_64 bits: 64 compiler: gcc v: 9.3.0 Desktop: Openbox 3.6.1 
           Distro: Ubuntu 20.04 LTS (Focal Fossa) 
Machine:   Type: Laptop System: Acer product: TravelMate P258-MG v: V1.10 serial: <filter> 
           Mobo: Acer model: BA50_SL v: V1.10 serial: <filter> UEFI: Insyde v: 1.10 date: 11/27/2015 
Battery:   ID-1: BAT1 charge: 27.0 Wh condition: 27.0/37.0 Wh (73%) model: SANYO AL15A32 status: Full 
           Device-1: hidpp_battery_0 model: Logitech Wireless Keyboard charge: 55% (should be ignored) status: Discharging 
CPU:       Topology: Dual Core model: Intel Core i7-6500U bits: 64 type: MT MCP arch: Skylake rev: 3 L2 cache: 4096 KiB 
           flags: avx avx2 lm nx pae sse sse2 sse3 sse4_1 sse4_2 ssse3 vmx bogomips: 20799 
           Speed: 500 MHz min/max: 400/3000 MHz Core speeds (MHz): 1: 500 2: 500 3: 501 4: 500 
Graphics:  Device-1: Intel Skylake GT2 [HD Graphics 520] vendor: Acer Incorporated ALI driver: i915 v: kernel bus ID: 00:02.0 
           Device-2: NVIDIA GK208BM [GeForce 920M] vendor: Acer Incorporated ALI driver: nouveau v: kernel bus ID: 01:00.0 
           Display: server: X.Org 1.20.8 driver: modesetting unloaded: fbdev,vesa resolution: 1366x768~60Hz, 1920x1080~60Hz 
           OpenGL: renderer: Mesa Intel HD Graphics 520 (SKL GT2) v: 4.6 Mesa 20.0.4 direct render: Yes 
Audio:     Device-1: Intel Sunrise Point-LP HD Audio vendor: Acer Incorporated ALI driver: snd_hda_intel v: kernel 
           bus ID: 00:1f.3 
           Device-2: NVIDIA GK208 HDMI/DP Audio vendor: Acer Incorporated ALI driver: snd_hda_intel v: kernel bus ID: 01:00.1 
           Device-3: Generalplus USB Audio Device type: USB driver: hid-generic,snd-usb-audio,usbhid bus ID: 1-1:2 
           Sound Server: ALSA v: k5.4.0-33-generic 
Network:   Device-1: Realtek RTL8111/8168/8411 PCI Express Gigabit Ethernet vendor: Acer Incorporated ALI driver: r8169 
           v: kernel port: 3000 bus ID: 02:00.0 
           IF: enp2s0 state: up speed: 100 Mbps duplex: full mac: <filter> 
           Device-2: Intel Wireless 7265 driver: iwlwifi v: kernel port: 3000 bus ID: 03:00.0 
           IF: wlp3s0 state: down mac: <filter> 
Drives:    Local Storage: total: 1.14 TiB used: 30.44 GiB (2.6%) 
           ID-1: /dev/sda vendor: LITE-ON model: CV1-CC256 size: 238.47 GiB 
           ID-2: /dev/sdb vendor: HGST (Hitachi) model: HTS721010A9E630 size: 931.51 GiB temp: 22 C 
Partition: ID-1: / size: 45.03 GiB used: 12.66 GiB (28.1%) fs: ext4 dev: /dev/sda8 
           ID-2: /home size: 42.63 GiB used: 17.78 GiB (41.7%) fs: ext4 dev: /dev/sda10 
           ID-3: swap-1 size: 4.00 GiB used: 0 KiB (0.0%) fs: swap dev: /dev/sda7 
Sensors:   System Temperatures: cpu: 37.5 C mobo: N/A gpu: nouveau temp: 39 C 
           Fan Speeds (RPM): N/A 
Info:      Processes: 216 Uptime: 3m Memory: 7.64 GiB used: 1.06 GiB (13.9%) Init: systemd runlevel: 5 Compilers: gcc: 9.3.0 
           Shell: bash v: 5.0.16 inxi: 3.0.38 

```
I have both an integrated Intel and an Nvidia graphic card, with the free drivers. I think it's worth mentioning that I had Nvidia proprietary drivers on Xubuntu 18.04, however I don't mind giving them a try if you think it may help.

---

### Post by CelticWarrior on 2020-06-15
Yes, it surely does help if you're using the Nvidia, hence my previous question.

---

### Post by ActionParsnip on 2020-06-15
It's that switching GPU hack. You'll need to look into Prime or Optimus (I forget which it is) to support that

---

### Post by CelticWarrior on 2020-06-15
> **ActionParsnip said:**
> It's that switching GPU hack. You'll need to look into Prime or Optimus (I forget which it is) to support that

Yes.

Installing the current Nvidia drivers should be enough.

---

### Post by ff300 on 2020-06-15
I installed the latest Nvidia drivers (440) and now it seems to work :D! I hope this lasts (I'm positive I did the very same on Xubuntu 18.04), but for now thanks a lot!

---

### Post by ajgreeny on 2020-06-15
Great news! Please mark as SOLVED from the Thread Tools menu up-top if this is now really solved to your satisfaction. 

It is a great help to other users searching the forum.

---

### Post by HermanAB on 2020-06-15
Note that if you installed OpenGL, then you can test the graphics performance using the utility 'gears' (part of mesa-utils) to give you some idea of whether the system is installed properly and working as expected.

---

### Post by ff300 on 2020-06-16
Ok, it seems I was optimistic. The issue isn't gone, it just takes a little more time to show up. Everything is as I said in the first post :(. Sorry to bother you again.
By the way I remembered I experienced more or less the same when installing Nvidia drivers on the previous Xubuntu.

The gears of glxgears run smoothly and without lag; however running it heats up the pc (I assume it's because of the GPU) and the output on the command line is somewhat strange - I don't think my monitor runs at 300 FPS
```

$ glxgears
Running synchronized to the vertical refresh.  The framerate should be
approximately the same as the monitor refresh rate.
1545 frames in 5.0 seconds = 308.569 FPS
1475 frames in 5.0 seconds = 294.951 FPS
1578 frames in 5.0 seconds = 315.349 FPS
1553 frames in 5.0 seconds = 310.537 FPS
1521 frames in 5.0 seconds = 304.125 FPS
1537 frames in 5.0 seconds = 307.280 FPS
1552 frames in 5.0 seconds = 310.315 FPS
1562 frames in 5.0 seconds = 312.325 FPS

```

EDIT: right now the system is not lagging at all. I don't really know how to interpret this. It may be worth noting that I had a reboot between the previous statement and this one.

---

### Post by ortollj on 2020-06-20
Hi
something I noticed on Ubuntu 18.04 , it seems  that the amount of swap  memory is never released once taken, and that this ultimately leads to  lag.

[URL="https://ask.sagemath.org/question/52065/little-code-which-produces-memory-overflow/"]https://ask.sagemath.org/question/52065/little-code-which-produces-memory-overflow/


Oops my post is inappropriate, the post was aboout Ubuntu 20

Sorry[/URL]

---

### Post by ff300 on 2020-07-06
Ok, I think I should at least mention this for whomever may find this thread in the future.
In the end I couldn't really solve the problem, so I decided to try out another distro (right now I'm on Manjaro, I'm not completely satisfied but I'm not disappointed either). On the new OS the issue is gone, so I'm confident it's something related to Debian-based OSes. For the time being I'm going to stick to Manjaro, I guess I'll come back to Ubuntu when I'll change the hw.
I'm marking this as solved, even though I don't think its exactly the case.

---

