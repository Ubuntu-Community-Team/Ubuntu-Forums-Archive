---
title: "Resolution problems with 2nd monitor"
date: 2008-05-10
forum: General Help
---

### Post by Speedy328 on 2008-05-10
I have a monitor problem with Ubuntu 8.04 after doing a clean install. I have a Dell Latitude C600 laptop which I have in a docking station. I have a CTX 5370 monitor attached to the docking station. I also have another laptop running Windows XP (for work) attached to the monitor via a KVM switch.

The problem is that when I had 7.10 installed I was able to display 1280x1024 on the monitor. With Hardy, no matter what I try to do to configure 1280x1024 I can't get it to work. If I run 'dpkg-reconfigure xserver-xorg' it give me a pretty blank xorg.conf file with no real settings. I've tried to insert the proper horz and vert sync settings and the fact that I am using the 'ati' driver. However, when I do a ctl-alt-bksp to restart X, it will usually bring up a warning box telling me that it couldn't get my video device or monitor setting and I need to reconfigure. If I try to do that and choose the correct settings it ignores them and comes up in 600x800 mode. Checking the Xorg.0.log file show that it is now using a xorg.conf.failsafe file rather than the xorg.conf file with the settings for my monitor.

I've tried several different combinations of things to correct this but all seem to have the same effect.

This is the output from lspci:

```
00:00.0 Host bridge: Intel Corporation 440BX/ZX/DX - 82443BX/ZX/DX Host bridge (rev 03)
00:01.0 PCI bridge: Intel Corporation 440BX/ZX/DX - 82443BX/ZX/DX AGP bridge (rev 03)
00:03.0 CardBus bridge: Texas Instruments PCI1420 PC card Cardbus Controller
00:03.1 CardBus bridge: Texas Instruments PCI1420 PC card Cardbus Controller
00:07.0 Bridge: Intel Corporation 82371AB/EB/MB PIIX4 ISA (rev 02)
00:07.1 IDE interface: Intel Corporation 82371AB/EB/MB PIIX4 IDE (rev 01)
00:07.2 USB Controller: Intel Corporation 82371AB/EB/MB PIIX4 USB (rev 01)
00:07.3 Bridge: Intel Corporation 82371AB/EB/MB PIIX4 ACPI (rev 03)
00:08.0 Multimedia audio controller: ESS Technology ES1983S Maestro-3i PCI Audio Accelerator (rev 10)
00:0d.0 Ethernet controller: 3Com Corporation 3c905 100BaseTX [Boomerang]
00:10.0 Ethernet controller: 3Com Corporation 3c556 Hurricane CardBus [Cyclone] (rev 10)
00:10.1 Communication controller: 3Com Corporation Mini PCI 56k Winmodem (rev 10)
01:00.0 VGA compatible controller: ATI Technologies Inc Rage Mobility M3 AGP 2x (rev 02)
```

and this is the results from ddcprobe:

```
vbe: VESA 2.0 detected.
oem: ATI MOBILE M3
memory: 8192kb
mode: 320x200x32k
mode: 320x200x64k
mode: 320x200x16m
mode: 1600x1200x256
mode: 640x400x256
mode: 640x480x256
mode: 640x480x32k
mode: 640x480x64k
mode: 640x480x16m
mode: 1600x1200x32k
mode: 800x600x256
mode: 800x600x32k
mode: 800x600x64k
mode: 800x600x16m
mode: 1600x1200x64k
mode: 1024x768x256
mode: 1024x768x32k
mode: 1024x768x64k
mode: 1024x768x16m
mode: 1280x1024x256
mode: 1280x1024x32k
mode: 1280x1024x64k
mode: 1280x1024x16m
edid: 
edid: 1 1
id: 5370
eisa: CTX5370
serial: 00000000
manufacture: 0 2001
input: composite sync, sync on green, digital signal.
screensize: 33 25
gamma: 2.100000
dpms: RGB, active off, suspend, standby
timing: 720x400@70 Hz (VGA 640x400, IBM)
timing: 640x480@60 Hz (VGA)
timing: 640x480@67 Hz (Mac II, Apple)
timing: 640x480@72 Hz (VESA)
timing: 640x480@75 Hz (VESA)
timing: 800x600@60 Hz (VESA)
timing: 800x600@75 Hz (VESA)
timing: 832x624@75 Hz (Mac II)
timing: 1024x768@87 Hz Interlaced (8514A)
timing: 1024x768@60 Hz (VESA)
timing: 1024x768@70 Hz (VESA)
timing: 1024x768@75 Hz (VESA)
timing: 1280x1024@75 (VESA)
ctiming: 640x480@120
ctiming: 800x600@100
ctiming: 1024x768@85
ctiming: 1280x1024@60
ctiming: 1280x960@60
dtiming: 640x480@85
dtiming: 800x600@85
dtiming: 1024x768@104
monitorrange: 30-72, 50-130
```

If you look closely you'll see that it appears to see the monitor correctly so I don't think that it is caused by that.

Any ideas?

Thanks

---

