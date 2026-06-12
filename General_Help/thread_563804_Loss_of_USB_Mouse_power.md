---
title: "Loss of USB Mouse power"
date: 2007-09-30
forum: General Help
---

### Post by Robbyx on 2007-09-30
I was just transfering a file from my Olympus DS2300 digital recorder that is connected via a USB cable. In the middle of the transfer the USB Logitech MX500 mouse  lost it power as the laser turned off. I had to move the mouse to a new USB slot. It then worked. Is there any way of trouble shooting the mouse's loss of power?

Notes:
FIesty
Olympus mounted as a removable drive: not through its uuid because I could not find it.


Robin

---

### Post by geraldm on 2007-10-01
What did the log say when the mouse lost power;  /var/log/syslog
Was there a message that a usb device disconnected, say the mouse device?
Was the only device affected just the mouse, or other usb devices as well?
Did the file transfer complete OK?

Gerald

---

### Post by Robbyx on 2007-10-01
> **geraldm said:**
> What did the log say when the mouse lost power;  /var/log/syslog
Was there a message that a usb device disconnected, say the mouse device?
Was the only device affected just the mouse, or other usb devices as well?
Did the file transfer complete OK?

Gerald

No disconnection message.
The mouse was the only connected device that was affected.
When I switched the usb socket over so that power was restored I was able to transfer the file.

Syslog was restarted this morning when the computer was turned on. I do not have a log of that event from yesterday. However this morning's log may give ain indication because there are a lot of unknown outputIN entries which may indicate a conflict. I do not know so here is the log:


```
Oct  1 08:06:45 robin-desktop syslogd 1.4.1#20ubuntu4: restart.
Oct  1 08:06:45 robin-desktop anacron[6120]: Job `cron.daily' terminated
Oct  1 08:06:45 robin-desktop anacron[6120]: Normal exit (1 job run)
Oct  1 08:07:44 robin-desktop kernel: [  580.666403] Unknown OutputIN= OUT=vmnet8 SRC=172.16.77.1 DST=172.16.77.255 LEN=265 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=138 DPT=138 LEN=245 
Oct  1 08:07:44 robin-desktop kernel: [  580.666737] Unknown OutputIN= OUT=vmnet1 SRC=192.168.208.1 DST=192.168.208.255 LEN=265 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=138 DPT=138 LEN=245 
Oct  1 08:09:34 robin-desktop kernel: [  690.378931] Unknown OutputIN= OUT=vmnet8 SRC=172.16.77.1 DST=172.16.77.255 LEN=78 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=137 DPT=137 LEN=58 
Oct  1 08:09:34 robin-desktop kernel: [  690.379354] Unknown OutputIN= OUT=vmnet1 SRC=192.168.208.1 DST=192.168.208.255 LEN=78 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=137 DPT=137 LEN=58 
Oct  1 08:11:44 robin-desktop kernel: [  820.039201] Unknown OutputIN= OUT=vmnet8 SRC=172.16.77.1 DST=172.16.77.255 LEN=265 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=138 DPT=138 LEN=245 
Oct  1 08:11:44 robin-desktop kernel: [  820.039304] Unknown OutputIN= OUT=vmnet1 SRC=192.168.208.1 DST=192.168.208.255 LEN=265 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=138 DPT=138 LEN=245 
Oct  1 08:13:01 robin-desktop gconfd (robin-22928): starting (version 2.18.0.1), pid 22928 user 'robin'
Oct  1 08:13:01 robin-desktop gconfd (robin-22928): Resolved address "xml:readonly:/etc/gconf/gconf.xml.mandatory" to a read-only configuration source at position 0
Oct  1 08:13:01 robin-desktop gconfd (robin-22928): Resolved address "xml:readwrite:/home/robin/.gconf" to a writable configuration source at position 1
Oct  1 08:13:01 robin-desktop gconfd (robin-22928): Resolved address "xml:readonly:/etc/gconf/gconf.xml.defaults" to a read-only configuration source at position 2
Oct  1 08:13:01 robin-desktop gconfd (robin-22928): Resolved address "xml:readonly:/var/lib/gconf/debian.defaults" to a read-only configuration source at position 3
Oct  1 08:13:01 robin-desktop gconfd (robin-22928): Resolved address "xml:readonly:/var/lib/gconf/defaults" to a read-only configuration source at position 4
Oct  1 08:13:07 robin-desktop kernel: [  902.278433] ISO 9660 Extensions: Microsoft Joliet Level 3
Oct  1 08:13:07 robin-desktop kernel: [  902.518591] ISO 9660 Extensions: RRIP_1991A
Oct  1 08:13:07 robin-desktop gconfd (robin-22928): Resolved address "xml:readwrite:/home/robin/.gconf" to a writable configuration source at position 0
Oct  1 08:13:11 robin-desktop NetworkManager: <information>^IUpdating allowed wireless network lists. 
Oct  1 08:13:12 robin-desktop NetworkManager: <WARNING>^I nm_dbus_get_networks_cb (): error received: org.freedesktop.NetworkManagerInfo.NoNetworks - There are no wireless networks stored.. 
Oct  1 08:14:34 robin-desktop kernel: [  989.598963] Unknown OutputIN= OUT=vmnet8 SRC=172.16.77.1 DST=172.16.77.255 LEN=78 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=137 DPT=137 LEN=58 
Oct  1 08:14:34 robin-desktop kernel: [  989.701847] Unknown OutputIN= OUT=vmnet1 SRC=192.168.208.1 DST=192.168.208.255 LEN=78 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=137 DPT=137 LEN=58 
Oct  1 08:16:30 robin-desktop firefox-bin: F 10-01 08:16:29 23276      firefox-bin ipc_client.cc:85] fd too big, check fd leak first!
Oct  1 08:16:44 robin-desktop kernel: [ 1119.358943] Unknown OutputIN= OUT=vmnet8 SRC=172.16.77.1 DST=172.16.77.255 LEN=265 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=138 DPT=138 LEN=245 
Oct  1 08:16:44 robin-desktop kernel: [ 1119.359047] Unknown OutputIN= OUT=vmnet1 SRC=192.168.208.1 DST=192.168.208.255 LEN=265 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=138 DPT=138 LEN=245 
Oct  1 08:17:01 robin-desktop /USR/SBIN/CRON[23532]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Oct  1 08:17:02 robin-desktop gdl_update: E 10-01 08:17:01 23541       gdl_update proxy_detect.cc:335] Failed to parse prefs: /root/.mozilla/firefox/vyrew1tj.default/prefs.js
Oct  1 08:19:19 robin-desktop kernel: [ 1273.575165] usb 2-6: USB disconnect, address 4
Oct  1 08:19:19 robin-desktop NetworkManager: <debug info>^I[1191223159.364108] nm_hal_device_removed (): Device removed (hal udi is '/org/freedesktop/Hal/devices/usb_device_46d_c025_noserial_if0_logicaldev_input'). 
Oct  1 08:19:19 robin-desktop NetworkManager: <debug info>^I[1191223159.366431] nm_hal_device_removed (): Device removed (hal udi is '/org/freedesktop/Hal/devices/usb_device_46d_c025_noserial_if0'). 
Oct  1 08:19:19 robin-desktop NetworkManager: <debug info>^I[1191223159.372316] nm_hal_device_removed (): Device removed (hal udi is '/org/freedesktop/Hal/devices/usb_device_46d_c025_noserial'). 
Oct  1 08:19:19 robin-desktop NetworkManager: <debug info>^I[1191223159.375903] nm_hal_device_removed (): Device removed (hal udi is '/org/freedesktop/Hal/devices/usb_device_46d_c025_noserial_usbraw'). 
Oct  1 08:19:20 robin-desktop kernel: [ 1274.229080] usb 2-6: new low speed USB device using ohci_hcd and address 7
Oct  1 08:19:20 robin-desktop kernel: [ 1274.442629] usb 2-6: configuration #1 chosen from 1 choice
Oct  1 08:19:20 robin-desktop NetworkManager: <debug info>^I[1191223160.228125] nm_hal_device_added (): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_46d_c025_noserial'). 
Oct  1 08:19:20 robin-desktop kernel: [ 1274.452664] input: B16_b_02 USB-PS/2 Optical Mouse as /class/input/input6
Oct  1 08:19:20 robin-desktop kernel: [ 1274.452727] input: USB HID v1.10 Mouse [B16_b_02 USB-PS/2 Optical Mouse] on usb-0000:00:0b.0-6
Oct  1 08:19:20 robin-desktop NetworkManager: <debug info>^I[1191223160.305456] nm_hal_device_added (): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_46d_c025_noserial_if0'). 
Oct  1 08:19:20 robin-desktop kernel: [ 1274.574942] usb 2-6: USB disconnect, address 7
Oct  1 08:19:20 robin-desktop NetworkManager: <debug info>^I[1191223160.378926] nm_hal_device_removed (): Device removed (hal udi is '/org/freedesktop/Hal/devices/usb_device_46d_c025_noserial_if0'). 
Oct  1 08:19:20 robin-desktop NetworkManager: <debug info>^I[1191223160.387536] nm_hal_device_removed (): Device removed (hal udi is '/org/freedesktop/Hal/devices/usb_device_46d_c025_noserial'). 
Oct  1 08:19:20 robin-desktop NetworkManager: <debug info>^I[1191223160.401158] nm_hal_device_added (): New device added (hal udi is '/org/freedesktop/Hal/devices/computer_logicaldev_input_2'). 
Oct  1 08:19:21 robin-desktop kernel: [ 1275.234445] usb 2-6: new low speed USB device using ohci_hcd and address 8
Oct  1 08:19:21 robin-desktop kernel: [ 1275.446001] usb 2-6: configuration #1 chosen from 1 choice
Oct  1 08:19:21 robin-desktop NetworkManager: <debug info>^I[1191223161.235758] nm_hal_device_added (): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_46d_c025_noserial'). 
Oct  1 08:19:21 robin-desktop kernel: [ 1275.455993] input: B16_b_02 USB-PS/2 Optical Mouse as /class/input/input7
Oct  1 08:19:21 robin-desktop kernel: [ 1275.456056] input: USB HID v1.10 Mouse [B16_b_02 USB-PS/2 Optical Mouse] on usb-0000:00:0b.0-6
Oct  1 08:19:21 robin-desktop NetworkManager: <debug info>^I[1191223161.304106] nm_hal_device_added (): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_46d_c025_noserial_if0'). 
Oct  1 08:19:21 robin-desktop NetworkManager: <debug info>^I[1191223161.412078] nm_hal_device_added (): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_46d_c025_noserial_if0_logicaldev_input'). 
Oct  1 08:19:21 robin-desktop lomoco: 002.008: 046d:c025 MX500 Optical Mouse (M-BP81A) Caps: RES SMS
Oct  1 08:19:21 robin-desktop lomoco: SmartScroll disabled
Oct  1 08:19:21 robin-desktop NetworkManager: <debug info>^I[1191223161.524293] nm_hal_device_added (): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_46d_c025_noserial_usbraw'). 
Oct  1 08:19:34 robin-desktop kernel: [ 1288.934627] Unknown OutputIN= OUT=vmnet8 SRC=172.16.77.1 DST=172.16.77.255 LEN=78 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=137 DPT=137 LEN=58 
Oct  1 08:19:34 robin-desktop kernel: [ 1288.934771] Unknown OutputIN= OUT=vmnet1 SRC=192.168.208.1 DST=192.168.208.255 LEN=78 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=137 DPT=137 LEN=58 
Oct  1 08:21:05 robin-desktop kernel: [ 1379.875421] usb 2-6: USB disconnect, address 8
Oct  1 08:21:06 robin-desktop NetworkManager: <debug info>^I[1191223266.003442] nm_hal_device_removed (): Device removed (hal udi is '/org/freedesktop/Hal/devices/usb_device_46d_c025_noserial_if0'). 
Oct  1 08:21:06 robin-desktop NetworkManager: <debug info>^I[1191223266.006422] nm_hal_device_removed (): Device removed (hal udi is '/org/freedesktop/Hal/devices/usb_device_46d_c025_noserial_if0_logicaldev_input'). 
Oct  1 08:21:06 robin-desktop NetworkManager: <debug info>^I[1191223266.095526] nm_hal_device_removed (): Device removed (hal udi is '/org/freedesktop/Hal/devices/usb_device_46d_c025_noserial'). 
Oct  1 08:21:06 robin-desktop NetworkManager: <debug info>^I[1191223266.334348] nm_hal_device_removed (): Device removed (hal udi is '/org/freedesktop/Hal/devices/usb_device_46d_c025_noserial_usbraw'). 
Oct  1 08:21:06 robin-desktop kernel: [ 1380.530562] usb 2-6: new low speed USB device using ohci_hcd and address 9
Oct  1 08:21:06 robin-desktop kernel: [ 1380.745106] usb 2-6: configuration #1 chosen from 1 choice
Oct  1 08:21:06 robin-desktop kernel: [ 1380.756093] input: B16_b_02 USB-PS/2 Optical Mouse as /class/input/input8
Oct  1 08:21:06 robin-desktop kernel: [ 1380.756156] input: USB HID v1.10 Mouse [B16_b_02 USB-PS/2 Optical Mouse] on usb-0000:00:0b.0-6
Oct  1 08:21:06 robin-desktop NetworkManager: <debug info>^I[1191223266.835429] nm_hal_device_added (): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_46d_c025_noserial'). 
Oct  1 08:21:07 robin-desktop NetworkManager: <debug info>^I[1191223267.478414] nm_hal_device_added (): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_46d_c025_noserial_if0'). 
Oct  1 08:21:07 robin-desktop NetworkManager: <debug info>^I[1191223267.590505] nm_hal_device_added (): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_46d_c025_noserial_if0_logicaldev_input'). 
Oct  1 08:21:07 robin-desktop lomoco: 002.009: 046d:c025 MX500 Optical Mouse (M-BP81A) Caps: RES SMS
Oct  1 08:21:07 robin-desktop lomoco: SmartScroll disabled
Oct  1 08:21:07 robin-desktop NetworkManager: <debug info>^I[1191223267.705318] nm_hal_device_added (): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_46d_c025_noserial_usbraw'). 
Oct  1 08:22:44 robin-desktop kernel: [ 1478.454065] Unknown OutputIN= OUT=vmnet8 SRC=172.16.77.1 DST=172.16.77.255 LEN=265 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=138 DPT=138 LEN=245 
Oct  1 08:22:44 robin-desktop kernel: [ 1478.454177] Unknown OutputIN= OUT=vmnet1 SRC=192.168.208.1 DST=192.168.208.255 LEN=265 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=138 DPT=138 LEN=245 
Oct  1 08:23:15 robin-desktop kernel: [ 1509.230401] usb 2-6: USB disconnect, address 9
Oct  1 08:23:15 robin-desktop NetworkManager: <debug info>^I[1191223395.628978] nm_hal_device_removed (): Device removed (hal udi is '/org/freedesktop/Hal/devices/usb_device_46d_c025_noserial_if0_logicaldev_input'). 
Oct  1 08:23:15 robin-desktop NetworkManager: <debug info>^I[1191223395.631769] nm_hal_device_removed (): Device removed (hal udi is '/org/freedesktop/Hal/devices/usb_device_46d_c025_noserial_if0'). 
Oct  1 08:23:15 robin-desktop NetworkManager: <debug info>^I[1191223395.635897] nm_hal_device_removed (): Device removed (hal udi is '/org/freedesktop/Hal/devices/usb_device_46d_c025_noserial_usbraw'). 
Oct  1 08:23:15 robin-desktop NetworkManager: <debug info>^I[1191223395.640488] nm_hal_device_removed (): Device removed (hal udi is '/org/freedesktop/Hal/devices/usb_device_46d_c025_noserial'). 
Oct  1 08:23:16 robin-desktop kernel: [ 1509.883622] usb 2-6: new low speed USB device using ohci_hcd and address 10
Oct  1 08:23:16 robin-desktop kernel: [ 1510.095175] usb 2-6: configuration #1 chosen from 1 choice
Oct  1 08:23:16 robin-desktop NetworkManager: <debug info>^I[1191223396.482835] nm_hal_device_added (): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_46d_c025_noserial'). 
Oct  1 08:23:16 robin-desktop kernel: [ 1510.106164] input: B16_b_02 USB-PS/2 Optical Mouse as /class/input/input9
Oct  1 08:23:16 robin-desktop kernel: [ 1510.106231] input: USB HID v1.10 Mouse [B16_b_02 USB-PS/2 Optical Mouse] on usb-0000:00:0b.0-6
Oct  1 08:23:16 robin-desktop NetworkManager: <debug info>^I[1191223396.564573] nm_hal_device_added (): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_46d_c025_noserial_if0'). 
Oct  1 08:23:16 robin-desktop NetworkManager: <debug info>^I[1191223396.664437] nm_hal_device_added (): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_46d_c025_noserial_if0_logicaldev_input'). 
Oct  1 08:23:16 robin-desktop lomoco: 002.010: 046d:c025 MX500 Optical Mouse (M-BP81A) Caps: RES SMS
Oct  1 08:23:16 robin-desktop lomoco: SmartScroll disabled
Oct  1 08:23:16 robin-desktop NetworkManager: <debug info>^I[1191223396.788135] nm_hal_device_added (): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_46d_c025_noserial_usbraw'). 
Oct  1 08:24:31 robin-desktop kernel: [ 1585.151459] usb 2-6: USB disconnect, address 10
Oct  1 08:24:31 robin-desktop NetworkManager: <debug info>^I[1191223471.737270] nm_hal_device_removed (): Device removed (hal udi is '/org/freedesktop/Hal/devices/usb_device_46d_c025_noserial_if0_logicaldev_input'). 
Oct  1 08:24:31 robin-desktop NetworkManager: <debug info>^I[1191223471.738576] nm_hal_device_removed (): Device removed (hal udi is '/org/freedesktop/Hal/devices/usb_device_46d_c025_noserial_if0'). 
Oct  1 08:24:31 robin-desktop NetworkManager: <debug info>^I[1191223471.744201] nm_hal_device_removed (): Device removed (hal udi is '/org/freedesktop/Hal/devices/usb_device_46d_c025_noserial'). 
Oct  1 08:24:31 robin-desktop NetworkManager: <debug info>^I[1191223471.747020] nm_hal_device_removed (): Device removed (hal udi is '/org/freedesktop/Hal/devices/usb_device_46d_c025_noserial_usbraw'). 
Oct  1 08:24:32 robin-desktop kernel: [ 1585.804695] usb 2-6: new low speed USB device using ohci_hcd and address 11
Oct  1 08:24:32 robin-desktop kernel: [ 1586.018247] usb 2-6: configuration #1 chosen from 1 choice
Oct  1 08:24:32 robin-desktop NetworkManager: <debug info>^I[1191223472.600260] nm_hal_device_added (): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_46d_c025_noserial'). 
Oct  1 08:24:32 robin-desktop kernel: [ 1586.026235] input: B16_b_02 USB-PS/2 Optical Mouse as /class/input/input10
Oct  1 08:24:32 robin-desktop kernel: [ 1586.026300] input: USB HID v1.10 Mouse [B16_b_02 USB-PS/2 Optical Mouse] on usb-0000:00:0b.0-6
Oct  1 08:24:32 robin-desktop NetworkManager: <debug info>^I[1191223472.680258] nm_hal_device_added (): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_46d_c025_noserial_if0'). 
Oct  1 08:24:32 robin-desktop NetworkManager: <debug info>^I[1191223472.780824] nm_hal_device_added (): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_46d_c025_noserial_if0_logicaldev_input'). 
Oct  1 08:24:32 robin-desktop lomoco: 002.011: 046d:c025 MX500 Optical Mouse (M-BP81A) Caps: RES SMS
Oct  1 08:24:32 robin-desktop lomoco: SmartScroll disabled
Oct  1 08:24:32 robin-desktop NetworkManager: <debug info>^I[1191223472.896100] nm_hal_device_added (): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_46d_c025_noserial_usbraw'). 
Oct  1 08:24:34 robin-desktop kernel: [ 1588.190538] Unknown OutputIN= OUT=vmnet8 SRC=172.16.77.1 DST=172.16.77.255 LEN=78 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=137 DPT=137 LEN=58 
Oct  1 08:24:34 robin-desktop kernel: [ 1588.190687] Unknown OutputIN= OUT=vmnet1 SRC=192.168.208.1 DST=192.168.208.255 LEN=78 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=137 DPT=137 LEN=58 
Oct  1 08:24:53 robin-desktop kernel: [ 1607.086214] Inbound IN=eth1 OUT= MAC=00:19:db:4c:ef:fd:00:14:7f:25:9c:b7:08:00 SRC=82.2.230.166 DST=192.168.1.201 LEN=91 TOS=0x00 PREC=0x00 TTL=120 ID=5070 PROTO=UDP SPT=44162 DPT=58345 LEN=71 
Oct  1 08:26:04 robin-desktop kernel: [ 1676.539047] usb 2-6: USB disconnect, address 11
Oct  1 08:26:04 robin-desktop kernel: [ 1677.193241] usb 2-6: new low speed USB device using ohci_hcd and address 12
Oct  1 08:26:04 robin-desktop kernel: [ 1677.407793] usb 2-6: configuration #1 chosen from 1 choice
Oct  1 08:26:04 robin-desktop kernel: [ 1677.418774] input: B16_b_02 USB-PS/2 Optical Mouse as /class/input/input11
Oct  1 08:26:04 robin-desktop kernel: [ 1677.418836] input: USB HID v1.10 Mouse [B16_b_02 USB-PS/2 Optical Mouse] on usb-0000:00:0b.0-6
Oct  1 08:26:04 robin-desktop NetworkManager: <debug info>^I[1191223564.697821] nm_hal_device_removed (): Device removed (hal udi is '/org/freedesktop/Hal/devices/usb_device_46d_c025_noserial_if0_logicaldev_input'). 
Oct  1 08:26:04 robin-desktop NetworkManager: <debug info>^I[1191223564.700349] nm_hal_device_removed (): Device removed (hal udi is '/org/freedesktop/Hal/devices/usb_device_46d_c025_noserial_if0'). 
Oct  1 08:26:09 robin-desktop kernel: [ 1682.251993] Inbound IN=eth1 OUT= MAC=00:19:db:4c:ef:fd:00:14:7f:25:9c:b7:08:00 SRC=82.2.230.166 DST=192.168.1.201 LEN=70 TOS=0x00 PREC=0x00 TTL=120 ID=8270 PROTO=UDP SPT=44162 DPT=58345 LEN=50 
Oct  1 08:26:17 robin-desktop NetworkManager: <debug info>^I[1191223577.141670] nm_hal_device_removed (): Device removed (hal udi is '/org/freedesktop/Hal/devices/usb_device_46d_c025_noserial'). 
Oct  1 08:26:17 robin-desktop NetworkManager: <debug info>^I[1191223577.167678] nm_hal_device_added (): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_46d_c025_noserial'). 
Oct  1 08:26:17 robin-desktop NetworkManager: <debug info>^I[1191223577.231707] nm_hal_device_added (): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_46d_c025_noserial_if0'). 
Oct  1 08:26:17 robin-desktop NetworkManager: <debug info>^I[1191223577.348160] nm_hal_device_added (): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_46d_c025_noserial_if0_logicaldev_input'). 
Oct  1 08:26:17 robin-desktop NetworkManager: <debug info>^I[1191223577.475899] nm_hal_device_removed (): Device removed (hal udi is '/org/freedesktop/Hal/devices/usb_device_46d_c025_noserial_usbraw'). 
Oct  1 08:26:17 robin-desktop lomoco: 002.012: 046d:c025 MX500 Optical Mouse (M-BP81A) Caps: RES SMS
Oct  1 08:26:17 robin-desktop lomoco: SmartScroll disabled
Oct  1 08:26:17 robin-desktop NetworkManager: <debug info>^I[1191223577.598527] nm_hal_device_added (): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_46d_c025_noserial_usbraw'). 
Oct  1 08:26:34 robin-desktop kernel: [ 1707.123830] Inbound IN=eth1 OUT= MAC=00:19:db:4c:ef:fd:00:14:7f:25:9c:b7:08:00 SRC=82.2.230.166 DST=192.168.1.201 LEN=70 TOS=0x00 PREC=0x00 TTL=120 ID=9329 PROTO=UDP SPT=44162 DPT=58345 LEN=50 
Oct  1 08:27:17 robin-desktop kernel: [ 1750.306376] Inbound IN=eth1 OUT= MAC=00:19:db:4c:ef:fd:00:14:7f:25:9c:b7:08:00 SRC=82.2.230.166 DST=192.168.1.201 LEN=91 TOS=0x00 PREC=0x00 TTL=120 ID=11057 PROTO=UDP SPT=44162 DPT=58345 LEN=71 
Oct  1 08:29:34 robin-desktop kernel: [ 1887.442459] Unknown OutputIN= OUT=vmnet8 SRC=172.16.77.1 DST=172.16.77.255 LEN=78 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=137 DPT=137 LEN=58 
Oct  1 08:29:34 robin-desktop kernel: [ 1887.442636] Unknown OutputIN= OUT=vmnet1 SRC=192.168.208.1 DST=192.168.208.255 LEN=78 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=137 DPT=137 LEN=58 
Oct  1 08:29:44 robin-desktop kernel: [ 1897.417752] Unknown OutputIN= OUT=vmnet8 SRC=172.16.77.1 DST=172.16.77.255 LEN=265 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=138 DPT=138 LEN=245 
Oct  1 08:29:44 robin-desktop kernel: [ 1897.417846] Unknown OutputIN= OUT=vmnet1 SRC=192.168.208.1 DST=192.168.208.255 LEN=265 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=138 DPT=138 LEN=245 
Oct  1 08:31:38 robin-desktop kernel: [ 2010.461072] usb 2-6: USB disconnect, address 12
Oct  1 08:31:38 robin-desktop NetworkManager: <debug info>^I[1191223898.363745] nm_hal_device_removed (): Device removed (hal udi is '/org/freedesktop/Hal/devices/usb_device_46d_c025_noserial_if0_logicaldev_input'). 
Oct  1 08:31:38 robin-desktop NetworkManager: <debug info>^I[1191223898.365951] nm_hal_device_removed (): Device removed (hal udi is '/org/freedesktop/Hal/devices/usb_device_46d_c025_noserial_if0'). 
Oct  1 08:31:38 robin-desktop kernel: [ 2011.114313] usb 2-6: new low speed USB device using ohci_hcd and address 13
Oct  1 08:31:38 robin-desktop NetworkManager: <debug info>^I[1191223898.778860] nm_hal_device_removed (): Device removed (hal udi is '/org/freedesktop/Hal/devices/usb_device_46d_c025_noserial_usbraw'). 
Oct  1 08:31:38 robin-desktop NetworkManager: <debug info>^I[1191223898.784102] nm_hal_device_removed (): Device removed (hal udi is '/org/freedesktop/Hal/devices/usb_device_46d_c025_noserial'). 
Oct  1 08:31:38 robin-desktop kernel: [ 2011.324855] usb 2-6: configuration #1 chosen from 1 choice
Oct  1 08:31:38 robin-desktop NetworkManager: <debug info>^I[1191223898.997060] nm_hal_device_added (): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_46d_c025_noserial'). 
Oct  1 08:31:39 robin-desktop kernel: [ 2011.335881] input: B16_b_02 USB-PS/2 Optical Mouse as /class/input/input12
Oct  1 08:31:39 robin-desktop kernel: [ 2011.335946] input: USB HID v1.10 Mouse [B16_b_02 USB-PS/2 Optical Mouse] on usb-0000:00:0b.0-6
Oct  1 08:31:39 robin-desktop NetworkManager: <debug info>^I[1191223899.161108] nm_hal_device_added (): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_46d_c025_noserial_if0'). 
Oct  1 08:31:39 robin-desktop NetworkManager: <debug info>^I[1191223899.266488] nm_hal_device_added (): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_46d_c025_noserial_if0_logicaldev_input'). 
Oct  1 08:31:39 robin-desktop lomoco: 002.013: 046d:c025 MX500 Optical Mouse (M-BP81A) Caps: RES SMS
Oct  1 08:31:39 robin-desktop lomoco: SmartScroll disabled
Oct  1 08:31:39 robin-desktop NetworkManager: <debug info>^I[1191223899.397214] nm_hal_device_added (): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_46d_c025_noserial_usbraw'). 
```

Robin

---

### Post by geraldm on 2007-10-01
The log shows connecting as different device numbers from 6 to 12 over 12 minutes.
That is often enough! 
Perhaps a power-saving feature in a kernel such as CONFIG_USB_SUSPEND=y ?
Otherwise I would suggest checking for other threads with this same mouse MX500
to see if they were able to resolve any problem.

Gerald

---

