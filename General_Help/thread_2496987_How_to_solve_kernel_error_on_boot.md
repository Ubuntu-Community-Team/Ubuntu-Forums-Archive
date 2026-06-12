---
title: "How to solve kernel error on boot"
date: 2024-04-18
forum: General Help
---

### Post by luncaaa on 2024-04-18
Hello o/

I have an old potato laptop in which I installed Lubuntu 23.10 deleting everything else (I selected the delete disk option when installing it). It turns on and off fine but a screen appears for some seconds with the following warnings (from kern.log):
```
2024-04-11T20:51:07.662130+02:00 aspire kernel: [    4.406799] UBSAN: array-index-out-of-bounds in /build/linux-D15vQj/linux-6.5.0/drivers/gpu/drm/radeon/radeon_atombios.c:2715:55
2024-04-11T20:51:07.662134+02:00 aspire kernel: [    4.406822] index 1 is out of range for type 'UCHAR [1]'
2024-04-11T20:51:07.663263+02:00 aspire kernel: [    4.416921] UBSAN: array-index-out-of-bounds in /build/linux-D15vQj/linux-6.5.0/drivers/gpu/drm/radeon/radeon_atombios.c:2705:39
2024-04-11T20:51:07.663267+02:00 aspire kernel: [    4.416942] index 2 is out of range for type 'ATOM_PPLIB_NONCLOCK_INFO [1]'
2024-04-11T20:51:07.664411+02:00 aspire kernel: [    4.422136] UBSAN: array-index-out-of-bounds in /build/linux-D15vQj/linux-6.5.0/drivers/gpu/drm/radeon/sumo_dpm.c:1622:30
2024-04-11T20:51:07.664450+02:00 aspire kernel: [    4.422162] index 4 is out of range for type 'sumo_vid_mapping_entry [4]'
```

After searching these errors, I found multiple threads. One said that downgrading the kernel version was needed because it wasn't compatible with old specs, while another thread said that and update was probably needed. What should I do and what commands should I execute if necessary? (all packages from apt are up-to-date)

Information from **inxi -Fxxrzc0**:
```
System:
  Kernel: 6.5.0-27-generic arch: x86_64 bits: 64 compiler: N/A Desktop: LXQt
    v: 1.3.0 tk: Qt v: 5.15.10 wm: Openbox dm: SDDM Distro: Ubuntu 23.10
    (Mantic Minotaur)
Machine:
  Type: Laptop System: Acer product: Aspire V5-123 v: 1
    serial: <superuser required>
  Mobo: Acer model: ZA10_KB v: Type2 - A01 Board Version
    serial: <superuser required> UEFI: Insyde v: 2.03 date: 08/20/2013
Battery:
  ID-1: BAT1 charge: 46.7 Wh (96.9%) condition: 48.2/48.8 Wh (98.7%)
    volts: 12.1 min: 11.1 model: SANYO AL12B32 serial: <filter>
    status: discharging
CPU:
  Info: dual core model: AMD E1-2100 APU with Radeon HD Graphics bits: 64
    type: MCP arch: Jaguar rev: 1 cache: L1: 128 KiB L2: 1024 KiB
  Speed (MHz): avg: 800 min/max: 800/1000 boost: disabled cores: 1: 800
    2: 800 bogomips: 3992
  Flags: avx ht lm nx pae sse sse2 sse3 sse4_1 sse4_2 sse4a ssse3 svm
Graphics:
  Device-1: AMD Kabini [Radeon HD 8210] vendor: Acer Incorporated ALI
    driver: radeon v: kernel arch: GCN-2 ports: active: eDP-1
    empty: HDMI-A-1,VGA-1 bus-ID: 00:01.0 chip-ID: 1002:9834
  Device-2: Sunplus Innovation HD WebCam driver: uvcvideo type: USB rev: 2.0
    speed: 480 Mb/s lanes: 1 bus-ID: 1-2:2 chip-ID: 1bcf:2c54
  Display: x11 server: X.Org v: 1.21.1.7 compositor: Picom v: 10 driver: X:
    loaded: radeon unloaded: fbdev,modesetting,vesa dri: radeonsi gpu: radeon
    display-ID: :0 screens: 1
  Screen-1: 0 s-res: 1366x768 s-dpi: 96
  Monitor-1: eDP-1 mapped: eDP model: AU Optronics 0x105c res: 1366x768
    dpi: 136 diag: 294mm (11.6")
  API: OpenGL v: 4.5 Mesa 23.2.1-1ubuntu3.1 renderer: KABINI ( LLVM 15.0.7
    DRM 2.50 6.5.0-27-generic) direct-render: Yes
Audio:
  Device-1: AMD Kabini HDMI/DP Audio vendor: Acer Incorporated ALI
    driver: snd_hda_intel v: kernel bus-ID: 00:01.1 chip-ID: 1002:9840
  Device-2: AMD FCH Azalia vendor: Acer Incorporated ALI
    driver: snd_hda_intel v: kernel bus-ID: 00:14.2 chip-ID: 1022:780d
  API: ALSA v: k6.5.0-27-generic status: kernel-api
  Server-1: PipeWire v: 0.3.79 status: active with: 1: pipewire-pulse
    status: active 2: wireplumber status: active 3: pipewire-alsa type: plugin
Network:
  Device-1: Qualcomm Atheros QCA9565 / AR9565 Wireless Network Adapter
    vendor: Foxconn driver: ath9k v: kernel pcie: speed: 2.5 GT/s lanes: 1
    bus-ID: 01:00.0 chip-ID: 168c:0036
  IF: wlp1s0 state: up mac: <filter>
  Device-2: Qualcomm Atheros QCA8171 Gigabit Ethernet
    vendor: Acer Incorporated ALI driver: alx v: kernel pcie: speed: 2.5 GT/s
    lanes: 1 port: 2000 bus-ID: 02:00.0 chip-ID: 1969:10a1
  IF: enp2s0 state: down mac: <filter>
Bluetooth:
  Device-1: Foxconn / Hon Hai driver: btusb v: 0.8 type: USB rev: 1.1
    speed: 12 Mb/s lanes: 1 bus-ID: 4-4:3 chip-ID: 0489:e05f
  Report: hciconfig ID: hci0 rfk-id: 3 state: up address: <filter> bt-v: 4.1
    lmp-v: 7 sub-v: 1
Drives:
  Local Storage: total: 465.76 GiB used: 9.9 GiB (2.1%)
  ID-1: /dev/sda vendor: HGST (Hitachi) model: HTS545050A7E680
    size: 465.76 GiB speed: 6.0 Gb/s serial: <filter>
Partition:
  ID-1: / size: 457.09 GiB used: 9.89 GiB (2.2%) fs: ext4 dev: /dev/sda2
  ID-2: /boot/efi size: 299.4 MiB used: 7.7 MiB (2.6%) fs: vfat
    dev: /dev/sda1
Swap:
  ID-1: swap-1 type: file size: 512 MiB used: 0 KiB (0.0%) priority: -2
    file: /swapfile
Sensors:
  System Temperatures: cpu: 64.9 C mobo: N/A gpu: radeon temp: 64.0 C
  Fan Speeds (rpm): N/A
Repos:
  Packages: 1937 pm: dpkg pkgs: 1927 pm: snap pkgs: 10
  Active apt repos in: /etc/apt/sources.list
    1: deb http://archive.ubuntu.com/ubuntu/ mantic main restricted
    2: deb http://archive.ubuntu.com/ubuntu/ mantic-updates main restricted
    3: deb http://archive.ubuntu.com/ubuntu/ mantic universe
    4: deb http://archive.ubuntu.com/ubuntu/ mantic-updates universe
    5: deb http://archive.ubuntu.com/ubuntu/ mantic multiverse
    6: deb http://archive.ubuntu.com/ubuntu/ mantic-updates multiverse
    7: deb http://security.ubuntu.com/ubuntu mantic-security main restricted
    8: deb http://security.ubuntu.com/ubuntu mantic-security universe
    9: deb http://security.ubuntu.com/ubuntu mantic-security multiverse
    10: deb http://archive.ubuntu.com/ubuntu/ mantic-backports main restricted universe multiverse
Info:
  Processes: 171 Uptime: 9m Memory: total: 4 GiB note: est.
  available: 3.27 GiB used: 1.48 GiB (45.2%) Init: systemd v: 253
  target: graphical (5) default: graphical Compilers: N/A Shell: Bash
  v: 5.2.15 running-in: qterminal inxi: 3.3.29
```

---

### Post by guiverc on 2024-04-18
Is your system working correctly??  I wouldn't worry about your system if it was.

Your alternative, which can be the best option for older hardware, is a LTS release using the GA kernel stack.  As Ubuntu LTS releases have kernel stack options, you use the older GA option, with 5.15 being the kernel available for 22.04 LTS for example.

If you boot 22.04 or 22.04.1 media you could see if the message appears there (ie. older media using an older 5.15 kernel). If it's a boot message for example, you likely don't have to install anything, just boot the system in *live* or *Try* mode.  Using an older LTS kernel stack  could be an option going forward for you, as where as 23.10 is supported only until July 2024, using 22.04 still has years of support left. 

With a *flavor* like Lubuntu, the initial Lubuntu 22.04 LTS media, as well as Lubuntu 22.04.1 LTS media will install and use that kernel for the *life* of the product, however later 22.04.2, 22.04.3, 22.04.4, 22.04.5 media uses HWE kernels (22.04.4 using the 6.5 kernel you're using now for example).. so if you can find older 22.04(.1) media you can install it; however if you have a working 23.10 system you could install any 22.04 ISO and then switch from HWE kernel stack to the older GA kernel stack.

As for cause of message, sorry I'm not able to help you, but on hardware where I've seen it, I've not noticed any problems thus I ignore it.   The oldest machine I use in QA of Lubuntu currently is from 2005 (*though RAM & other upgrades since original purchase*)...

---

