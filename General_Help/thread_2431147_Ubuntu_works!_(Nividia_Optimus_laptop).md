---
title: "Ubuntu works! (Nividia Optimus laptop)"
date: 2019-11-12
forum: General Help
---

### Post by bhooshan-aj on 2019-11-12
I am Debian user (Ubuntu before that... since Ubuntu 6 and days of shipitubuntu) 
I got this laptop I hadn't been able to use Debian **because my external monitor on HDMI would just not work/detect.**

But today I thought I'd give Ubuntu a try and it works. Right out of the box.

I have a ASUS TUF FX504GM laptop with an Intel i7 8750H & nvidia 1060. Here's my system's complete info

```
System:    Host: HomeLT Kernel: 4.19.0-6-amd64 x86_64 bits: 64 compiler: gcc v: 8.3.0 
           parameters: BOOT_IMAGE=/boot/vmlinuz-4.19.0-6-amd64 
           root=UUID=c3cf7cf3-60b4-4639-af2a-63e8a397f5d8 ro quiet splash 
           Desktop: Xfce 4.14.1 tk: Gtk 3.24.5 info: xfce4-panel wm: xfwm4 dm: LightDM 1.26.0 
           Distro: MX-19_x64 patito feo October 21  2019 base: Debian GNU/Linux 10 (buster) 
Machine:   Type: Laptop System: ASUSTeK product: TUF GAMING FX504GM_FX80GM v: 1.0 
           serial: <filter> 
           Mobo: ASUSTeK model: FX504GM v: 1.0 serial: <filter> UEFI: American Megatrends 
           v: FX504GM.308 date: 06/10/2019 
Battery:   ID-1: BAT1 charge: 44.0 Wh condition: 44.0/48.1 Wh (91%) volts: 4.0/11.7 
           model: ASUS A32-K55 type: Li-ion serial: <filter> status: Full 
CPU:       Topology: 6-Core model: Intel Core i7-8750H bits: 64 type: MT MCP arch: Kaby Lake 
           family: 6 model-id: 9E (158) stepping: A (10) microcode: B4 L2 cache: 9216 KiB 
           flags: avx avx2 lm nx pae sse sse2 sse3 sse4_1 sse4_2 ssse3 vmx bogomips: 52992 
           Speed: 900 MHz min/max: 800/4100 MHz Core speeds (MHz): 1: 901 2: 900 3: 900 4: 900 
           5: 901 6: 900 7: 900 8: 900 9: 900 10: 900 11: 900 12: 900 
           Vulnerabilities: Type: l1tf 
           mitigation: PTE Inversion; VMX: conditional cache flushes, SMT vulnerable 
           Type: mds mitigation: Clear CPU buffers; SMT vulnerable 
           Type: meltdown mitigation: PTI 
           Type: spec_store_bypass 
           mitigation: Speculative Store Bypass disabled via prctl and seccomp 
           Type: spectre_v1 mitigation: usercopy/swapgs barriers and __user pointer sanitization 
           Type: spectre_v2 mitigation: Full generic retpoline, IBPB: conditional, IBRS_FW, 
           STIBP: conditional, RSB filling 
Graphics:  Device-1: Intel UHD Graphics 630 vendor: ASUSTeK driver: i915 v: kernel 
           bus ID: 00:02.0 chip ID: 8086:3e9b 
           Device-2: NVIDIA GP106M [GeForce GTX 1060] vendor: ASUSTeK driver: N/A 
           bus ID: 01:00.0 chip ID: 10de:1c20 
           Display: x11 server: X.Org 1.20.4 driver: modesetting unloaded: fbdev,vesa 
           resolution: 1920x1080~120Hz 
           OpenGL: renderer: Mesa DRI Intel UHD Graphics 630 (Coffeelake 3x8 GT2) 
           v: 4.5 Mesa 18.3.6 compat-v: 3.0 direct render: Yes 
Audio:     Device-1: Intel Cannon Lake PCH cAVS vendor: ASUSTeK driver: snd_hda_intel v: kernel 
           bus ID: 00:1f.3 chip ID: 8086:a348 
           Sound Server: ALSA v: k4.19.0-6-amd64 
Network:   Device-1: Intel Wireless-AC 9560 [Jefferson Peak] driver: iwlwifi v: kernel 
           port: 6000 bus ID: 00:14.3 chip ID: 8086:a370 
           IF: wlan0 state: down mac: <filter> 
           Device-2: Realtek RTL8111/8168/8411 PCI Express Gigabit Ethernet vendor: ASUSTeK 
           driver: r8169 v: kernel port: 3000 bus ID: 03:00.0 chip ID: 10ec:8168 
           IF: eth0 state: up speed: 100 Mbps duplex: full mac: <filter> 
Drives:    Local Storage: total: 1.15 TiB used: 5.21 GiB (0.4%) 
           ID-1: /dev/nvme0n1 vendor: Kingston model: RBUSNS8154P3256GJ size: 238.47 GiB 
           block size: physical: 512 B logical: 512 B speed: 15.8 Gb/s lanes: 2 serial: <filter> 
           rev: E8FK11.C scheme: GPT 
           ID-2: /dev/sda vendor: Seagate model: ST1000LX015-1U7172 size: 931.51 GiB block size: 
           physical: 4096 B logical: 512 B speed: 6.0 Gb/s rotation: 5400 rpm serial: <filter> 
           rev: SDM1 scheme: GPT 
           ID-3: /dev/sdb type: USB vendor: SanDisk model: Cruzer Blade size: 7.45 GiB 
           block size: physical: 512 B logical: 512 B serial: <filter> rev: 1.26 scheme: GPT 
Partition: ID-1: / raw size: 31.50 GiB size: 30.88 GiB (98.03%) used: 5.18 GiB (16.8%) fs: ext4 
           dev: /dev/sda2 
Sensors:   System Temperatures: cpu: 49.0 C mobo: 27.8 C 
           Fan Speeds (RPM): cpu: 0 
Repos:     No active apt repos in: /etc/apt/sources.list 
           Active apt repos in: /etc/apt/sources.list.d/antix.list 
           1: deb http://iso.mxrepo.com/antix/buster buster main
           Active apt repos in: /etc/apt/sources.list.d/debian-stable-updates.list 
           1: deb http://deb.debian.org/debian buster-updates main contrib non-free
           Active apt repos in: /etc/apt/sources.list.d/debian.list 
           1: deb http://deb.debian.org/debian buster main contrib non-free
           2: deb http://deb.debian.org/debian-security buster/updates main contrib non-free
           Active apt repos in: /etc/apt/sources.list.d/mx.list 
           1: deb http://mxrepo.com/mx/repo/ buster main non-free
           No active apt repos in: /etc/apt/sources.list.d/various.list 
Info:      Processes: 303 Uptime: 3m Memory: 15.52 GiB used: 1.02 GiB (6.6%) Init: SysVinit 
           v: 2.93 runlevel: 5 default: 5 Compilers: gcc: 8.3.0 alt: 8 Shell: bash v: 5.0.3 
           running in: quick-system-in inxi: 3.0.36 
```

I tried **bumblebee, prime** etc and could not make it work.

Can someone enlighten me why Ubuntu is able to work right out of box when Debian, MX Linux and Manjaro/Arch failed to?
[B] LIke what configuration, drivers, work arounds are impletemented?

I am actually very curious to learn. Understand where I failed.
[/B]

---

### Post by bhooshan-aj on 2019-11-24
bump. No one?

---

