---
title: "Kk freezes: GPU HANG"
date: 2022-12-08
forum: General Help
---

### Post by benjaminbreeg on 2022-12-08
My KK Ubuntu freezes occasionally and randomly. Here's how this seems to be reflected in syslog:


```

    Dec  7 22:58:24 DadsLGGram google-chrome.desktop[7760]: [7869:12220:1207/225824.514766:ERROR:vulkan_swap_chain.cc(442)] vkAcquireNextImageKHR() hangs.
    Dec  7 22:58:24 DadsLGGram google-chrome.desktop[7760]: [7869:7869:1207/225824.515372:ERROR:gpu_service_impl.cc(988)] Exiting GPU process because some drivers can't recover from errors. GPU process will restart shortly.
    Dec  7 22:58:24 DadsLGGram google-chrome.desktop[7760]: [7753:7753:1207/225824.532073:ERROR:gpu_process_host.cc(990)] GPU process exited unexpectedly: exit_code=8704
    Dec  7 22:58:27 DadsLGGram kernel: [ 3056.086872] i915 0000:00:02.0: [drm] GPU HANG: ecode 12:1:859ffffb
    Dec  7 22:58:27 DadsLGGram kernel: [ 3056.086955] i915 0000:00:02.0: [drm] Resetting chip for stopped heartbeat on rcs0
    Dec  7 22:58:27 DadsLGGram kernel: [ 3056.188365] i915 0000:00:02.0: [drm] GuC firmware i915/adlp_guc_70.1.1.bin version 70.1
    Dec  7 22:58:27 DadsLGGram kernel: [ 3056.188368] i915 0000:00:02.0: [drm] HuC firmware i915/tgl_huc_7.9.3.bin version 7.9
    Dec  7 22:58:27 DadsLGGram kernel: [ 3056.207405] i915 0000:00:02.0: [drm] HuC authenticated
    Dec  7 22:58:27 DadsLGGram kernel: [ 3056.207993] i915 0000:00:02.0: [drm] GuC submission enabled
    Dec  7 22:58:27 DadsLGGram kernel: [ 3056.207994] i915 0000:00:02.0: [drm] GuC SLPC enabled
    Dec  7 22:58:27 DadsLGGram google-chrome.desktop[7760]: libva error: vaGetDriverNameByIndex() failed with unknown libva error, driver_name = (null)

```

Now, I can see that there's a Chrome portion, and a kernel portion, and I am not really sure if these two are related. At any rate, I'd appreciate some pointers.


Upon request, I can post [inxi]([https://github.com/smxi/inxi](https://github.com/smxi/inxi)) details of my laptop.

---

### Post by MAFoElffen on 2022-12-09
Please run the [UbuntuForums 'system-info' script]("https://github.com/UbuntuForums/system-info") on it and post the URL of the pastebin you load the report to. That will give a better idea of both the hardware and how it is configured.

---

### Post by benjaminbreeg on 2022-12-09
Thank you for the reply. It turns out that [disabling hardware acceleration in Chrome did the trick]("https://www.reddit.com/r/Ubuntu/comments/zfz8nh/ubuntu_kk_crash_gpu_hang/"). Latest Chrome (108) released a few days ago has a bug on Ubuntu (Linux?), as I've had no problems with previous Chrome versions.

Just for kicks, here's what inxi says about my computer:

System:
  Kernel: 5.19.0-26-generic arch: x86_64 bits: 64 compiler: N/A
    Desktop: GNOME v: 43.0 Distro: Ubuntu 22.10 (Kinetic Kudu)
Machine:
  Type: Laptop System: LG product: 17Z90Q-K.ADC9U1 v: 0.1 serial: <filter>
  Mobo: LG model: 17Z90Q v: FAB1 serial: <filter> UEFI: Phoenix
    v: A1ZG0360 X64 date: 06/02/2022
Battery:
  ID-1: CMB0 charge: 75.3 Wh (94.1%) condition: 80.0/80.0 Wh (100.0%)
    volts: 8.7 min: 7.7 model: LG LGES-LG status: not charging
  Device-1: hidpp_battery_0 model: Logitech M585/M590 Multi-Device Mouse
    charge: 100% (should be ignored) status: discharging
  Device-2: hidpp_battery_1 model: Logitech K850 Performance Wireless
    Keyboard charge: 100% (should be ignored) status: discharging
CPU:
  Info: 12-core (4-mt/8-st) model: 12th Gen Intel Core i7-1260P bits: 64
    type: MST AMCP arch: Alder Lake rev: 3 cache: L1: 1.1 MiB L2: 9 MiB
    L3: 18 MiB
  Speed (MHz): avg: 1908 high: 4207 min/max: 400/4700:3400 cores: 1: 4207
    2: 3939 3: 2500 4: 453 5: 2500 6: 2500 7: 2214 8: 1105 9: 1645 10: 2500
    11: 1994 12: 1345 13: 696 14: 1058 15: 1482 16: 400 bogomips: 79872
  Flags: avx avx2 ht lm nx pae sse sse2 sse3 sse4_1 sse4_2 ssse3 vmx
Graphics:
  Device-1: Intel Alder Lake-P Integrated Graphics vendor: LG driver: i915
    v: kernel arch: Gen-12.2 bus-ID: 00:02.0
  Device-2: Luxvisions Innotech LGE Camera type: USB driver: uvcvideo
    bus-ID: 1-2:2
  Device-3: Integrated Express USB3.0 4K30 Video type: USB
    driver: hid-generic,snd-usb-audio,usbhid,uvcvideo bus-ID: 4-3.3.4:7
  Device-4: Logitech BRIO Ultra HD Webcam type: USB
    driver: hid-generic,snd-usb-audio,usbhid,uvcvideo bus-ID: 4-3.4.4:11
  Display: server: X.Org v: 1.22.1.3 with: Xwayland v: 22.1.3 driver:
    gpu: evdi,i915 note:  X driver n/a resolution: 1: 3840x2160~60Hz
    2: 3840x2160~60Hz
  OpenGL: renderer: Mesa Intel Graphics (ADL GT2) v: 4.6 Mesa 22.2.1
    direct render: Yes
Audio:
  Device-1: Intel Alder Lake PCH-P High Definition Audio vendor: LG
    driver: sof-audio-pci-intel-tgl bus-ID: 4-3.3.4:7
  Device-2: Integrated Express USB3.0 4K30 Video type: USB
    driver: hid-generic,snd-usb-audio,usbhid,uvcvideo
  Device-3: DisplayLink USB3.0 Ultra Docking station type: USB
    driver: cdc_ncm,snd-usb-audio,usbfs bus-ID: 4-3.4.2:9
  Device-4: Logitech BRIO Ultra HD Webcam type: USB
    driver: hid-generic,snd-usb-audio,usbhid,uvcvideo bus-ID: 4-3.4.4:11
  Sound Server-1: ALSA v: k5.19.0-26-generic running: yes
  Sound Server-2: PipeWire v: 0.3.58 running: yes
Network:
  Device-1: Intel Alder Lake-P PCH CNVi WiFi driver: iwlwifi v: kernel
    bus-ID: 00:14.3
  IF: wlp0s20f3 state: down mac: <filter>
  IF-ID-1: enx44a92c5141c6 state: up speed: 1000 Mbps duplex: half
    mac: <filter>
Bluetooth:
  Device-1: Intel type: USB driver: btusb v: 0.8 bus-ID: 1-10:4
  Report: hciconfig ID: hci0 rfk-id: 0 state: up address: <filter>
Drives:
  Local Storage: total: 3.22 TiB used: 398.96 GiB (12.1%)
  ID-1: /dev/nvme0n1 vendor: Samsung model: MZVL21T0HCLR-00B00
    size: 953.87 GiB temp: 53.9 C
  ID-2: /dev/sda type: USB vendor: SanDisk model: Extreme 55AE
    size: 1.82 TiB
  ID-3: /dev/sdb type: USB vendor: Generic model: MassStorageClass
    size: 238.75 GiB
  ID-4: /dev/sdc type: USB vendor: Generic model: MassStorageClass
    size: 238.75 GiB
Partition:
  ID-1: / size: 937.34 GiB used: 15.14 GiB (1.6%) fs: ext4
    dev: /dev/nvme0n1p2
  ID-2: /boot/efi size: 511 MiB used: 5.2 MiB (1.0%) fs: vfat
    dev: /dev/nvme0n1p1
Swap:
  ID-1: swap-1 type: file size: 2 GiB used: 0 KiB (0.0%) file: /swapfile
Sensors:
  System Temperatures: cpu: 87.0 C mobo: N/A
  Fan Speeds (RPM): N/A
Info:
  Processes: 471 Uptime: 58m Memory: 31.04 GiB used: 6.8 GiB (21.9%)
  Init: systemd target: graphical (5) Compilers: gcc: 12.2.0 Packages: 2115
  Shell: Sudo v: 1.9.11p3 inxi: 3.3.21

---

