---
title: "Bluetooth system freeze"
date: 2008-05-02
forum: General Help
---

### Post by fiftyMIPsparc on 2008-05-02
When pairing a bluetooth device (mobile phone), the system completely locks up. This happens after entering the device passcode and I get the GNOME bubble stating that pairing was successful. The system is completely unresponsive, however my caps lock light starts flashing. :confused:

Tried it three times, all three times it behaved the same way. Computer is an IBM T43.

Computer locked up at 15:19:18 (I know this because the clock froze :) ) Here's whats in the logs immediately before lockup:

daemon.log
```
May  2 15:14:27 T43 NetworkManager: <debug> [1209755667.323234] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_3f0_4117_KP14AA4_if0_printer_noserial'). 
May  2 15:15:35 T43 input[5807]: /org/bluez/input: org.bluez.input.Manager.ListDevices()
May  2 15:15:35 T43 audio[5817]: /org/bluez/audio: org.bluez.audio.Manager.ListDevices()
May  2 15:19:07 T43 NetworkManager: <debug> [1209755947.578218] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/bluetooth_acl_1c1226c03c'). 
May  2 15:19:15 T43 NetworkManager: <debug> [1209755955.333825] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/bluetooth_acl_1c1226c03c'). 
```

debug
```
May  2 15:14:27 T43 NetworkManager: <debug> [1209755667.323234] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_3f0_4117_KP14AA4_if0_printer_noserial'). 
May  2 15:15:35 T43 input[5807]: /org/bluez/input: org.bluez.input.Manager.ListDevices()
May  2 15:15:35 T43 audio[5817]: /org/bluez/audio: org.bluez.audio.Manager.ListDevices()
May  2 15:19:07 T43 NetworkManager: <debug> [1209755947.578218] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/bluetooth_acl_1c1226c03c'). 
May  2 15:19:15 T43 NetworkManager: <debug> [1209755955.333825] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/bluetooth_acl_1c1226c03c'). 
```

syslog
```
May  2 15:19:07 T43 NetworkManager: <debug> [1209755947.578218] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/bluetooth_acl_1c1226c03c'). 
May  2 15:19:07 T43 hcid[5798]: pin_code_request (sba=00:0E:9B:DD:DF:D4, dba=00:1C:12:26:C0:3C)
May  2 15:19:15 T43 hcid[5798]: link_key_notify (sba=00:0E:9B:DD:DF:D4, dba=00:1C:12:26:C0:3C)
May  2 15:19:15 T43 NetworkManager: <debug> [1209755955.333825] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/bluetooth_acl_1c1226c03c'). 
```

Anybody have any ideas?

---

### Post by etaham on 2008-05-06
I'm having the same problem. I'm using a zonet adapter on my pc.

---

### Post by fiftyMIPsparc on 2008-05-14
Also, I forgot to mention that it's the IBM integrated bluetooth... so apparently it's not specific to just my hardware...

---

### Post by michaelaly on 2008-06-06
bump,
  I'm using a Kensington bluetooth adapter and have the same issue, total freeze up after I connect to the device(mobile phone). I'm at a loss and haven't had much luck searching the forums. Any ideas?

---

### Post by michaelaly on 2008-06-07
[Solved] I installed Blueman per these instructions : [http://ubuntuforums.org/showthread.php?t=559089](http://ubuntuforums.org/showthread.php?t=559089)

No more locking up, and my phone is now fully accessible as it should be.

---

