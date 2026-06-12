---
title: "bluetooth audio - a2dp missing"
date: 2024-08-20
forum: General Help
---

### Post by luzip665 on 2024-08-20
Hello,

after a fresh installation of XUbuntu 24.04 I try to connect to my headset using bluetooth.

For that I use blueman-manager.

I can connect to my headset, but I cannot switch to audio profile a2dp. It's just missing in the context menu. There are only HSP/HFP, HSP/HFP Codec CVSD and HSP/HFP Codec mSBC.


If I try with live cd everything is there.


Please, can someone tell me if I am missing some packages?

```

inxi -A (as user)
Audio:
  Device-1: AMD Renoir Radeon High Definition Audio driver: snd_hda_intel
  Device-2: AMD ACP/ACP3X/ACP6x Audio Coprocessor driver: N/A
  Device-3: AMD Family 17h/19h HD Audio driver: snd_hda_intel
  API: ALSA v: k6.8.0-40-generic status: kernel-api
  Server-1: PipeWire v: 1.0.5 status: active

```

```

lspci
00:00.0 Host bridge: Advanced Micro Devices, Inc. [AMD] Renoir/Cezanne Root Complex
00:00.2 IOMMU: Advanced Micro Devices, Inc. [AMD] Renoir/Cezanne IOMMU
00:01.0 Host bridge: Advanced Micro Devices, Inc. [AMD] Renoir PCIe Dummy Host Bridge
00:02.0 Host bridge: Advanced Micro Devices, Inc. [AMD] Renoir PCIe Dummy Host Bridge
00:02.1 PCI bridge: Advanced Micro Devices, Inc. [AMD] Renoir/Cezanne PCIe GPP Bridge
00:02.2 PCI bridge: Advanced Micro Devices, Inc. [AMD] Renoir/Cezanne PCIe GPP Bridge
00:02.3 PCI bridge: Advanced Micro Devices, Inc. [AMD] Renoir/Cezanne PCIe GPP Bridge
00:02.4 PCI bridge: Advanced Micro Devices, Inc. [AMD] Renoir/Cezanne PCIe GPP Bridge
00:02.6 PCI bridge: Advanced Micro Devices, Inc. [AMD] Renoir/Cezanne PCIe GPP Bridge
00:08.0 Host bridge: Advanced Micro Devices, Inc. [AMD] Renoir PCIe Dummy Host Bridge
00:08.1 PCI bridge: Advanced Micro Devices, Inc. [AMD] Renoir Internal PCIe GPP Bridge to Bus
00:14.0 SMBus: Advanced Micro Devices, Inc. [AMD] FCH SMBus Controller (rev 51)
00:14.3 ISA bridge: Advanced Micro Devices, Inc. [AMD] FCH LPC Bridge (rev 51)
00:18.0 Host bridge: Advanced Micro Devices, Inc. [AMD] Cezanne Data Fabric; Function 0
00:18.1 Host bridge: Advanced Micro Devices, Inc. [AMD] Cezanne Data Fabric; Function 1
00:18.2 Host bridge: Advanced Micro Devices, Inc. [AMD] Cezanne Data Fabric; Function 2
00:18.3 Host bridge: Advanced Micro Devices, Inc. [AMD] Cezanne Data Fabric; Function 3
00:18.4 Host bridge: Advanced Micro Devices, Inc. [AMD] Cezanne Data Fabric; Function 4
00:18.5 Host bridge: Advanced Micro Devices, Inc. [AMD] Cezanne Data Fabric; Function 5
00:18.6 Host bridge: Advanced Micro Devices, Inc. [AMD] Cezanne Data Fabric; Function 6
00:18.7 Host bridge: Advanced Micro Devices, Inc. [AMD] Cezanne Data Fabric; Function 7
01:00.0 Non-Volatile memory controller: Sandisk Corp WD Black SN770 / PC SN740 256GB / PC SN560 (DRAM-less) NVMe SSD (rev 01)
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168/8211/8411 PCI Express Gigabit Ethernet Controller (rev 0e)
03:00.0 Network controller: Realtek Semiconductor Co., Ltd. RTL8852AE 802.11ax PCIe Wireless Network Adapter
04:00.0 SD Host controller: O2 Micro, Inc. SD/MMC Card Reader Controller (rev 01)
06:00.0 USB controller: Renesas Technology Corp. uPD720202 USB 3.0 Host Controller (rev 02)
07:00.0 VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] Cezanne [Radeon Vega Series / Radeon Vega Mobile Series] (rev d2)
07:00.1 Audio device: Advanced Micro Devices, Inc. [AMD/ATI] Renoir Radeon High Definition Audio Controller
07:00.2 Encryption controller: Advanced Micro Devices, Inc. [AMD] Family 17h (Models 10h-1fh) Platform Security Processor
07:00.3 USB controller: Advanced Micro Devices, Inc. [AMD] Renoir/Cezanne USB 3.1
07:00.4 USB controller: Advanced Micro Devices, Inc. [AMD] Renoir/Cezanne USB 3.1
07:00.5 Multimedia controller: Advanced Micro Devices, Inc. [AMD] ACP/ACP3X/ACP6x Audio Coprocessor (rev 01)
07:00.6 Audio device: Advanced Micro Devices, Inc. [AMD] Family 17h/19h HD Audio Controller

```

```

syslog after connecting to my my headset
2024-08-20T22:39:49.820372+02:00 lpmobil bluealsa: bluez.c:1199: Signal: org.freedesktop.DBus.ObjectManager.InterfacesAdded()
2024-08-20T22:39:49.820911+02:00 lpmobil bluealsa: bluez.c:1290: Adding new Stream End-Point: 88:08:94:A3:19:AB: SNK: SBC
2024-08-20T22:39:49.820978+02:00 lpmobil bluealsa: bluez.c:1199: Signal: org.freedesktop.DBus.ObjectManager.InterfacesAdded()
2024-08-20T22:39:49.821036+02:00 lpmobil bluealsa: bluez.c:1290: Adding new Stream End-Point: 88:08:94:A3:19:AB: SNK: AAC
2024-08-20T22:39:49.844857+02:00 lpmobil bluealsa: dbus.c:47: Called: org.bluez.MediaEndpoint1.SelectConfiguration() on /org/bluez/hci0/A2DP/SBC/source/1
2024-08-20T22:39:49.844973+02:00 lpmobil bluealsa: bluez.c:280: A2DP peer capabilities blob [len=4]: 7fff0835
2024-08-20T22:39:49.856835+02:00 lpmobil bluealsa: bluez.c:1199: Signal: org.freedesktop.DBus.ObjectManager.InterfacesAdded()
2024-08-20T22:39:49.857032+02:00 lpmobil bluealsa: dbus.c:47: Called: org.bluez.MediaEndpoint1.SetConfiguration() on /org/bluez/hci0/A2DP/SBC/source/1
2024-08-20T22:39:49.857119+02:00 lpmobil bluealsa: a2dp.c:383: Selected A2DP SBC bit-pool range: [8, 53]
2024-08-20T22:39:49.857195+02:00 lpmobil bluealsa: storage.c:117: Loading storage: /var/lib/bluealsa/88:08:94:A3:19:AB
2024-08-20T22:39:49.857384+02:00 lpmobil bluealsa: bluez.c:420: A2DP Source (SBC) configured for device 88:08:94:A3:19:AB
2024-08-20T22:39:49.857500+02:00 lpmobil bluealsa: bluez.c:423: A2DP selected configuration blob [len=4]: 11150835
2024-08-20T22:39:49.857575+02:00 lpmobil bluealsa: bluez.c:425: PCM configuration: channels: 2, sampling: 48000
2024-08-20T22:39:49.965928+02:00 lpmobil kernel: Bluetooth: hci0: SCO packet for unknown connection handle 2
2024-08-20T22:39:49.965950+02:00 lpmobil kernel: input: Smokin' Buds (AVRCP) as /devices/virtual/input/input18
2024-08-20T22:39:50.062909+02:00 lpmobil wireplumber[1842]: Properties changed in unknown transport '/org/bluez/hci0/dev_88_08_94_A3_19_AB/sep1/fd1'. Multiple sound server instances (PipeWire/Pulseaudio/bluez-alsa) are probably trying to use Bluetooth audio at the same time, which can cause problems. The system configuration likely should be fixed to have only one sound server that manages Bluetooth audio.
2024-08-20T22:39:50.063102+02:00 lpmobil bluealsa: bluez.c:1407: Signal: org.freedesktop.DBus.Properties.PropertiesChanged(): org.bluez.MediaTransport1: Volume
2024-08-20T22:39:50.063244+02:00 lpmobil bluealsa: bluez.c:1425: Skipping A2DP volume update: 64
2024-08-20T22:39:50.171420+02:00 lpmobil wireplumber[1842]: RFCOMM receive command but modem not available: AT+CSCS="UTF-8"#015
2024-08-20T22:39:52.247674+02:00 lpmobil pipewire-pulse[1843]: mod.protocol-pulse: client 0x64507ac30000 [PulseAudio-Lautstärkeregler]: ERROR command:104 (SEND_OBJECT_MESSAGE) tag:274 error:3 (Das Argument ist ungültig)
2024-08-20T22:39:52.247909+02:00 lpmobil pipewire-pulse[1843]: mod.protocol-pulse: client 0x64507ac30000 [PulseAudio-Lautstärkeregler]: ERROR command:104 (SEND_OBJECT_MESSAGE) tag:275 error:3 (Das Argument ist ungültig)
2024-08-20T22:39:52.398192+02:00 lpmobil bluealsa: bluez.c:1199: Signal: org.freedesktop.DBus.ObjectManager.InterfacesAdded()

```


Thank you in advance!

---

### Post by #&amp;thj^% on 2024-08-20
Audio and Bluetooth is the worst I've seen on any previous versions of buntu's
will you show me this:
```
bluetoothctl show
## And this:
systemctl status bluetooth|grep A2DP
```

---

### Post by &amp;KyT$0P# on 2024-08-20
> **luzip665 said:**
> If I try with live cd everything is there.


Please, can someone tell me if I am missing some packages?

As a start, you could try comparing output of this command in the live CD vs your system -
```
dpkg-query -W | grep -P -i 'blue|libspa|pipewire|pulse'
```

> **luzip665 said:**
> ```

2024-08-20T22:39:50.062909+02:00 lpmobil wireplumber[1842]: Properties changed in unknown transport '/org/bluez/hci0/dev_88_08_94_A3_19_AB/sep1/fd1'. Multiple sound server instances (PipeWire/Pulseaudio/bluez-alsa) are probably trying to use Bluetooth audio at the same time, which can cause problems. The system configuration likely should be fixed to have only one sound server that manages Bluetooth audio.

```

Do you get this log message in the live CD when it works correctly?

---

### Post by luzip665 on 2024-08-21
I compared installed packages from live cd and installation and removed the following

bluez-alsa-utils
gnome-bluetooth-3-common
gnome-bluetooth-sendto
gstreamer1.0-pipewire
libasound2-plugin-bluez
libgnome-bluetooth-3.0-13
pipewire-alsa
pipewire-audio



Now it works with my headset.

But the next thing is my JBL Flip 3. With this the problem remains.



This message is not there anymore
```

2024-08-20T22:39:50.062909+02:00 lpmobil wireplumber[1842]: Properties changed in unknown transport '/org/bluez/hci0/dev_88_08_94_A3_19_AB/sep1/fd1'. Multiple sound server instances (PipeWire/Pulseaudio/bluez-alsa) are probably trying to use Bluetooth audio at the same time, which can cause problems. The system configuration likely should be fixed to have only one sound server that manages Bluetooth audio

```


Result of dpkg-query on local installation
```

blueman 2.3.5-3build1
bluez   5.72-0ubuntu5
bluez-alsa-utils        4.1.1-1build3
bluez-cups      5.72-0ubuntu5
bluez-obexd     5.72-0ubuntu5
libbluetooth3:amd64     5.72-0ubuntu5
libgnome-bluetooth-ui-3.0-13:amd64      46.0-1build1
libpipewire-0.3-0t64:amd64      1.0.5-1ubuntu1
libpipewire-0.3-common  1.0.5-1ubuntu1
libpipewire-0.3-modules:amd64   1.0.5-1ubuntu1
libpulse-mainloop-glib0:amd64   1:16.1+dfsg1-2ubuntu10
libpulse0:amd64 1:16.1+dfsg1-2ubuntu10
libspa-0.2-bluetooth:amd64      1.0.5-1ubuntu1
libspa-0.2-modules:amd64        1.0.5-1ubuntu1
libspandsp2t64:amd64    0.0.6+dfsg-2.1build1
pipewire:amd64  1.0.5-1ubuntu1
pipewire-bin    1.0.5-1ubuntu1
pipewire-pulse  1.0.5-1ubuntu1
pulseaudio      1:16.1+dfsg1-2ubuntu10
pulseaudio-utils        1:16.1+dfsg1-2ubuntu10
xfce4-pulseaudio-plugin:amd64   0.4.8-1build2

```

on live cd
```

blueman 2.3.5-3build1
bluez   5.72-0ubuntu5
bluez-cups      5.72-0ubuntu5
bluez-obexd     5.72-0ubuntu5
libbluetooth3:amd64     5.72-0ubuntu5
libpipewire-0.3-0t64:amd64      1.0.5-1ubuntu1
libpipewire-0.3-common  1.0.5-1ubuntu1
libpipewire-0.3-modules:amd64   1.0.5-1ubuntu1
libpulse-mainloop-glib0:amd64   1:16.1+dfsg1-2ubuntu10
libpulse0:amd64 1:16.1+dfsg1-2ubuntu10
libspa-0.2-bluetooth:amd64      1.0.5-1ubuntu1
libspa-0.2-modules:amd64        1.0.5-1ubuntu1
pipewire:amd64  1.0.5-1ubuntu1
pipewire-bin    1.0.5-1ubuntu1
pipewire-pulse  1.0.5-1ubuntu1
pulseaudio      1:16.1+dfsg1-2ubuntu10
pulseaudio-utils        1:16.1+dfsg1-2ubuntu10
xfce4-pulseaudio-plugin:amd64   0.4.8-1build2

```


What I wonder is the package bluez-alsa-utils. It is named in the local dpkg-query but it's not installed anymore

---

### Post by luzip665 on 2024-08-21
After removing and reconnecting the JBL box I can switch to a2pd.

But if I try to change the output in pavucontrol following appears in syslog

```

2024-08-21T17:08:38.965736+02:00 lpmobil kernel: Bluetooth: hci0: SCO packet for unknown connection handle 10
2024-08-21T17:08:38.965751+02:00 lpmobil kernel: input: JBL Flip 3 (AVRCP) as /devices/virtual/input/input36
2024-08-21T17:08:39.847262+02:00 lpmobil bluetoothd[3755]: profiles/audio/avdtp.c:cancel_request() Open: Connection timed out (110)
2024-08-21T17:08:39.847774+02:00 lpmobil wireplumber[1838]: Acquire /org/bluez/hci0/dev_B8_D5_0B_DA_87_C4/sep1/fd3 returned error: org.bluez.Error.Failed
2024-08-21T17:08:39.847893+02:00 lpmobil wireplumber[1838]: (bluez_output.B8_D5_0B_DA_87_C4.1-61) running -> error (Received error event)
2024-08-21T17:08:39.847977+02:00 lpmobil wireplumber[1838]: Failure in Bluetooth audio transport /org/bluez/hci0/dev_B8_D5_0B_DA_87_C4/sep1/fd3
2024-08-21T17:08:39.848239+02:00 lpmobil pipewire[1831]: pw.node: (bluez_output.B8_D5_0B_DA_87_C4.1-61) running -> error (Received error event)
2024-08-21T17:08:41.846936+02:00 lpmobil bluetoothd[3755]: profiles/audio/avdtp.c:cancel_request() Abort: Connection timed out (110)
2024-08-21T17:08:41.852813+02:00 lpmobil pipewire-pulse[1839]: mod.protocol-pulse: client 0x602047b8a2a0 [PulseAudio-Lautstärkeregler]: ERROR command:-1 (invalid) tag:4294967295 error:25 (Eingabe-/Ausgabefehler)
2024-08-21T17:08:41.865595+02:00 lpmobil pipewire-pulse[1839]: mod.protocol-pulse: client 0x602047b8a2a0 [PulseAudio-Lautstärkeregler]: ERROR command:104 (SEND_OBJECT_MESSAGE) tag:1388 error:3 (Das Argument ist ungültig)
2024-08-21T17:08:41.865709+02:00 lpmobil pipewire-pulse[1839]: mod.protocol-pulse: client 0x602047b8a2a0 [PulseAudio-Lautstärkeregler]: ERROR command:104 (SEND_OBJECT_MESSAGE) tag:1389 error:3 (Das Argument ist ungültig)

```


It works with profile HSP/HFP, but not with profile a2dp

---

