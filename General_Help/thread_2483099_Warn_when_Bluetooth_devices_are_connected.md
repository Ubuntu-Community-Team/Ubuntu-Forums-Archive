---
title: "Warn when Bluetooth devices are connected"
date: 2023-01-20
forum: General Help
---

### Post by meetdilip on 2023-01-20
Hi, I often end up shutting down the PC without disconnecting the Bluetooth devices. Sometimes I disable Bluetooth using the drop-down menu with Bluetooth devices connected. 

Wondering if there is any script possible in Python or otherwise to warn when a Bluetooth device is connected in these 2 cases. I almost corrupted the connection and had to remove and re-add the device to make it work due to this issue.

I am using a Gnome extension based on 

[https://github.com/TheWeirdDev/Bluetooth_Headset_Battery_Level](https://github.com/TheWeirdDev/Bluetooth_Headset_Battery_Level)

to show battery %. 

Just in case it helps.

Thanks.

---

### Post by #&amp;thj^% on 2023-01-20
It can be done, I'll show just a basic start, that you can tweak to your liking:
```
udevadm monitor
monitor will print the received events for:
UDEV - the event which udev sends out after rule processing
KERNEL - the kernel uevent

```
Now I'll start bluetooth:
```
KERNEL[8893.719371] add      /module/bnep (module)
UDEV  [8893.734252] add      /module/bnep (module)

```
A guide to help write rules: [https://linuxconfig.org/tutorial-on-how-to-write-basic-udev-rules-in-linux](https://linuxconfig.org/tutorial-on-how-to-write-basic-udev-rules-in-linux)

---

