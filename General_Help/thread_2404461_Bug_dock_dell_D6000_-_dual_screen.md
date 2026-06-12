---
title: "Bug dock dell D6000 - dual screen"
date: 2018-10-24
forum: General Help
---

### Post by payet-benjamin-l on 2018-10-24
Hello,

From time to time I'm facing an issue with my Dell computer connected to a docking station dell D6000.
Indeed, it seems that the connectivity to this dock is some times crashing which cause my two external screens to not display anything anymore (black screens). When this issue occured I have to disconnect then reconnect the cable between my computer and the dock.

I'm using the driver " DisplayLink USB Graphics Software for Ubuntu 4.4", the OS Ubuntu 18.04.1 LTS.

Please find below an extract of the dmesg fetched right after the issue occured :

[18924.710643] usb 4-1.1: reset SuperSpeed USB device number 3 using xhci_hcd
[18924.744549] usb 4-1.1: Warning! Unlikely big volume range (=767), cval->res is probably wrong.
[18924.744557] usb 4-1.1: [4] FU [Mic Capture Volume] ch = 2, val = -4592/7680/16
[18924.745400] usb 4-1.1: Warning! Unlikely big volume range (=672), cval->res is probably wrong.
[18924.745409] usb 4-1.1: [7] FU [Dell USB Audio Playback Volume] ch = 6, val = -10752/0/16
[18924.766918] cdc_ncm 4-1.1:1.5: MAC-Address: 9c:eb:e8:68:4e:8f
[18924.766925] cdc_ncm 4-1.1:1.5: setting rx_max = 16384
[18924.767051] cdc_ncm 4-1.1:1.5: setting tx_max = 16384
[18924.767653] cdc_ncm 4-1.1:1.5 usb0: register 'cdc_ncm' at usb-0000:3b:00.0-1.1, CDC NCM, 9c:eb:e8:68:4e:8f
[18924.768555] usb 4-1.1: usbfs: process 1265 (DeviceWindowDis) did not claim interface 0 before use
[18924.776790] cdc_ncm 4-1.1:1.5 enx9cebe8684e8f: renamed from usb0
[18924.836227] IPv6: ADDRCONF(NETDEV_UP): enx9cebe8684e8f: link is not ready
[18924.836848] IPv6: ADDRCONF(NETDEV_UP): enx9cebe8684e8f: link is not ready
[18924.852741] cdc_ncm 4-1.1:1.5 enx9cebe8684e8f: network connection: disconnected
[18928.228824] cdc_ncm 4-1.1:1.5 enx9cebe8684e8f: 1000 mbit/s downlink 1000 mbit/s uplink
[18928.260825] cdc_ncm 4-1.1:1.5 enx9cebe8684e8f: network connection: connected
[18928.260902] IPv6: ADDRCONF(NETDEV_CHANGE): enx9cebe8684e8f: link becomes ready
[18930.971350] usb 3-1: USB disconnect, device number 2
[18930.971356] usb 3-1.2: USB disconnect, device number 3
[18930.972657] usb 3-1.3: USB disconnect, device number 4
[18930.972686] usb 3-1.3.1: USB disconnect, device number 6
[18930.976360] usb 3-1.4: USB disconnect, device number 5
[18930.986041] xhci_hcd 0000:3b:00.0: xHCI host controller not responding, assume dead
[18930.986154] xhci_hcd 0000:3b:00.0: HC died; cleaning up
[18930.986255] usb 4-1: USB disconnect, device number 2
[18930.986267] usb 4-1.1: USB disconnect, device number 3
[18930.996291] cdc_ncm 4-1.1:1.5 enx9cebe8684e8f: unregister 'cdc_ncm' usb-0000:3b:00.0-1.1, CDC NCM
[18931.115116] xhci_hcd 0000:3b:00.0: remove, state 1
[18931.115151] usb usb4: USB disconnect, device number 1
[18931.115351] usb 4-1.2: USB disconnect, device number 4
[18931.123847] xhci_hcd 0000:3b:00.0: USB bus 4 deregistered
[18931.123890] xhci_hcd 0000:3b:00.0: remove, state 1
[18931.123914] usb usb3: USB disconnect, device number 1
[18931.134889] evdi: [D] evdi_painter_disconnect:612 (dev=1) Disconnected from 0000000021119283
[18931.134904] evdi: [D] evdi_detect:79 Painter is disconnected
[18931.157324] evdi: [D] evdi_painter_disconnect:612 (dev=2) Disconnected from 00000000f6d42c36
[18931.157328] evdi: [D] evdi_detect:79 Painter is disconnected
[18931.238689] xhci_hcd 0000:3b:00.0: Host halt failed, -19
[18931.238692] xhci_hcd 0000:3b:00.0: Host not accessible, reset failed.
[18931.238791] xhci_hcd 0000:3b:00.0: USB bus 3 deregistered
[18931.383597] acpi INT3400:00: Unsupported event [0x86]
[18931.402595] pci_bus 0000:04: Allocating resources
[18931.402659] pcieport 0000:04:02.0: bridge window [mem 0x00100000-0x000fffff 64bit pref] to [bus 3b] add_size 200000 add_align 100000
[18931.402687] pcieport 0000:04:02.0: BAR 15: no space for [mem size 0x00200000 64bit pref]
[18931.402692] pcieport 0000:04:02.0: BAR 15: failed to assign [mem size 0x00200000 64bit pref]
[18931.402699] pcieport 0000:04:02.0: BAR 15: no space for [mem size 0x00200000 64bit pref]
[18931.402703] pcieport 0000:04:02.0: BAR 15: failed to assign [mem size 0x00200000 64bit pref]
[18931.423491] evdi: [D] evdi_detect:79 Painter is disconnected
[18931.424239] evdi: [D] evdi_detect:79 Painter is disconnected
[18931.491742] evdi: [D] evdi_painter_crtc_state_notify:483 (dev=-1) Notifying crtc state: 3
[18931.491746] evdi: [W] evdi_painter_send_crtc_state:389 Painter is not connected!
[18931.492870] evdi: [D] evdi_painter_crtc_state_notify:483 (dev=-1) Notifying crtc state: 3
[18931.492873] evdi: [W] evdi_painter_send_crtc_state:389 Painter is not connected!
[18931.973813] evdi: [D] evdi_detect:79 Painter is disconnected
[18931.973822] evdi: [D] evdi_detect:79 Painter is disconnected
[18936.178538] pcieport 0000:04:00.0: Refused to change power state, currently in D3
[18936.179941] pci_bus 0000:05: busn_res: [bus 05] is released
[18936.180030] pci_bus 0000:06: busn_res: [bus 06-3a] is released
[18936.180100] pci_bus 0000:3b: busn_res: [bus 3b] is released
[18936.181107] pci_bus 0000:04: busn_res: [bus 04-3b] is released


Can someone please help me to solve this problem ? Thank you.

---

