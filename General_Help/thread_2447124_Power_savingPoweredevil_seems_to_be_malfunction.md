---
title: "Power saving/Poweredevil seems to be malfunction"
date: 2020-07-13
forum: General Help
---

### Post by Perfect Storm on 2020-07-13
Hello,

No matter what changes I make in Power Savings, they/it don't apply for some reason. Same things happens also in Manjaro Plasma when I was using it. It complaining about a shared library which I can't find in the repositories.

regards
Storm

This is what I get from output:
```
storm@universe:~$ systemsettings5
QQmlEngine::setContextForObject(): Object already has a QQmlContext
Couldn't load plugin: "The shared library was not found."
powerdevil: ("AC", "Battery", "migration", "LowBattery") ()
powerdevil: "Wireless"  has a runtime requirement
powerdevil: "Screen brightness"  has a runtime requirement
powerdevil: The action  QVariant(QString, "BrightnessControl")  appears not to be supported by the core.
powerdevil: "Dim screen"  has a runtime requirement
powerdevil: The action  QVariant(QString, "DimDisplay")  appears not to be supported by the core.
powerdevil: "Keyboard backlight"  has a runtime requirement
powerdevil: The action  QVariant(QString, "KeyboardBrightnessControl")  appears not to be supported by the core.
powerdevil: "Button events handling"  has a runtime requirement
powerdevil: "Screen Energy Saving"  has a runtime requirement
powerdevil: "Wireless"  has a runtime requirement
powerdevil: "Screen brightness"  has a runtime requirement
powerdevil: The action  QVariant(QString, "BrightnessControl")  appears not to be supported by the core.
powerdevil: "Dim screen"  has a runtime requirement
powerdevil: The action  QVariant(QString, "DimDisplay")  appears not to be supported by the core.
powerdevil: "Keyboard backlight"  has a runtime requirement
powerdevil: The action  QVariant(QString, "KeyboardBrightnessControl")  appears not to be supported by the core.
powerdevil: "Button events handling"  has a runtime requirement
powerdevil: "Screen Energy Saving"  has a runtime requirement
powerdevil: "Wireless"  has a runtime requirement
powerdevil: "Screen brightness"  has a runtime requirement
powerdevil: The action  QVariant(QString, "BrightnessControl")  appears not to be supported by the core.
powerdevil: "Dim screen"  has a runtime requirement
powerdevil: The action  QVariant(QString, "DimDisplay")  appears not to be supported by the core.
powerdevil: "Keyboard backlight"  has a runtime requirement
powerdevil: The action  QVariant(QString, "KeyboardBrightnessControl")  appears not to be supported by the core.
powerdevil: "Button events handling"  has a runtime requirement
powerdevil: "Screen Energy Saving"  has a runtime requirement
powerdevil: Loading routine called
powerdevil: ()
powerdevil: Ok, KConfigGroup ready ("icon")
powerdevil: ()
powerdevil: Ok, KConfigGroup ready ("icon")
powerdevil: ()
powerdevil: Ok, KConfigGroup ready ("icon")
```

My System:
```
:
 storm@universe:~$ inxi -Fxzc0

System:
 Kernel: 5.4.0-40-generic x86_64 bits: 64 compiler: gcc v: 9.3.0
 Desktop: KDE Plasma 5.18.5 Distro: Ubuntu 20.04 LTS (Focal Fossa)
Machine:
 Type: Desktop Mobo: ASUSTeK model: PRIME X370-A v: Rev X.0x serial: <filter>
 UEFI: American Megatrends v: 0805 date: 06/20/2017
Battery:
 Device-1: hidpp_battery_0 model: Logitech Wireless Solar Keyboard K750 charge: 93%
 status: N/A
 Device-2: hidpp_battery_1 model: Logitech Marathon Mouse/Performance Plus M705
 charge: 55% (should be ignored) status: Discharging
CPU:
 Topology: 8-Core model: AMD Ryzen 7 1700X bits: 64 type: MT MCP arch: Zen rev: 1
 L2 cache: 4096 KiB
 flags: avx avx2 lm nx pae sse sse2 sse3 sse4_1 sse4_2 sse4a ssse3 svm
 bogomips: 108583
 Speed: 2030 MHz min/max: 2200/3400 MHz Core speeds (MHz): 1: 1892 2: 1815 3: 2015
 4: 2029 5: 1824 6: 1742 7: 2683 8: 3493 9: 1853 10: 2141 11: 2108 12: 2142 13: 1865
 14: 1767 15: 1849 16: 1819
Graphics:
 Device-1: NVIDIA GP104 [GeForce GTX 1070] vendor: ASUSTeK driver: nvidia v: 440.100
 bus ID: 2a:00.0
 Display: x11 server: X.Org 1.20.8 driver: nvidia
 unloaded: fbdev,modesetting,nouveau,vesa resolution: 1920x1080~60Hz
 OpenGL: renderer: GeForce GTX 1070/PCIe/SSE2 v: 4.6.0 NVIDIA 440.100
 direct render: Yes
Audio:
 Device-1: NVIDIA GP104 High Definition Audio vendor: ASUSTeK driver: snd_hda_intel
 v: kernel bus ID: 2a:00.1
 Device-2: AMD Family 17h HD Audio vendor: ASUSTeK driver: snd_hda_intel v: kernel
 bus ID: 2c:00.3
 Sound Server: ALSA v: k5.4.0-40-generic
Network:
 Device-1: Qualcomm Atheros AR9227 Wireless Network Adapter driver: ath9k v: kernel
 bus ID: 27:01.0
 IF: wlp39s1 state: up mac: <filter>
 Device-2: Realtek RTL8111/8168/8411 PCI Express Gigabit Ethernet vendor: ASUSTeK
 driver: r8169 v: kernel port: f000 bus ID: 28:00.0
 IF: enp40s0 state: down mac: <filter>
Drives:
 Local Storage: total: 1.14 TiB used: 61.12 GiB (5.2%)
 ID-1: /dev/sda vendor: Samsung model: SSD 850 EVO 250GB size: 232.89 GiB
 ID-2: /dev/sdb vendor: Toshiba model: DT01ACA100 size: 931.51 GiB temp: 42 C
Partition:
 ID-1: / size: 227.77 GiB used: 10.91 GiB (4.8%) fs: ext4 dev: /dev/sda5
 ID-2: /home size: 915.89 GiB used: 50.20 GiB (5.5%) fs: ext4 dev: /dev/sdb1
Sensors:
 System Temperatures: cpu: 45.9 C mobo: N/A gpu: nvidia temp: 54 C
 Fan Speeds (RPM): N/A gpu: nvidia fan: 0%
Info:
 Processes: 334 Uptime: 5h 01m Memory: 31.36 GiB used: 4.61 GiB (14.7%) Init: systemd
 runlevel: 5 Compilers: gcc: 9.3.0 Shell: bash v: 5.0.16 inxi: 3.0.38
storm@universe:~$


```

---

### Post by Perfect Storm on 2020-07-13
I made a reinstall which solved my problem.

---

### Post by Perfect Storm on 2020-07-13
I spoke to soon. The problem still persist.

---

### Post by Perfect Storm on 2020-07-14
I have updated the BIOS to the latest - No cigar.

---

