---
title: "Blank Screen after Awake from Sleep"
date: 2020-07-02
forum: General Help
---

### Post by hayloiuy on 2020-07-02
After my PC wake up from sleep, there is only blank screen.

Now I gotta shutdown my computer after every usage. Whats is the problem?
I am using Ubuntu 19.10.

---

### Post by ajgreeny on 2020-07-02
We need a lot more information to be able to help you in any way.

Open a terminal and run command ```
inxi -Fzx
``` then copy the output back here.

Please use **Code-Tags** for terminal output as it makes that output much more easily read and understood, formatting the text as seen in terminal, not as plain text when it is copied and pasted. See my signature below for a **How-to**

---

### Post by ActionParsnip on 2020-07-02
Ubuntu 19.10 is EOL at some point this month so only has a matter of WEEKS left in support.
[https://wiki.ubuntu.com/Releases](https://wiki.ubuntu.com/Releases)

I suggest you upgrade to 20.04 which is LTS. The newer packages may help the situation.

---

### Post by GhX6GZMB on 2020-07-02
> **hayloiuy said:**
> After my PC wake up from sleep, there is only blank screen.

Now I gotta shutdown my computer after every usage. Whats is the problem?
I am using Ubuntu 19.10.

What exactly do you mean with "sleep"? 

Suspend (=suspend to RAM) or Hibernate (=suspend to disk and power off)?

---

### Post by hayloiuy on 2020-07-06
Here ya go.
```
System:
  Host: wesker-desktop Kernel: 5.3.0-62-generic x86_64 bits: 64 
  compiler: gcc v: 9.2.1 Desktop: Gnome 3.34.3 
  Distro: Ubuntu 19.10 (Eoan Ermine) 
Machine:
  Type: Desktop Mobo: ASRock model: H81M-VG4 R2.0 serial: <filter> 
  UEFI: American Megatrends v: P1.20 date: 07/04/2014 
CPU:
  Topology: Dual Core model: Intel Core i3-4150 bits: 64 type: MT MCP 
  arch: Haswell rev: 3 L2 cache: 3072 KiB 
  flags: avx avx2 lm nx pae sse sse2 sse3 sse4_1 sse4_2 ssse3 vmx 
  bogomips: 27992 
  Speed: 800 MHz min/max: 800/3500 MHz Core speeds (MHz): 1: 800 2: 800 
  3: 800 4: 800 
Graphics:
  Device-1: NVIDIA GF108 [GeForce GT 730] vendor: Micro-Star MSI 
  driver: nvidia v: 390.138 bus ID: 01:00.0 
  Display: x11 server: X.Org 1.20.5 driver: nvidia 
  unloaded: fbdev,modesetting,nouveau,vesa resolution: 1920x1080~60Hz 
  OpenGL: renderer: GeForce GT 730/PCIe/SSE2 v: 4.6.0 NVIDIA 390.138 
  direct render: Yes 
Audio:
  Device-1: Intel 8 Series/C220 Series High Definition Audio vendor: ASRock 
  driver: snd_hda_intel v: kernel bus ID: 00:1b.0 
  Device-2: NVIDIA GF108 High Definition Audio vendor: Micro-Star MSI 
  driver: snd_hda_intel v: kernel bus ID: 01:00.1 
  Sound Server: ALSA v: k5.3.0-62-generic 
Network:
  Device-1: Realtek RTL8111/8168/8411 PCI Express Gigabit Ethernet 
  vendor: ASRock driver: r8169 v: kernel port: d000 bus ID: 03:00.0 
  IF: enp3s0 state: down mac: <filter> 
  Device-2: Ralink MT7601U Wireless Adapter type: USB driver: mt7601u 
  bus ID: 3-1:2 
  IF: wlx14cc20216dd2 state: up mac: <filter> 
Drives:
  Local Storage: total: 465.76 GiB used: 22.12 GiB (4.7%) 
  ID-1: /dev/sda vendor: Seagate model: ST500DM002-1BD142 size: 465.76 GiB 
  temp: 38 C 
Partition:
  ID-1: / size: 192.61 GiB used: 22.12 GiB (11.5%) fs: ext4 dev: /dev/sda7 
  ID-2: swap-1 size: 8.00 GiB used: 0 KiB (0.0%) fs: swap dev: /dev/sda5 
Sensors:
  System Temperatures: cpu: 40.0 C mobo: N/A gpu: nvidia temp: 37 C 
  Fan Speeds (RPM): N/A gpu: nvidia fan: 42% 
Info:
  Processes: 298 Uptime: 50m Memory: 7.71 GiB used: 1.88 GiB (24.3%) 
  Init: systemd runlevel: 5 Compilers: gcc: 9.2.1 Shell: bash v: 5.0.3 
  inxi: 3.0.36 



```

---

### Post by hayloiuy on 2020-07-06
Suspend to RAM

---

