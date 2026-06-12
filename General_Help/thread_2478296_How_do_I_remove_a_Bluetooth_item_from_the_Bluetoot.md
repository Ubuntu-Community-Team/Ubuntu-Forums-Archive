---
title: "How do I remove a Bluetooth item from the Bluetooth list of devices?"
date: 2022-08-22
forum: General Help
---

### Post by Paddy Landau on 2022-08-22
**Ubuntu 20.04**

When I go to Settings > Bluetooth, it lists all devices that are connected or were connected.

However, it also lists two devices that aren't set up. They are old connections that are no longer needed.

In the attached screenshot, you can see "FitTrack". You can also see "TWS" listed twice, one of them due to a failed connection.

I would like to remove the FitTrack entry and the incorrect TWS entry from the list.

If I select either item with my mouse, Bluetooth attempts to connect, and doesn't give me an option to remove the device.

How do I remove the two unwanted devices from the Bluetooth list, please? I can't find the answers online.

---

### Post by tea for one on 2022-08-22
Via the terminal ```
bluetoothctl
```
Here is a site - hope it is useful.
[https://www.makeuseof.com/manage-bluetooth-linux-with-bluetoothctl/](https://www.makeuseof.com/manage-bluetooth-linux-with-bluetoothctl/)

---

### Post by Paddy Landau on 2022-08-22
That was most helpful, thank you!

I discovered that I could find the Bluetooth MAC addresses by looking in /var/lib/bluetooth. A little detective work showed me which devices were the unwanted ones.

Then, I used your link to figure out that I could remove them with "bluetoothctl remove".

Thank you!

---

### Post by tea for one on 2022-08-22
Alternatively```
bluetoothctl
```
Then ```
devices
```
```
edited@edited:~$ bluetoothctl
Agent registered
[CHG] Controller 38:BA:F8:DE:A3:31 Pairable: yes
[bluetooth]# devices
Device 00:14:41:1D:7B:38 JVC  HA-FX21BT
Device BB:F0:36:57:41:8D Cocoon BeatX
[bluetooth]# exit
edited@edited:~$ 

```

---

### Post by Paddy Landau on 2022-08-23
> **tea for one said:**
> ```
devices
```
Ah! That would have saved me quite some trouble!

Thank you

Unfortunately, "man bluetoothctl" shows nothing of use.

EDIT: Except --help, which I missed. Silly me!

---

