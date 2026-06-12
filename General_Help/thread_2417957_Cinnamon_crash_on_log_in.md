---
title: "Cinnamon crash on log in"
date: 2019-04-29
forum: General Help
---

### Post by cyfral6 on 2019-04-29
Hi, I'm pretty new to linux, tried installing amd gpu 18.40 drivers and something might have gone wrong as cinnamon refuses to work.

inxi -Fxzd shows the driver is not loaded? 

```
System:
  Host: kazuko-Lenovo-ideapad-530S-14ARR Kernel: 4.15.0-48-generic x86_64 
  bits: 64 compiler: gcc v: 7.3.0 Desktop: Cinnamon 4.0.10 
  Distro: Linux Mint 19.1 Tessa base: Ubuntu 18.04 bionic 
Machine:
  Type: Laptop System: LENOVO product: 81H1 v: Lenovo ideapad 530S-14ARR 
  serial: <filter> 
  Mobo: LENOVO model: LNVNB161216 v: SDK0J40709 WIN serial: <filter> 
  UEFI: LENOVO v: 8PCN50WW date: 12/25/2018 
Battery:
  ID-1: BAT0 charge: 43.7 Wh condition: 43.7/45.5 Wh (96%) 
  model: CPT-COS L17C4PB0 status: Full 
  Device-1: hidpp_battery_0 model: Logitech Performance MX charge: 5% 
  status: Discharging 
CPU:
  Topology: Quad Core model: AMD Ryzen 7 2700U with Radeon Vega Mobile Gfx 
  bits: 64 type: MT MCP arch: Zen L2 cache: 2048 KiB 
  flags: lm nx pae sse sse2 sse3 sse4_1 sse4_2 sse4a ssse3 svm 
  bogomips: 35134 
  Speed: 1366 MHz min/max: 1600/2200 MHz Core speeds (MHz): 1: 1371 2: 1431 
  3: 1448 4: 1435 5: 1503 6: 1534 7: 1371 8: 1373 
Graphics:
  Device-1: AMD Raven Ridge [Radeon Vega Series / Radeon Vega Mobile Series] 
  vendor: Lenovo driver: N/A bus ID: 03:00.0 
  Display: x11 server: X.Org 1.19.6 driver: fbdev unloaded: modesetting,vesa 
  resolution: 1920x1080~77Hz 
  OpenGL: renderer: N/A v: N/A direct render: N/A 
Audio:
  Device-1: AMD vendor: Lenovo driver: snd_hda_intel v: kernel 
  bus ID: 03:00.1 
  Device-2: AMD vendor: Lenovo driver: N/A bus ID: 03:00.5 
  Device-3: AMD vendor: Lenovo driver: snd_hda_intel v: kernel 
  bus ID: 03:00.6 
  Sound Server: ALSA v: k4.15.0-48-generic 
Network:
  Device-1: Qualcomm Atheros QCA9377 802.11ac Wireless Network Adapter 
  vendor: Lenovo driver: ath10k_pci v: kernel bus ID: 01:00.0 
  IF: wlp1s0 state: down mac: <filter> 
  Device-2: Atheros type: USB driver: btusb bus ID: 1-4:4 
Drives:
  Local Storage: total: 238.47 GiB used: 15.53 GiB (6.5%) 
  ID-1: /dev/nvme0n1 vendor: Western Digital 
  model: PC SN520 SDAPMUW-256G-1101 size: 238.47 GiB 
  Message: No Optical or Floppy data was found. 
Partition:
  ID-1: / size: 232.28 GiB used: 15.52 GiB (6.7%) fs: ext4 dev: /dev/dm-0 
  ID-2: swap-1 size: 976.0 MiB used: 0 KiB (0.0%) fs: swap dev: /dev/dm-1 
Sensors:
  System Temperatures: cpu: 51.1 C mobo: N/A 
  Fan Speeds (RPM): N/A 
Info:
  Processes: 224 Uptime: 2m Memory: 7.41 GiB used: 666.5 MiB (8.8%) 
  Init: systemd runlevel: 5 Compilers: gcc: 7.4.0 Shell: bash v: 4.4.19 
  inxi: 3.0.33 



```

and glxinfo returns this:
```
name of display: :0
Error: couldn't find RGB GLX visual or fbconfig

```

I've been trying to find a working solution for this for the last few days with no luck so I'm here, forced to ask the more competent people for help.

---

