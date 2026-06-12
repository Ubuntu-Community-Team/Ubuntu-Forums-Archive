---
title: "Can't open gui ubuntu"
date: 2022-08-04
forum: General Help
---

### Post by lorlik on 2022-08-04
Hi, I have ubuntu on my laptop. And one day I turned my laptop on and I saw only command line and I satrted to look for answare in internet, but none of them doesn't works.
**What I can say:**
 I tryed ctrl + alt + F2, then ctrl + alt + F1.
 I tryed ctrl + alt + F7
**What I did before this:**
 **Last what I did is:**
  I closed my laptop and after I open it I saw laggy logining in. There was just something like can't log in or idk, but I cant write my pasword there bcs it updates and then I pressed suspend button bcs I thought it was turn off, but nothing chenged, and then I turned off my laptop using nutton and I saw this problem...
**Wierd:**
 when I run startx it turns on ubuntu terminal on forward of the black screen and from there I can even run my c++ gui snake game...

---

### Post by TheFu on 2022-08-04
You are seeing a terminal, are you seeing any window decorations/boarders?

Also, it would be good to know a bit about the system hardware and software versions.  I doubt startx will impress a system running Wayland either.

**inxi -Fxxz** output would be helpful as an overview. The 'z' option removes all sensitive, personal, information.  Please post that wrapped in 'code tags', for more help.

Nobody here knows anything about "my c++ snake game".

---

### Post by ActionParsnip on 2022-08-04
If you boot an older kernel is it OK?

---

### Post by lorlik on 2022-08-05
No, i don't see any borders.
Here is **inxi -Fxxz** output:
```

System: 
    Kernel: 5.15.0-43-generic x86_64 bits: 64 compiler: gcc w: 11.2.0 Console: tty 1
         Distro: Ubuntu 22.04.1 LTS (Jammy Jellyfish) Machine: 
    Type: Laptop System: Dell product: Latitude 5580 v: N/A serial: <superuser required> Chassis:
        type: 10 serial: <superuser required> 
    Mobo: Dell model: 0FH6CJ v: A00 serial: <superuser required> UEFI- [Legacy]: Dell v: 1.9.3
         date: 03/08/2018 
Battery:
     ID-1: BATO charge: 28.0 Wh (56.2%) condition: 49.8/68.0 Wh (73.2%) volts: 7.6 min: 7.6
        model: SMP DELL GD1JP65 serial: <filter> status: Discharging 
CPU: 
    Info: quad core model: Intel Core i7-7820HQ bits: 64 type: MT MCP arch: Kaby Lake rev: 9 cache:
        L1: 256 KiB L2: 1024 KiB L3: 8 MiB 
    Speed (MHz): avg: 1323 high: 2928 min/max: 800/3900 cores: 1: 1341 2: 2928 3: 1750 4: 1053
        5: 900 6: 900 7: 877 8: 840 bogomios: 46398 
Flags: avx avx2 ht lm nx pae sse sse2 sse3 sse4_1 sse4_2 ssse3 vmx 
Graphics: 
    Device-1: Intel HD Graphics 630 vendar: Dell driver. i915 : kernel ports: active: eDP-1
        empty: DP-1, DP-2, HDMI-A-1, HDMI-A-2, HDMI-A-3 bus-ID: 00:02.0 chip-ID: 8086:591b 
    Device-2: NVIDIA GM107 [GeForce 940MX] Vendor: Dell driver: N/A pcie: Speed: 8 GT/S lanes: 16
         bus-ID: 01:00.0 chip-ID: 10de: 1790 
    Device-3: Realtek Integrated Hebcam HD type: USB driver: uvcvideo bus-ID: 1-11:3
        chip-ID: Obda:568C 
    Display: server: X.org v: 1.21.1.3 driver: X: loaded: modesetting unloaded: fbdev, vesa
        gpu: 1915 tty: 240X67 
    Monitor-1: eDP-1 model: BOE Display res: 1920x1080 dpi: 142 diag: 395mm (15.5")
    Message:. GL data unavailable in console. Try -G --display 
Audio: 
    Device-1: Intel CM238 HD Audio vendor: Dell driver: snd_hda_intel v: kernel 
         bus-ID: 00:1f.3 chip-ID: 8086:a171 
    Device-2: NVIDIA GM107 High Definition Audio (GeForce 940MX] driver: snd_hda intelu: kernel
        pcie: speed: 8 GT/S lanes: 16 bus-ID: 01:00.1 chip-ID: 10de:Ofbc 
     Sound Server-1: ALSA V: k5.15.0-43-generic running: yes 
     Sound Server-2: PulseAudio v: 15.99.1.running: yes
     Sound Server-3: PipeWire v: 0.3.48 running: yes Network: 
    Device-1: Intel Ethernet 1219-LM vendor: Dell driver: e1000e v: kernel port: N/A
         bus-ID: 00:1f.6 chip-ID: 8086:15e3 
    IF: enpos31f6 state: down mac: <filter> 
    Device-2: Intel Wireless 8265 / 8275 driver: iwlwifi v: kernel pcie: speed: 2.5 GT/s lanes: 1
         bus-ID: 02:00.0 chip-ID: 8086:24fd 
    IF: w1p2s0 state: up mac: (filter) 
Bluetooth: 
    Device-1: Intel Bluetooth wireless interface type: USB driver: btusb v: 0.8 bus-ID: 1-6:2
         chip-ID: 8087:0azb 
    Report: hciconfig ID: hcio rfk-id: 0 state: up address: <filter> bt-v: 2.1 imp-v: 4.2
         sub-v: 100 
Drives: 
     Local Storage: total: 476.94 GiB used: 52.49 GiB (11.0%)
    ID-1: /dev/sda vendor: SK Hynix model: SC311 SATA 512GB size: 476.94 GiB speed: 6.0 Gb/s
        serial: (filter)
Partition:
    ID-1 / size: 467.89 GiB used: 52.48 GiB (11.28) fs: ext4 dev: /dev/sda3
    ID-2: /boot/efi size: 512 NiB used: 5.2 MiB (1.08) fs: vfat dev: /dev/sda2
Swap:
    ID-1: swap-1 type: file size: 2 GiB used: 0 KiB (0.08) priority: -2 file: /swapfile 
Sensors:
    System Temperatures: cpu: 51.0 C pch: 45.0 C mobo: 41.0 C sodimm: SODIMM C
    Fan Speeds (RPM): cpu: 2308
Info:
    Processes: 192 Uptime: 28m Memory: 15.28 GiB used: 659.8 MiB (4.2%) Init: systemd v: 249
    runlevel: 5 Compilers: gcc: 11.2.0 alt: 11 Packages: 2062 apt: 2042 snap: 20 Shell: Bash
    v: 5.1.16 running-in: tty 1 inxi: 3.3.13 

```

---

### Post by TheFu on 2022-08-05
Looks like you have 2 GPUs.  an Nvidia and the iGPU from Intel.  You'll need to tell the OS which you want to use, somehow.  I don't know how to accomplish that.
Also, looks like you are running 22.04.
I don't see any DE or window manager referenced, which explains why you don't see any borders.

Install a window manager - say fvwm or openbox, then run those from the command line after xinit.  I have a script that does this in my ~/.xinitrc file.  I think 22.04 systemd-logind broke some things, but I don't have it and don't actually know.

If you see a terminal and can type inside it, run openbox & - that should start a minimal windowing environment.

---

### Post by lorlik on 2022-08-05
I installed openbox, run **openbox** and it gives this:
```

[1] 2910
Openbox-Message: Failed to open the display from the DISPLAY environment variable.

```
and then I run startx and it seems to work.
I have black screen and when I press left button i see "menu" where I can chose program.
But...
I don't understand. I need to live like this whole my linux life? Or here is some way to fix it.
If it is to say which core use, so how..?

---

### Post by #&amp;thj^% on 2022-08-05
Simple and easy way:
```
sudo apt-get install xinit
```
or you'll need to add it to **"~/.xinitrc"**, and execute **"startx"** instead.
Heads up "Remember that an X app can't be run outside the Xorg environment."
Pardon the drive by...

---

### Post by TheFu on 2022-08-05
> **lorlik said:**
> I installed openbox, run **openbox** and it gives this:
```

[1] 2910
Openbox-Message: Failed to open the display from the DISPLAY environment variable.

```
and then I run startx and it seems to work.
I have black screen and when I press left button i see "menu" where I can chose program.
But...
I don't understand. I need to live like this whole my linux life? Or here is some way to fix it.
If it is to say which core use, so how..?

Which DE were you using before the issue?  openbox isn't a DE. It is a minimal WM, window manager. It is how we handled X/11 in the 1990s and how some people, like me, still use it.
Sorry, but when I saw you were using startx and coding in C++, I made all sorts of assumptions which may have not been correct.

If you want a full DE (gnome/xfce/kde/lxqt/mate/cinnamon or one of the others), ignore everything I've posted. I realize this is too late now.  Before the X environment starts, you should look in the X.log.0 log file for errors.  Almost always, the issue will be clearly spelled out. You just need to read, comprehend and recognize the issue.

BTW, X11 uses the DISPLAY environment variable for everything. It says which GPU to use, which monitor to write output towards, which keyboard and mouse to use.  If it isn't set, X doesn't work.  99% of the time, typical users can set it to:
export DISPLAY=:0
and that will be a work-around while troubleshooting.

Once you see the X.log.0 errors, solve those.  Sometimes it is a missing or corrupted file.  Sometimes it clearly says to run some program with specific options.  I'm greatly trusting that what you've described above concerning a terminal and startup is what I think it is. It may not be at all, since we are coming for entirely different backgrounds.  A black background isn't the normal output for an X11 environment that is running.  Normally, it is a dithered gray background with a large 'X' that shows were the mouse is on the screen.  I'm not really certain the system is running X at this point.

Oh .... all log files are in /var/log/.  Look there for errors and warnings.

---

### Post by lorlik on 2022-08-07
I still don't understand what I can do here :(. In X.0.log some missing files. Some fonts. But I have no ideas what i need to do here... 
Information what I forgot to say:
In unattended-upgrades.log 
```
linux-modules-nvidia-510-generic-hwe-generic-hwe-22.04 is kept back bcs a related package is kept back or due to local apt_preference(5)
nvidia-kernel-common-510 is kept back bcs a related package is kept back or due to local apt_preference(5)

```
Can It be a problem?

---

