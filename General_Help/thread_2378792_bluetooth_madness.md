---
title: "bluetooth madness"
date: 2017-11-27
forum: General Help
---

### Post by The musmula on 2017-11-27
Recently my laptop decides to disable bluetooth at random times. The funny thing is that I can't just turn it back on, instead I get this error message: [https://imgur.com/a/jsM5d](https://imgur.com/a/jsM5d)
When I restart my laptop, everything works fine again.

Running Ubuntu Gnome 16.04.3 on a Dell xps 15 9560

Just did a restart, bluetooth is still not functional. Great

Output of my bluetooth service status:
```


bluetooth.service - Bluetooth service
   Loaded: loaded (/lib/systemd/system/bluetooth.service; disabled; vendor preset: enabled)
   Active: active (running) since Mon 2017-11-27 13:47:26 CET; 4min 4s ago
     Docs: man:bluetoothd(8)
 Main PID: 1092 (bluetoothd)
   Status: "Running"
    Tasks: 1
   Memory: 2.5M
      CPU: 9ms
   CGroup: /system.slice/bluetooth.service
           &#9492;&#9472;1092 /usr/lib/bluetooth/bluetoothd


Nov 27 13:47:26 hal-9000 systemd[1]: Starting Bluetooth service...
Nov 27 13:47:26 hal-9000 bluetoothd[1092]: Bluetooth daemon 5.37
Nov 27 13:47:26 hal-9000 bluetoothd[1092]: Starting SDP server
Nov 27 13:47:26 hal-9000 systemd[1]: Started Bluetooth service.
Nov 27 13:47:26 hal-9000 bluetoothd[1092]: Bluetooth management interface 1.14 initialized
Nov 27 13:51:19 hal-9000 systemd[1]: Started Bluetooth service.


```

Crazy, did another restart, now everything is fine. welp

---

### Post by Kirk Schnable on 2017-12-02
Maybe the device is failing or there's a problem with the driver for your particular model of device.... A few things you could keep an eye on:

- See if you can see the device in "lsusb" (this is a terminal command you can run to list your USB devices that are connected), that's most likely where it will show up as it's probably a USB device even if it's internal, unless it's built in to your WiFi card chipset possibly.
- If you can see it on lsusb now, see if it disappears when you notice the failure.
- Check /var/log/syslog when these incidents occur and see if you see any bluetooth related errors, segfaults, etc.

This may yield some more clues to what is going on.

---

