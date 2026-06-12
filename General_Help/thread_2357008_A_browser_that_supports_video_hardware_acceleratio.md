---
title: "A browser that supports video hardware acceleration for youtube"
date: 2017-03-29
forum: General Help
---

### Post by ultragamer2 on 2017-03-29
I am trying to find a browser for ubuntu that supports hardware video decoding on youtube.com

Here are my system specs. As you can see it's a low power cpu and it really needs video decoding.


```
System:    Host: moviepc-GB-3000 Kernel: 4.4.0-66-generic x86_64 (64 bit)
           Desktop: MATE 1.12.1  Distro: Ubuntu 16.04 xenial
Machine:   Mobo: GIGABYTE model: MZBSWAP-00 v: 1.x
           Bios: American Megatrends v: F5 date: 03/23/2016
CPU:       Dual core Intel Celeron N3000 (-MCP-) cache: 1024 KB 
           clock speeds: max: 2080 MHz 1: 1478 MHz 2: 1140 MHz
Graphics:  Card: Intel Device 22b1
           Display Server: X.Org 1.18.4 drivers: intel (unloaded: fbdev,vesa)
           Resolution: 1920x1080@60.00hz
           GLX Renderer: Mesa DRI Intel HD Graphics (Cherryview)
           GLX Version: 3.0 Mesa 11.2.2
Audio:     Card Intel Device 2284 driver: snd_hda_intel
           Sound: Advanced Linux Sound Architecture v: k4.4.0-66-generic
Network:   Card: Realtek RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
           driver: r8169
           IF: enp3s0 state: up speed: 100 Mbps duplex: full mac: <filter>
Drives:    HDD Total Size: 94.1GB (41.1% used)
           ID-1: /dev/sda model: KingFast size: 32.0GB
           ID-2: USB /dev/sdb model: Ultra size: 62.1GB
Partition: ID-1: / size: 14G used: 11G (89%) fs: ext4 dev: /dev/sda2
           ID-2: swap-1 size: 7.97GB used: 0.00GB (0%) fs: swap dev: /dev/sda3
RAID:      No RAID devices: /proc/mdstat, md_mod kernel module present
Sensors:   None detected - is lm-sensors installed and configured?
Info:      Processes: 179 Uptime: 6 days Memory: 869.2/7406.1MB
           Client: Shell (bash) inxi: 2.2.35
```

---

### Post by SeijiSensei on 2017-03-29
If you're using Flash, open a video full screen, then right-click on it and choose Settings.  You'll see a box for hardware acceleration.  I don't how to do this with HTML5 videos.  I don't see any such settings available in the YouTube player.

This isn't a browser function but depends on the player the browser invokes to display video.

If you install smplayer, the companion smtube player uses mplayer or mpv to display YouTube videos.  You can control whether hardware acceleration is used by those players in Options > Preferences.

---

### Post by ultragamer2 on 2017-03-30
Thanks it looks good and I can filter by duration length.

Does anyone know what 'output driver' in video preferences I should choose for hardware acceleration to work?

Graphics:  Card: Intel Device 22b1
           Display Server: X.Org 1.18.4 drivers: intel (unloaded: fbdev,vesa)
           Resolution: 1920x1080@60.00hz
           GLX Renderer: Mesa DRI Intel HD Graphics (Cherryview)
           GLX Version: 3.0 Mesa 11.2.2

I tried choosing vdpau and there was no video, default seems to use a lot of cpu.

---

### Post by deadflowr on 2017-03-30
intel should use vaapi, and the driver package should already be installed
it's in the package *libva-intel-vaapi-driver* (for 12.04 and 14.04 at least)
Edit: also found in *i965-va-driver* (in 16.04 and newer, I think)

---

### Post by ultragamer2 on 2017-03-30
OK thanks, it can't load 1080p but goes up to 720p, watching a test video it shows between 22% - 49% cpu utilisation on both cores, is that about right? I thought it would be lower.

Also every time smtube starts it seems to reset to 320p and shows the dialog about it being a new version.

---

### Post by ultragamer2 on 2017-03-31
Does the system monitor cpu utilisation metre measure the integrated gpu part of the cpu or just the cpu part?

---

