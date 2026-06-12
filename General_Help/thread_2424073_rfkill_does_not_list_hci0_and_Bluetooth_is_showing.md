---
title: "rfkill does not list hci0 and Bluetooth is showing no adaptors found"
date: 2019-08-02
forum: General Help
---

### Post by radkrishnan on 2019-08-02
Hello,
My new XPS 13 9380 with ubuntu pre-installed, has problems with bluetooth. Usually rebooting works, but this time the hci0 seems to be disabled completely.
modprobe bluetooth does help in starting the bluetooth and the systemctl shows following result:
```

&#9679; bluetooth.service - Bluetooth service
   Loaded: loaded (/lib/systemd/system/bluetooth.service; enabled; vendor preset
   Active: active (running) since Fri 2019-08-02 21:32:35 EDT; 1min 56s ago
     Docs: man:bluetoothd(8)
 Main PID: 2442 (bluetoothd)
   Status: "Running"
    Tasks: 1 (limit: 4915)
   CGroup: /system.slice/bluetooth.service
           &#9492;&#9472;2442 /usr/lib/bluetooth/bluetoothd


Aug 02 21:32:35 radhakrishnan-XPS-13-9380 systemd[1]: Starting Bluetooth service
Aug 02 21:32:35 radhakrishnan-XPS-13-9380 bluetoothd[2442]: Bluetooth daemon 5.5
Aug 02 21:32:35 radhakrishnan-XPS-13-9380 systemd[1]: Started Bluetooth service.
Aug 02 21:32:35 radhakrishnan-XPS-13-9380 bluetoothd[2442]: Starting SDP server
Aug 02 21:32:35 radhakrishnan-XPS-13-9380 bluetoothd[2442]: Bluetooth management

```

But I cannot connect to any devices as it shows 'no adaptors found'.
hciconfig -a gives no output.
and as stated in title rfkill list all does not show hci0.
```

0: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no

```


Any help would be appreciated. 
Regards.

---

