---
title: "Syslog flooded w/ACPI error entries"
date: 2022-12-20
forum: General Help
---

### Post by benjaminbreeg on 2022-12-20
These are the entries that get repeated every 2 seconds in my syslog:

```
Dec 19 23:43:09 DadsLGGram kernel: [ 1102.583569] 
Dec 19 23:43:09 DadsLGGram kernel: [ 1102.583570] 
Dec 19 23:43:09 DadsLGGram kernel: [ 1102.583570] Initialized Local Variables for Method [_TMP]:
Dec 19 23:43:09 DadsLGGram kernel: [ 1102.583570]   Local0: 0000000099fc2ba8 <Obj>           Integer 0000000000000038
Dec 19 23:43:09 DadsLGGram kernel: [ 1102.583574] 
Dec 19 23:43:09 DadsLGGram kernel: [ 1102.583575] No Arguments are initialized for method [_TMP]
Dec 19 23:43:09 DadsLGGram kernel: [ 1102.583575] 
Dec 19 23:43:09 DadsLGGram kernel: [ 1102.583576] ACPI Error: Aborting method \_SB.PC00.LPCB.LGEC.SEN2._TMP due to previous error (AE_NOT_EXIST) (20220331/psparse-529)
Dec 19 23:43:13 DadsLGGram kernel: [ 1106.590603] ACPI Error: No handler for Region [XIN1] (0000000030431499) [UserDefinedRegion] (20220331/evregion-130)
Dec 19 23:43:13 DadsLGGram kernel: [ 1106.590612] ACPI Error: Region UserDefinedRegion (ID=143) has no handler (20220331/exfldio-261)

```

As a result, syslog is rendered unusable. At the very least, I would like to suppress them from syslog. Tried the ```
loglevel=3
``` trick, didn't help.

Ubuntu Kinetic on a 2022 LGGram. See details below:

```
System:  Kernel: 5.19.0-26-generic arch: x86_64 bits: 64 compiler: N/A
    Desktop: GNOME v: 43.1 Distro: Ubuntu 22.10 (Kinetic Kudu)
Machine:
  Type: Laptop System: LG product: 17Z90Q-K.ADC9U1 v: 0.1 serial: <filter>
  Mobo: LG model: 17Z90Q v: FAB1 serial: <filter> UEFI: Phoenix
    v: A1ZG0360 X64 date: 06/02/2022
Battery:
  ID-1: CMB0 charge: 79.4 Wh (99.2%) condition: 80.0/80.0 Wh (100.0%)
    volts: 8.9 min: 7.7 model: LG LGES-LG status: charging
  Device-1: hidpp_battery_2 model: Logitech M585/M590 Multi-Device Mouse
    charge: 100% (should be ignored) status: discharging
  Device-2: hidpp_battery_3 model: Logitech K850 Performance Wireless
    Keyboard charge: 100% (should be ignored) status: discharging
CPU:
  Info: 12-core (4-mt/8-st) model: 12th Gen Intel Core i7-1260P bits: 64
    type: MST AMCP arch: Alder Lake rev: 3 cache: L1: 1.1 MiB L2: 9 MiB
    L3: 18 MiB
  Speed (MHz): avg: 1989 high: 3301 min/max: 400/4700:3400 cores: 1: 2972
    2: 872 3: 2511 4: 2518 5: 1399 6: 1665 7: 1861 8: 1994 9: 2357 10: 1310
    11: 2412 12: 3301 13: 2405 14: 1696 15: 1421 16: 1136 bogomips: 79872
  Flags: avx avx2 ht lm nx pae sse sse2 sse3 sse4_1 sse4_2 ssse3 vmx
Graphics:
  Device-1: Intel Alder Lake-P Integrated Graphics vendor: LG driver: i915
    v: kernel arch: Gen-12.2 bus-ID: 00:02.0
  Device-2: Integrated Express USB3.0 4K30 Video type: USB
    driver: hid-generic,snd-usb-audio,usbhid,uvcvideo bus-ID: 2-3.3.4:16
  Device-3: Logitech BRIO Ultra HD Webcam type: USB
    driver: hid-generic,snd-usb-audio,usbhid,uvcvideo bus-ID: 2-3.4.4:20
  Device-4: Luxvisions Innotech LGE Camera type: USB driver: uvcvideo
    bus-ID: 3-2:2
  Display: server: X.Org v: 1.22.1.3 with: Xwayland v: 22.1.3 driver:
    gpu: evdi,i915 note:  X driver n/a resolution: 1: 3840x2160~60Hz
    2: 3840x2160~60Hz
  OpenGL: renderer: Mesa Intel Graphics (ADL GT2) v: 4.6 Mesa 22.2.1
    direct render: Yes
Audio:
  Device-1: Intel Alder Lake PCH-P High Definition Audio vendor: LG
    driver: sof-audio-pci-intel-tgl bus-ID: 2-3.3.4:16
  Device-2: Integrated Express USB3.0 4K30 Video type: USB
    driver: hid-generic,snd-usb-audio,usbhid,uvcvideo
  Device-3: DisplayLink USB3.0 Ultra Docking station type: USB
    driver: cdc_ncm,snd-usb-audio,usbfs bus-ID: 2-3.4.2:18
  Device-4: Logitech BRIO Ultra HD Webcam type: USB
    driver: hid-generic,snd-usb-audio,usbhid,uvcvideo bus-ID: 2-3.4.4:20
  Sound Server-1: ALSA v: k5.19.0-26-generic running: yes
  Sound Server-2: PulseAudio v: 16.1 running: no
  Sound Server-3: PipeWire v: 0.3.58 running: yes
Network:
  Device-1: Intel Alder Lake-P PCH CNVi WiFi driver: iwlwifi v: kernel
    bus-ID: 00:14.3
  IF: wlp0s20f3 state: down mac: <filter>
  IF-ID-1: enx44a92c5141c6 state: up speed: 1000 Mbps duplex: half
    mac: <filter>
Bluetooth:
  Device-1: Intel type: USB driver: btusb v: 0.8 bus-ID: 3-10:3
  Report: hciconfig ID: hci0 rfk-id: 0 state: up address: <filter>
Drives:
  Local Storage: total: 3.22 TiB used: 410.31 GiB (12.5%)
  ID-1: /dev/nvme0n1 vendor: Samsung model: MZVL21T0HCLR-00B00
    size: 953.87 GiB temp: 47.9 C
  ID-2: /dev/sda type: USB vendor: SanDisk model: Extreme 55AE
    size: 1.82 TiB
  ID-3: /dev/sdb type: USB vendor: SMI (STMicroelectronics) model: USB DISK
    size: 238.75 GiB
  ID-4: /dev/sdc type: USB vendor: Generic model: MassStorageClass
    size: 238.75 GiB
Partition:
  ID-1: / size: 937.34 GiB used: 38.91 GiB (4.2%) fs: ext4
    dev: /dev/nvme0n1p2
  ID-2: /boot/efi size: 511 MiB used: 5.2 MiB (1.0%) fs: vfat
    dev: /dev/nvme0n1p1
Swap:
  ID-1: swap-1 type: file size: 2 GiB used: 0 KiB (0.0%) file: /swapfile
Sensors:
  System Temperatures: cpu: 75.0 C mobo: N/A
  Fan Speeds (RPM): N/A
Info:
  Processes: 409 Uptime: 34m Memory: 31.04 GiB used: 5.66 GiB (18.2%)
  Init: systemd target: graphical (5) Compilers: gcc: 12.2.0 Packages: 2176
  Shell: Sudo v: 1.9.11p3 inxi: 3.3.21

```

---

### Post by benjaminbreeg on 2023-01-10
Rumor has it that [COLOR=#1C1C1C][FONT=&amp]RTD3 might be the culprit, so I [/FONT][/COLOR][attempted to disable that in BIOS]("https://github.com/dhedlund/kernel-patch-lg-gram-17/issues/4#issue-1528165854")[COLOR=#1C1C1C][FONT=&amp], though it doesn't work due to the fact that "ITBT RTD3 Disabled is not supported when SW CM is applied for OS." [/FONT][/COLOR][COLOR=#1C1C1C][FONT=&amp]Any ideas as to what "SW CM is applied for OS" might mean? And how I can get rid of it?

[IMG]https://i.imgur.com/AhGYDGS.jpg[/IMG]

[/FONT][/COLOR]

---

