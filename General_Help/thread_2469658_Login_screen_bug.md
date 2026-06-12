---
title: "Login screen bug"
date: 2021-12-05
forum: General Help
---

### Post by nicolam94 on 2021-12-05
Hello everyone

I'm having some issues logging in into my machine and restoring the session after the suspension mode. The screen starts to glitch to a gray static noise just after the password insertion. 
Here's a video I made of the problem: [https://drive.google.com/file/d/1wWAAt0hVSoT_SaufAfSLbUDMkZwSK8RH/view?usp=sharing](https://drive.google.com/file/d/1wWAAt0hVSoT_SaufAfSLbUDMkZwSK8RH/view?usp=sharing)

Here are my specs:

```
Host: nicola-laptop Kernel: 5.13.0-22-generic x86_64 bits: 64 
  compiler: gcc v: 11.2.0 
  parameters: BOOT_IMAGE=/boot/vmlinuz-5.13.0-22-generic 
  root=UUID=8a244fb7-d8a1-4fca-990d-b9dd579d94a2 ro quiet splash 
  vt.handoff=7 
  Desktop: GNOME 40.5 tk: GTK 3.24.30 wm: gnome-shell dm: GDM3 41.rc 
  Distro: Ubuntu 21.10 (Impish Indri) 
Machine:
  Type: Laptop System: HP product: HP 255 G6 Notebook PC 
  v: Type1ProductConfigId serial: <superuser required> Chassis: type: 10 
  serial: <superuser required> 
  Mobo: HP model: 8330 v: 27.33 serial: <superuser required> UEFI: Insyde 
  v: F.31 date: 07/25/2018 
Battery:
  ID-1: BAT1 charge: 17.4 Wh (59.2%) condition: 29.4/31.1 Wh (94.5%) 
  volts: 10.8 min: 10.9 model: Hewlett-Packard PABAS0241231 type: Li-ion 
  serial: 41167 status: Discharging 
Memory:
  RAM: total: 7.24 GiB used: 1.85 GiB (25.5%) 
  RAM Report: 
  permissions: Unable to run dmidecode. Root privileges required. 
PCI Slots:
  Permissions: Unable to run dmidecode. Root privileges required. 
CPU:
  Info: Dual Core model: AMD A9-9425 RADEON R5 5 COMPUTE CORES 2C+3G 
  bits: 64 type: MCP arch: Excavator family: 15 (21) model-id: 70 (112) 
  stepping: 0 microcode: 6006705 cache: L2: 1024 KiB bogomips: 12376 
  Speed: 1397 MHz min/max: 1400/3100 MHz boost: enabled Core speeds (MHz): 
  1: 1397 2: 1490 
  Flags: 3dnowprefetch abm acc_power aes aperfmperf apic arat avic avx avx2 
  bmi1 bmi2 bpext clflush cmov cmp_legacy constant_tsc cpb cpuid cr8_legacy 
  cx16 cx8 de decodeassists extapic extd_apicid f16c flushbyasid fma fma4 
  fpu fsgsbase fxsr fxsr_opt ht hw_pstate ibpb ibs lahf_lm lbrv lm lwp mca 
  mce misalignsse mmx mmxext monitor movbe msr mtrr mwaitx nodeid_msr 
  nonstop_tsc nopl npt nrip_save nx osvw overflow_recov pae pat pausefilter 
  pclmulqdq pdpe1gb perfctr_core perfctr_nb pfthreshold pge pni popcnt pse 
  pse36 ptsc rdtscp rep_good sep skinit smep ssbd sse sse2 sse4_1 sse4_2 
  sse4a ssse3 svm svm_lock syscall tbm tce tsc tsc_scale v_vmsave_vmload 
  vgif vmcb_clean vme vmmcall wdt xop xsave xsaveopt 
  Vulnerabilities: Type: itlb_multihit status: Not affected 
  Type: l1tf status: Not affected 
  Type: mds status: Not affected 
  Type: meltdown status: Not affected 
  Type: spec_store_bypass 
  mitigation: Speculative Store Bypass disabled via prctl and seccomp 
  Type: spectre_v1 
  mitigation: usercopy/swapgs barriers and __user pointer sanitization 
  Type: spectre_v2 mitigation: Full AMD retpoline, IBPB: conditional, STIBP: 
  disabled, RSB filling 
  Type: srbds status: Not affected 
  Type: tsx_async_abort status: Not affected 
Graphics:
  Device-1: AMD Stoney [Radeon R2/R3/R4/R5 Graphics] vendor: Hewlett-Packard 
  driver: amdgpu v: kernel bus-ID: 00:01.0 chip-ID: 1002:98e4 class-ID: 0300 
  Device-2: Quanta HP Webcam type: USB driver: uvcvideo bus-ID: 2-1:2 
  chip-ID: 0408:5220 class-ID: 0e02 serial: 0x0001 
  Display: wayland server: X.Org 1.21.1.2 compositor: gnome-shell driver: 
  loaded: amdgpu note: n/a (using device driver) display-ID: :0 screens: 1 
  Screen-1: 0 s-res: 1920x1080 s-dpi: 96 s-size: 508x286mm (20.0x11.3") 
  s-diag: 583mm (23") 
  Monitor-1: XWAYLAND0 res: 1920x1080 hz: 60 dpi: 143 
  size: 340x190mm (13.4x7.5") diag: 389mm (15.3") 
  OpenGL: renderer: AMD STONEY (DRM 3.41.0 5.13.0-22-generic LLVM 12.0.1) 
  v: 4.5 Mesa 21.2.2 direct render: Yes 
Audio:
  Device-1: AMD vendor: Hewlett-Packard driver: snd_hda_intel v: kernel 
  bus-ID: 00:01.1 chip-ID: 1002:15b3 class-ID: 0403 
  Device-2: AMD Family 15h Audio vendor: Hewlett-Packard 
  driver: snd_hda_intel v: kernel bus-ID: 00:09.2 chip-ID: 1022:157a 
  class-ID: 0403 
  Sound Server-1: ALSA v: k5.13.0-22-generic running: yes 
  Sound Server-2: PulseAudio v: 15.0 running: yes 
  Sound Server-3: PipeWire v: 0.3.32 running: yes 
Network:
  Device-1: Realtek RTL8111/8168/8411 PCI Express Gigabit Ethernet 
  vendor: Hewlett-Packard driver: r8169 v: kernel port: 3000 bus-ID: 02:00.0 
  chip-ID: 10ec:8168 class-ID: 0200 
  IF: enp2s0 state: down mac: f4:39:09:e8:0a:68 
  Device-2: Intel Dual Band Wireless-AC 3168NGW [Stone Peak] driver: iwlwifi 
  v: kernel port: 3000 bus-ID: 03:00.0 chip-ID: 8086:24fb class-ID: 0280 
  IF: wlp3s0 state: up mac: 7c:2a:31:7f:2d:99 
  IP v4: 192.168.1.15/24 type: dynamic noprefixroute scope: global 
  broadcast: 192.168.1.255 
  IP v6: fe80::b82:ba52:aa4:998d/64 type: noprefixroute scope: link 
  WAN IP: 87.0.251.43 
Bluetooth:
  Device-1: Intel Wireless-AC 3168 Bluetooth type: USB driver: btusb v: 0.8 
  bus-ID: 1-1.4:3 chip-ID: 8087:0aa7 class-ID: e001 
  Report: hciconfig ID: hci0 rfk-id: 0 state: down 
  bt-service: enabled,running rfk-block: hardware: no software: yes 
  address: 7C:2A:31:7F:2D:9D 
  Info: acl-mtu: 1021:4 sco-mtu: 96:6 link-policy: rswitch sniff 
  link-mode: slave accept 
Logical:
  Message: No logical block device data found. 
RAID:
  Message: No RAID data found. 
Drives:
  Local Storage: total: 238.47 GiB used: 19.06 GiB (8.0%) 
  SMART Message: Required tool smartctl not installed. Check --recommends 
  ID-1: /dev/sda maj-min: 8:0 vendor: Samsung model: MZNLN256HAJQ-000H1 
  size: 238.47 GiB block-size: physical: 4096 B logical: 512 B 
  speed: 6.0 Gb/s type: SSD serial: S3T6NE0K881314 rev: 3H3Q scheme: GPT 
  Optical-1: /dev/sr0 vendor: hp model: DVDRW DA8AESH rev: XH6M 
  dev-links: cdrom,cdrw,dvd,dvdrw 
  Features: speed: 24 multisession: yes audio: yes dvd: yes 
  rw: cd-r,cd-rw,dvd-r state: running 
Partition:
  ID-1: / raw-size: 237.97 GiB size: 233.18 GiB (97.99%) 
  used: 19.05 GiB (8.2%) fs: ext4 dev: /dev/sda2 maj-min: 8:2 label: N/A 
  uuid: 8a244fb7-d8a1-4fca-990d-b9dd579d94a2 
  ID-2: /boot/efi raw-size: 512 MiB size: 511 MiB (99.80%) 
  used: 5.2 MiB (1.0%) fs: vfat dev: /dev/sda1 maj-min: 8:1 label: N/A 
  uuid: 1299-491B 
Swap:
  Kernel: swappiness: 60 (default) cache-pressure: 100 (default) 
  ID-1: swap-1 type: file size: 2 GiB used: 0 KiB (0.0%) priority: -2 
  file: /swapfile 
Unmounted:
  Message: No unmounted partitions found. 
USB:
  Hub-1: 1-0:1 info: Full speed (or root) Hub ports: 2 rev: 2.0 
  speed: 480 Mb/s chip-ID: 1d6b:0002 class-ID: 0900 
  Hub-2: 1-1:2 info: Advanced Micro Devices Root Hub ports: 4 rev: 2.0 
  speed: 480 Mb/s power: 100mA chip-ID: 0438:7900 class-ID: 0900 
  Device-1: 1-1.4:3 info: Intel Wireless-AC 3168 Bluetooth type: Bluetooth 
  driver: btusb interfaces: 2 rev: 2.0 speed: 12 Mb/s power: 100mA 
  chip-ID: 8087:0aa7 class-ID: e001 
  Hub-3: 2-0:1 info: Full speed (or root) Hub ports: 4 rev: 2.0 
  speed: 480 Mb/s chip-ID: 1d6b:0002 class-ID: 0900 
  Device-1: 2-1:2 info: Quanta HP Webcam type: Video driver: uvcvideo 
  interfaces: 2 rev: 2.0 speed: 480 Mb/s power: 500mA chip-ID: 0408:5220 
  class-ID: 0e02 serial: 0x0001 
  Hub-4: 3-0:1 info: Full speed (or root) Hub ports: 4 rev: 3.0 
  speed: 5 Gb/s chip-ID: 1d6b:0003 class-ID: 0900 
Sensors:
  System Temperatures: cpu: 50.6 C mobo: 20.0 C gpu: amdgpu temp: 50.0 C 
  Fan Speeds (RPM): N/A 
Repos:
  Packages: 1505 apt: 1486 lib: 695 snap: 19 
  Active apt repos in: /etc/apt/sources.list 
  1: deb http://it.archive.ubuntu.com/ubuntu/ impish main restricted
  2: deb http://it.archive.ubuntu.com/ubuntu/ impish-updates main restricted
  3: deb http://it.archive.ubuntu.com/ubuntu/ impish universe
  4: deb http://it.archive.ubuntu.com/ubuntu/ impish-updates universe
  5: deb http://it.archive.ubuntu.com/ubuntu/ impish multiverse
  6: deb http://it.archive.ubuntu.com/ubuntu/ impish-updates multiverse
  7: deb http://it.archive.ubuntu.com/ubuntu/ impish-backports main restricted universe multiverse
  8: deb http://security.ubuntu.com/ubuntu impish-security main restricted
  9: deb http://security.ubuntu.com/ubuntu impish-security universe
  10: deb http://security.ubuntu.com/ubuntu impish-security multiverse
Processes:
  CPU top: 5 of 233 
  1: cpu: 13.5% command: firefox pid: 2163 mem: 454.8 MiB (6.1%) 
  2: cpu: 6.6% command: gnome-shell pid: 1118 mem: 297.2 MiB (4.0%) 
  3: cpu: 3.5% command: firefox pid: 2335 mem: 157.4 MiB (2.1%) 
  4: cpu: 2.2% command: firefox pid: 3179 mem: 255.1 MiB (3.4%) 
  5: cpu: 1.8% command: gnome-terminal-server pid: 4019 mem: 48.3 MiB (0.6%) 
  Memory top: 5 of 233 
  1: mem: 454.8 MiB (6.1%) command: firefox pid: 2163 cpu: 13.5% 
  2: mem: 297.2 MiB (4.0%) command: gnome-shell pid: 1118 cpu: 6.6% 
  3: mem: 255.1 MiB (3.4%) command: firefox pid: 3179 cpu: 2.2% 
  4: mem: 183.7 MiB (2.4%) command: snap-store pid: 1483 cpu: 0.3% 
  5: mem: 168.4 MiB (2.2%) command: firefox pid: 2557 cpu: 0.9% 
Info:
  Processes: 233 Uptime: 33m wakeups: 1 Init: systemd v: 248 runlevel: 5 
  tool: systemctl Compilers: gcc: N/A Shell: Bash v: 5.1.8 
  running-in: gnome-terminal inxi: 3.3.06 

```


What I've tried:

1. Reinstalling Ubuntu
2. Installing an Ubuntu variant (kde)
3. Installing another debian based, POP OS.
4. Installing Ubunut LTS
5. Starting the session on both wayland and xorg

Nothing worked.

The only workaround I have found was disabling the password at the login: this way the machine works properly. But just after that I found out that the problem comes out even when the PC goes in standby: if I try to come back to the sessions after the suspend black screen the glitch comes up again.
Could it be a graphic server issue? An issue of the login manager?

Did you guys ever seen something like this? Does someone have a hint for me?
Thank you so much for every answer to the thread.

---

### Post by gsahli on 2021-12-06
I "think" it's an amdgpu driver issue.
Try this: edit /etc/default/grub (I use sudo nano to edit such files)
edit this line: GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
to read:
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash amdgpu.dc=0"
then save the file
now run: sudo update-grub
and reboot
This is disabling the DC layer in the driver.

---

### Post by nicolam94 on 2021-12-07
Thank you very much, that seem to have solved the problem! 
I'm curious though, can you explain to me what you mean by "disabling the DC layer in the driver"?
Thank you very much for the answer anyway!

---

