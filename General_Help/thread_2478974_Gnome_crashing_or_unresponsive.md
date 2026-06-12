---
title: "Gnome crashing or unresponsive"
date: 2022-09-10
forum: General Help
---

### Post by Phineas on 2022-09-10
A week or so ago, I found that I would open my laptop and the Gnome would have crashed. I could Alt+F2 and use 'r' to restart it and all was well enough. I just assumed it was because I'm using a laptop from Costco and hardware or whatever. Then in the past day or so a new issue has come out where gnome becomes unresponsive while I'm in an app. Unresponsive such that even Alt+F2 doesn't work, and even as I type this the upper right buttons on the Firefox window are just round circles with no symbols for minimize or close, etc. When Gnome is unresponsive it won't let me click any icons on the taskbar, etc. I'm also finding that at some times no matter the window being shown on top, I'm interacting with another window.

The only way I can regain responsiveness is to drag the window I'm in such that it stops being maximized and that seems to give me some time to interact with Gnome before the responsiveness falls off again.

Anyone have any insights on this?

Edit: Wow I haven't used the forum in a long time. I just noticed it says I'm on 7.04 - that is obviously not true. This is the latest distro 22.04. -- Looks like since my account is so old I can't modify my profile to update that yet.

```

System:
  Kernel: 5.15.0-47-generic x86_64 bits: 64 compiler: gcc v: 11.2.0
    Desktop: GNOME 42.4 Distro: Ubuntu 22.04.1 LTS (Jammy Jellyfish)
Machine:
  Type: Laptop System: Micro-Star product: Alpha 15 B5EEK v: REV:1.0
    serial: <superuser required>
  Mobo: Micro-Star model: MS-158L v: REV:1.0 serial: <superuser required>
    UEFI: American Megatrends LLC. v: E158LAMS.104 date: 08/23/2021
Battery:
  ID-1: BAT1 charge: 83.3 Wh (98.7%) condition: 84.4/87.4 Wh (96.6%)
    volts: 17.2 min: 15.4 model: MSI Corp. MS-158L status: N/A
  Device-1: hidpp_battery_0 model: Logitech M570 charge: 90%
    status: Discharging
CPU:
  Info: 8-core model: AMD Ryzen 7 5800H with Radeon Graphics bits: 64
    type: MT MCP arch: Zen 3 rev: 0 cache: L1: 512 KiB L2: 4 MiB L3: 16 MiB
  Speed (MHz): avg: 2832 high: 3185 min/max: 400/4463 boost: enabled cores:
    1: 2534 2: 2535 3: 2835 4: 2881 5: 2925 6: 2790 7: 2936 8: 3018 9: 2589
    10: 2529 11: 3167 12: 3160 13: 3185 14: 3169 15: 2534 16: 2535
    bogomips: 102200
  Flags: avx avx2 ht lm nx pae sse sse2 sse3 sse4_1 sse4_2 sse4a ssse3 svm
Graphics:
  Device-1: AMD Navi 23 [Radeon RX 6600/6600 XT/6600M] vendor: Micro-Star MSI
    driver: amdgpu v: kernel bus-ID: 03:00.0
  Device-2: AMD Cezanne vendor: Micro-Star MSI driver: amdgpu v: kernel
    bus-ID: 07:00.0
  Device-3: Acer HD Webcam type: USB driver: uvcvideo bus-ID: 1-4:3
  Display: x11 server: X.Org v: 1.21.1.3 driver: X: loaded: amdgpu,ati
    unloaded: fbdev,modesetting,radeon,vesa gpu: amdgpu
    resolution: 1920x1080~144Hz
  OpenGL: renderer: AMD RENOIR (LLVM 13.0.1 DRM 3.42 5.15.0-47-generic)
    v: 4.6 Mesa 22.0.5 direct render: Yes
Audio:
  Device-1: AMD Navi 21 HDMI Audio [Radeon RX 6800/6800 XT / 6900 XT]
    driver: snd_hda_intel v: kernel bus-ID: 03:00.1
  Device-2: AMD Renoir Radeon High Definition Audio vendor: Micro-Star MSI
    driver: snd_hda_intel v: kernel bus-ID: 07:00.1
  Device-3: AMD Raven/Raven2/FireFlight/Renoir Audio Processor
    vendor: Micro-Star MSI driver: snd_rn_pci_acp3x v: kernel bus-ID: 07:00.5
  Device-4: AMD Family 17h HD Audio vendor: Micro-Star MSI
    driver: snd_hda_intel v: kernel bus-ID: 07:00.6
  Sound Server-1: ALSA v: k5.15.0-47-generic running: yes
  Sound Server-2: PulseAudio v: 15.99.1 running: yes
  Sound Server-3: PipeWire v: 0.3.48 running: yes
Network:
  Device-1: MEDIATEK driver: mt7921e v: kernel port: N/A bus-ID: 04:00.0
  IF: wlp4s0 state: up mac: <filter>
  Device-2: Realtek RTL8111/8168/8411 PCI Express Gigabit Ethernet
    vendor: Micro-Star MSI driver: r8169 v: kernel port: f000 bus-ID: 05:00.0
  IF: enp5s0 state: down mac: <filter>
Bluetooth:
  Device-1: MediaTek Wireless_Device type: USB driver: btusb v: 0.8
    bus-ID: 3-3:2
  Report: hciconfig ID: hci0 rfk-id: 0 state: up address: <filter>
    bt-v: 3.0 lmp-v: 5.2
Drives:
  Local Storage: total: 476.94 GiB used: 44.8 GiB (9.4%)
  ID-1: /dev/nvme0n1 vendor: Kingston model: OM8PCP3512F-AI1
    size: 476.94 GiB temp: 34.9 C
Partition:
  ID-1: / size: 263.62 GiB used: 44.76 GiB (17.0%) fs: ext4
    dev: /dev/nvme0n1p6
  ID-2: /boot/efi size: 296 MiB used: 35.9 MiB (12.1%) fs: vfat
    dev: /dev/nvme0n1p1
Swap:
  ID-1: swap-1 type: partition size: 2 GiB used: 0 KiB (0.0%)
    dev: /dev/nvme0n1p7
Sensors:
  System Temperatures: cpu: 67.0 C mobo: N/A
  Fan Speeds (RPM): N/A
  GPU: device: amdgpu temp: 48.0 C fan: 5 device: amdgpu temp: 61.0 C
Info:
  Processes: 416 Uptime: 19m Memory: 15.02 GiB used: 7.01 GiB (46.7%)
  Init: systemd runlevel: 5 Compilers: gcc: 11.2.0 Packages: 2611 Shell: Bash
  v: 5.1.16 inxi: 3.3.13

```

---

### Post by ajgreeny on 2022-09-10
To give you any useful help we need to know what the hardware actually is in that Costco laptop, so assuming you can actually get it to run to the desktop, open a terminal and run command ```
inxi -Fzx
``` then report back here the output you see.

Please use **Code-Tags** for terminal output as it makes that output much more easily read and understood, formatting the text as seen in terminal, not as plain text when it is copied and pasted. See my signature below for a **How-to**.

---

### Post by Phineas on 2022-09-10
inxi info added to top post

---

### Post by Phineas on 2022-09-10
Okay, so now I think the issue is actually my wireless trackball mouse. I'm not positive. But I booted into Windows and was also running into a few issues in a similar vein where the mouse was somehow interacting with a different window. So I've removed that mouse and so far, so good. Will follow up if it comes back.

---

