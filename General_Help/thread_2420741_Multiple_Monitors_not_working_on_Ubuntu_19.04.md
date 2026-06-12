---
title: "Multiple Monitors not working on Ubuntu 19.04"
date: 2019-06-10
forum: General Help
---

### Post by marcoppenheimer on 2019-06-10
Hi all, 

I've had a look through the forums and I couldn't find a solution, so please let me know if there's a solution thread! 

I'm very new to Ubuntu, bought a Dell XPS with 18.04 LTS preinstalled, recently upgraded to 19.04, and my dual monitor set-up no longer works correctly.  

I am connecting through an HDMI --> USB-c port for my laptop. 

The second monitor is detected, however will not work unless I lower the resolution of the second monitor to <1080p. 

I didn't have this problem with my laptop on 18.04 out the box. 

Is this a known problem? 
Is there a solution? 

Thanks!

---

### Post by TheFu on 2019-06-10
I cannot directly help with this specific issue. Sorry.

About non-LTS releases ...
When you are really new to Ubuntu, it is best to stay on LTS releases only.
New is the enemy of stable, as you've learned.
April of even years is when LTS releases happen.  14.04, 16.04, 18.04, 20.04 .... any other releases should be considered "technology demonstrations."  Expect things to fail.  17.10, they made Wayland the default display manager and at least 50 other things broke.  When they first introduced systemd, lots of stuff broke and much is still broken today, IMHO.  People have been struggling with non-trivial netplan configs, the new way to handle network setups.  Simple network setups work well, so most people aren't impacted.

If you can, go back to the 18.04 release you were using and maintain that until at least June-ish of 2020.  How to maintain an Ubuntu system?
```
sudo apt update
sudo apt dist-upgrade
sudo apt autoremove
sudo apt autoclean

```and 
run backups, at least once a week, keeping 2-3 months of versioned backups.
**Do those things once a week, to be happy.**

For other people to be able to help, they will need this information:
* The exact Dell laptop model.
* The exact release and kernel version.
* The exact GPU and GPU drivers.
* The exact monitors involved - model and any revision numbers.
* Perhaps specific information about the HDMI -to- USBc cable.

Much of this data can be gathered using **inxi -Fz**. Probably need to install that package. Post using [code tags]("https://blog.jdpfu.com/code_tags"), so it looks the same here as inside a terminal. Some information will need to be manually supplied, like the monitor and cable information.

Why I replied?
I have a 1200p VGA monitor that worked perfectly on older systems refuse to work higher than 1080p with a newer system that required a DVI-d -to- VGA active converter.  The converter was lying about the EDID capabilities so that only 1080p was offered to the GPU.  The monitor is definitely 1200p capable.  The active converter claimed it would work at 1200p, so I ended up manually cloning the monitor EDID information and feeding that into X/Windows using debug options for the nvidia GPU driver. Took me a few days to figure all that out.  For fault was in the DVI-d -to- VGA active converter, which I was forced to use because the new GPU I got didn't support VGA, just HDMI and DVI-d.

---

### Post by marcoppenheimer on 2019-06-11
This is fantastic advice. I had initially upgraded to 19.04 for the Gnome speed upgrades, but if it's worth waiting until 2020 then fine.  
It's comforting knowing that others had similar issues!! 

If there is no available solution for this, I might just backroll my laptop to factory settings and set up a cron job to run that code. 

My inxi output: 

```

System:    Host: [MYNAME]-XPS-13-9380 Kernel: 4.15.0-1039-oem x86_64 bits: 64 Desktop: Gnome 3.32.1 
           Distro: Ubuntu 19.04 (Disco Dingo) 
Machine:   Type: Laptop System: Dell product: XPS 13 9380 v: N/A serial: <filter> 
           Mobo: Dell model: 0KTW76 v: A00 serial: <filter> UEFI: Dell v: 1.4.0 date: 05/03/2019 
Battery:   ID-1: BAT0 charge: 3.2 Wh condition: 51.6/52.0 Wh (99%) 
CPU:       Topology: Quad Core model: Intel Core i7-8565U bits: 64 type: MT MCP L2 cache: 8192 KiB 
           Speed: 700 MHz min/max: 400/4600 MHz Core speeds (MHz): 1: 702 2: 711 3: 715 4: 700 5: 701 6: 700 7: 722 8: 702 
Graphics:  Device-1: Intel UHD Graphics 620 driver: i915 v: kernel 
           Display: x11 server: X.Org 1.20.4 driver: modesetting unloaded: fbdev,vesa resolution: 3840x2160~60Hz 
           OpenGL: renderer: Mesa DRI Intel HD Graphics (Whiskey Lake 3x8 GT2) v: 4.5 Mesa 19.0.2 
Audio:     Device-1: Intel driver: snd_hda_intel 
           Sound Server: ALSA v: k4.15.0-1039-oem 
Network:   Device-1: Qualcomm Atheros QCA6174 802.11ac Wireless Network Adapter driver: ath10k_pci 
           IF: wlp2s0 state: up mac: <filter> 
Drives:    Local Storage: total: 476.94 GiB used: 73.59 GiB (15.4%) 
           ID-1: /dev/nvme0n1 vendor: SK Hynix model: PC401 NVMe 512GB size: 476.94 GiB 
Partition: ID-1: / size: 462.78 GiB used: 73.53 GiB (15.9%) fs: ext4 dev: /dev/nvme0n1p3 
Sensors:   System Temperatures: cpu: 37.0 C mobo: N/A 
           Fan Speeds (RPM): N/A 
Info:      Processes: 374 Uptime: 5h 27m Memory: 15.35 GiB used: 3.84 GiB (25.0%) Shell: bash inxi: 3.0.33 

```

Monitors Tested on - Dell UltraSharp U2414H through HDMI --> USB-c, Dell UltraSharp 34 Curved USB-C Monitor &#8211; U3419W USB-c --> USB-c
Cable - CHOETECH USB C to HDMI Adapter (laptop USB-c female, cable USB-c male to HDMI female to cable HDMI male to monitor HDMI female)

---

### Post by thunderdfrost on 2020-01-30
I had similar problem, played with UEFI & Legacy boot mode, searched for hours but finally got it done by following ways: 
1. goto Software & Updates 
2. Additional Drivers 
3. Changed the display driver from there. 
4. restart

---

### Post by CelticWarrior on 2020-01-30
> **thunderdfrost said:**
> I had similar problem, played with UEFI & Legacy boot mode, searched for hours but finally got it done by following ways: 
1. goto Software & Updates 
2. Additional Drivers 
3. Changed the display driver from there. 
4. restart

This may have helped you - if you have a Nvidia graphics cards - but it's irrelevant for the OP with an Intel Graphics.

---

