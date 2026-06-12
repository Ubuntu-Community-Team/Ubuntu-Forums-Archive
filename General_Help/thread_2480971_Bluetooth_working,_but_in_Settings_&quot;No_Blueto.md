---
title: "Bluetooth working, but in Settings &quot;No Bluetooth Found&quot;"
date: 2022-11-15
forum: General Help
---

### Post by aaronwilbers on 2022-11-15
Hello.  I didn't see this exact issue but sorry if I missed a thread.  I have Ubuntu installed on this intel system.  I'm connected to a Bluetooth device for internet right now, and if I run the *Blueman Bluetooth Manager* application I downloaded from the repositories I see the Bluetooth devices and can add and connect.  If I go into Settings>Network I can click the toggle to allow the system to use the Bluetooth connection for internet. 

 But in Settings>Bluetooth it says there is no Bluetooth adapter installed.  I'm just trying to fix this.

  When I first installed this adapter, [COLOR=#0F1111][FONT=&amp]*FebSmart AX3000 PCI Express WiFi adapter is based on Intel WiFi 6 AX200NGW WiFi module*,[/FONT][/COLOR] on my prior build of 22.04 it showed up in the settings just fine.  But I clicked the slider to shut if off and after that it never would come back on per the Settings though it would work fine using the Blueman app.

I was in the process of rebuilding the system so I did a fresh install of 22.04 LTS and it is still showing as no dongle connected, though Bluetooth still works.  I'm just trying to fix the Settings issue so I can see the BT in that.  I didn't install Blueman until the Bluetooth part of settings stopped working. 
 
```
aaron@YGGDRASIL:~$ uname -a
Linux YGGDRASIL 5.15.0-52-generic #58-Ubuntu SMP Thu Oct 13 08:03:55 UTC 2022 x86_64 x86_64 x86_64 GNU/Linux

aaron@YGGDRASIL:~$ sudo dmesg | grep -i blue
[   27.547699] Bluetooth: Core ver 2.22
[   27.547715] NET: Registered PF_BLUETOOTH protocol family
[   27.547716] Bluetooth: HCI device and connection manager initialized
[   27.547719] Bluetooth: HCI socket layer initialized
[   27.547738] Bluetooth: L2CAP socket layer initialized
[   27.547742] Bluetooth: SCO socket layer initialized
[   27.596843] Bluetooth: hci0: Bootloader revision 0.3 build 0 week 24 2017
[   27.597884] Bluetooth: hci0: Device revision is 1
[   27.597886] Bluetooth: hci0: Secure boot is enabled
[   27.597887] Bluetooth: hci0: OTP lock is enabled
[   27.597888] Bluetooth: hci0: API lock is enabled
[   27.597888] Bluetooth: hci0: Debug lock is disabled
[   27.597889] Bluetooth: hci0: Minimum firmware build 1 week 10 2014
[   27.600378] Bluetooth: hci0: Found device firmware: intel/ibt-20-1-3.sfi
[   28.686563] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   28.686566] Bluetooth: BNEP filters: protocol multicast
[   28.686569] Bluetooth: BNEP socket layer initialized
[   29.338487] Bluetooth: hci0: Waiting for firmware download to complete
[   29.338830] Bluetooth: hci0: Firmware loaded in 1697704 usecs
[   29.338871] Bluetooth: hci0: Waiting for device to boot
[   29.352864] Bluetooth: hci0: Device booted in 13692 usecs
[   29.353328] Bluetooth: hci0: Found Intel DDC parameters: intel/ibt-20-1-3.ddc
[   29.355909] Bluetooth: hci0: Applying Intel DDC parameters completed
[   29.358896] Bluetooth: hci0: Firmware revision 0.3 build 126 week 5 2022
[1045432.528748] Bluetooth: RFCOMM TTY layer initialized
[1045432.528755] Bluetooth: RFCOMM socket layer initialized
[1045432.528759] Bluetooth: RFCOMM ver 1.11

aaron@YGGDRASIL:~$ sudo systemctl status bluetooth
&#9679; bluetooth.service - Bluetooth service
     Loaded: loaded (/lib/systemd/system/bluetooth.service; enabled; vendor preset: enabled)
     Active: active (running) since Thu 2022-11-03 08:07:41 CDT; 1 week 5 days ago
       Docs: man:bluetoothd(8)
   Main PID: 1093 (bluetoothd)
     Status: "Running"
      Tasks: 1 (limit: 19032)
     Memory: 2.3M
        CPU: 6.600s
     CGroup: /system.slice/bluetooth.service
             &#9492;&#9472;1093 /usr/lib/bluetooth/bluetoothd


Nov 03 08:07:41 YGGDRASIL bluetoothd[1093]: Bluetooth management interface 1.21 initialized
Nov 15 09:31:05 YGGDRASIL bluetoothd[1093]: Endpoint registered: sender=:1.264 path=/MediaEndpoint/A2DPSink/sbc
Nov 15 09:31:05 YGGDRASIL bluetoothd[1093]: Endpoint registered: sender=:1.264 path=/MediaEndpoint/A2DPSource/sbc
Nov 15 09:31:05 YGGDRASIL bluetoothd[1093]: Endpoint registered: sender=:1.264 path=/MediaEndpoint/A2DPSink/sbc_xq_453
Nov 15 09:31:05 YGGDRASIL bluetoothd[1093]: Endpoint registered: sender=:1.264 path=/MediaEndpoint/A2DPSource/sbc_xq_453
Nov 15 09:31:05 YGGDRASIL bluetoothd[1093]: Endpoint registered: sender=:1.264 path=/MediaEndpoint/A2DPSink/sbc_xq_512
Nov 15 09:31:05 YGGDRASIL bluetoothd[1093]: Endpoint registered: sender=:1.264 path=/MediaEndpoint/A2DPSource/sbc_xq_512
Nov 15 09:31:05 YGGDRASIL bluetoothd[1093]: Endpoint registered: sender=:1.264 path=/MediaEndpoint/A2DPSink/sbc_xq_552
Nov 15 09:31:05 YGGDRASIL bluetoothd[1093]: Endpoint registered: sender=:1.264 path=/MediaEndpoint/A2DPSource/sbc_xq_552
Nov 15 09:32:34 YGGDRASIL bluetoothd[1093]: bnep0 connected




```

---

