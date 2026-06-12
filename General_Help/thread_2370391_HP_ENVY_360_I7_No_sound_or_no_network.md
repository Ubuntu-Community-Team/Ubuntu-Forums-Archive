---
title: "HP ENVY 360 I7 No sound or no network"
date: 2017-09-02
forum: General Help
---

### Post by KmCsDFL on 2017-09-02
HI,
Purchased HP ENVY 360 15 inch I7 .
Running ubuntu 16.04

**With  the kernel  (default xenial) 4.4.0-31-generic I have no sound, but i have wifi**

Here are my shell info:
[COLOR=#0000cd]marius@hpsp:~$ aplay -l
aplay: device_list:268: no soundcards found...

marius@hpsp:~$ pactl list sinks
Sink #0
    State: SUSPENDED
    Name: auto_null
    Description: Dummy Output
    Driver: module-null-sink.c
    Sample Specification: s16le 2ch 44100Hz
    Channel Map: front-left,front-right
    Owner Module: 13
    Mute: no
    Volume: front-left: 40960 /  63% / -12.25 dB,   front-right: 40960 /  63% / -12.25 dB
            balance 0.00
    Base Volume: 65536 / 100% / 0.00 dB
    Monitor Source: auto_null.monitor
    Latency: 0 usec, configured 0 usec
    Flags: DECIBEL_VOLUME LATENCY 
    Properties:
        device.description = "Dummy Output"
        device.class = "abstract"
        device.icon_name = "audio-card"
    Formats:
        pcm[/COLOR]

[COLOR=#0000cd]marius@hpsp:/lib/modules$ lspci
00:00.0 Host bridge: Intel Corporation Device 5904 (rev 02)
00:02.0 VGA compatible controller: Intel Corporation Device 5916 (rev 02)
00:04.0 Signal processing controller: Intel Corporation Skylake Processor Thermal Subsystem (rev 02)
00:13.0 Non-VGA unclassified device: Intel Corporation Device 9d35 (rev 21)
00:14.0 USB controller: Intel Corporation Sunrise Point-LP USB 3.0 xHCI Controller (rev 21)
00:14.2 Signal processing controller: Intel Corporation Sunrise Point-LP Thermal subsystem (rev 21)
00:15.0 Signal processing controller: Intel Corporation Sunrise Point-LP Serial IO I2C Controller (rev 21)
00:15.1 Signal processing controller: Intel Corporation Sunrise Point-LP Serial IO I2C Controller (rev 21)
00:16.0 Communication controller: Intel Corporation Sunrise Point-LP CSME HECI (rev 21)
00:17.0 SATA controller: Intel Corporation Sunrise Point-LP SATA Controller [AHCI mode] (rev 21)
00:1c.0 PCI bridge: Intel Corporation Device 9d10 (rev f1)
00:1c.4 PCI bridge: Intel Corporation Sunrise Point-LP PCI Express Root Port (rev f1)
00:1d.0 PCI bridge: Intel Corporation Device 9d18 (rev f1)
00:1d.1 PCI bridge: Intel Corporation Device 9d19 (rev f1)
00:1f.0 ISA bridge: Intel Corporation Device 9d4e (rev 21)
00:1f.2 Memory controller: Intel Corporation Sunrise Point-LP PMC (rev 21)
00:1f.3 Audio device: Intel Corporation Device 9d71 (rev 21)
00:1f.4 SMBus: Intel Corporation Sunrise Point-LP SMBus (rev 21)
01:00.0 3D controller: NVIDIA Corporation GM108M [GeForce 940MX] (rev a2)
02:00.0 Non-Volatile memory controller: Toshiba America Info Systems Device 0115 (rev 01)
03:00.0 Unassigned class [ff00]: Realtek Semiconductor Co., Ltd. RTS522A PCI Express Card Reader (rev 01)
04:00.0 Network controller: Intel Corporation Wireless 7265 (rev 59)

[/COLOR]

**With kernel 4.11.0-041100-generic I h ave sound but I have no network interfaces,no eth wlan's.**

Any ideas.

---

### Post by KmCsDFL on 2017-09-03
kernel 4.9, all good. wifi and sound

---

