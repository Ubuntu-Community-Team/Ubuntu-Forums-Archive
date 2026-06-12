---
title: "Ubuntu 19.04 Incredibly awful screen tearing on Dell Precision 5530"
date: 2019-10-06
forum: General Help
---

### Post by pokemaniac00 on 2019-10-06
I currently run Ubuntu 19.04 on my Dell Precision 5530 Laptop. I had switched away from Linux Mint to Ubuntu in hopes that screen tearing would stop in linux, but it has begun to resurface again over time.
The screen will glitch, freeze, and tear, not limited to any specific applications at all.
I would attempt to create an /etc/X11/xorg.conf.d/20-intel.conf file, but when I reboot I would be stuck in a login loop.
What do I do? I'm pulling my hair out here trying to search for ways to resolve this issue and it is getting worse by the day!
output of inxi -Fxz

```

System:
  Host: Flor-Ubuntu Kernel: 5.0.0-31-generic x86_64 bits: 64 compiler: gcc 
  v: 8.3.0 Desktop: Gnome 3.32.2 Distro: Ubuntu 19.04 (Disco Dingo) 
Machine:
  Type: Laptop System: Dell product: Precision 5530 v: N/A serial: <filter> 
  Mobo: Dell model: 0F8T29 v: X04 serial: <filter> UEFI: Dell v: 1.11.2 
  date: 05/29/2019 
Battery:
  ID-1: BAT0 charge: 59.6 Wh condition: 91.7/97.0 Wh (94%) 
  model: SMP DELL GPM0365 status: Discharging 
CPU:
  Topology: 6-Core model: Intel Core i7-8850H bits: 64 type: MT MCP 
  arch: Kaby Lake rev: A L2 cache: 9216 KiB 
  flags: lm nx pae sse sse2 sse3 sse4_1 sse4_2 ssse3 vmx bogomips: 62208 
  Speed: 800 MHz min/max: 800/4300 MHz Core speeds (MHz): 1: 800 2: 800 
  3: 800 4: 800 5: 800 6: 800 7: 801 8: 801 9: 800 10: 800 11: 800 12: 800 
Graphics:
  Device-1: Intel UHD Graphics 630 vendor: Dell driver: i915 v: kernel 
  bus ID: 00:02.0 
  Device-2: NVIDIA GP107GLM [Quadro P1000 Mobile] vendor: Dell 
  driver: nvidia v: 418.56 bus ID: 01:00.0 
  Display: x11 server: X.Org 1.20.4 driver: modesetting,nvidia 
  unloaded: fbdev,nouveau,vesa tty: N/A 
  OpenGL: renderer: Quadro P1000/PCIe/SSE2 v: 4.6.0 NVIDIA 418.56 
  direct render: Yes 
Audio:
  Device-1: Intel Cannon Lake PCH cAVS vendor: Dell driver: snd_hda_intel 
  v: kernel bus ID: 00:1f.3 
  Sound Server: ALSA v: k5.0.0-31-generic 
Network:
  Device-1: Intel Wireless-AC 9260 driver: iwlwifi v: kernel port: 3000 
  bus ID: 3b:00.0 
  IF: wlp59s0 state: up mac: <filter> 
Drives:
  Local Storage: total: 476.94 GiB used: 57.72 GiB (12.1%) 
  ID-1: /dev/nvme0n1 vendor: Samsung model: PM981 NVMe 512GB 
  size: 476.94 GiB 
Partition:
  ID-1: / size: 467.96 GiB used: 57.69 GiB (12.3%) fs: ext4 
  dev: /dev/nvme0n1p2 
Sensors:
  System Temperatures: cpu: 41.0 C mobo: N/A gpu: nvidia temp: 53 C 
  Fan Speeds (RPM): cpu: 0 fan-2: 0 
Info:
  Processes: 349 Uptime: 4m Memory: 15.33 GiB used: 2.27 GiB (14.8%) 
  Init: systemd runlevel: 5 Compilers: gcc: 8.3.0 Shell: bash v: 5.0.3    inxi: 3.0.33

```

output of lspci | grep VGA
```
00:02.0 VGA compatible controller: Intel Corporation UHD Graphics 630 (Mobile)
```

---

### Post by Skaperen on 2019-10-06
there might be component limitations at UHD speeds.  i'd have to see it in action to get a idea if it is a software issue or a hardware issue.  i have seen that when HD came out.  and now UHD (4K, 3840x2160) is the big thing.

---

### Post by CatKiller on 2019-10-07
> **pokemaniac00 said:**
> I would attempt to create an /etc/X11/xorg.conf.d/20-intel.conf file, but when I reboot I would be stuck in a login loop.

What were you trying to put in that file? Your symptoms after doing so suggest that you made a mistake somewhere with the syntax.

---

### Post by mc4man on 2019-10-07
> **pokemaniac00 said:**
> I currently run Ubuntu 19.04 on my Dell Precision 5530 Laptop. I had switched away from Linux Mint to Ubuntu in hopes that screen tearing would stop in linux, but it has begun to resurface again over time.
The screen will glitch, freeze, and tear, not limited to any specific applications at all.
I would attempt to create an /etc/X11/xorg.conf.d/20-intel.conf file, but when I reboot I would be stuck in a login loop.
What do I do? I'm pulling my hair out here trying to search for ways to resolve this issue and it is getting worse by the day!

output of lspci | grep VGA
```
00:02.0 VGA compatible controller: Intel Corporation UHD Graphics 630 (Mobile)
```
Sounds like you have issues not just releated to a lack of vsync(tearing), maybe because of a Quadro gpu ,maybe Dell, maybe both.
You either have vsync or you don't, "glitch, freeze" have nothing to do with that.. also a lack of vsync doesn't  'get worse by the day' , though possibly your exposing increases.

If your hybrid hardware is using nvidia-prime (GeForce do, I've no idea about Quadro), then using a 20-intel.conf file to get TearFree (or any other option) is a waste of time & likely will cause issues. The TearFree option only works with SNA, currently & for quite some time, (14.04.3),  nvidia-prime ( iirc via ubuntu-drivers-common) uses modesetting.
If nvidia-settings has Prime Profiles then you should be able to remove tearing by enabling prime synchronization, do you have that tab ?

What is different about your hardware than from typical (GeForce), is that   lspci | grep VGA should list both devices, yours doesn't.

---

### Post by cruzer001 on 2019-10-07
The Quadro 630 card has been asked about a few times in this forum.  I have answered a few with little success.

19.10 is ready for release in a few weeks, you could upgrade now.  You will need to upgrade soon anyhow.

---

