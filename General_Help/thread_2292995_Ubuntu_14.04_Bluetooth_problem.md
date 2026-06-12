---
title: "Ubuntu 14.04 Bluetooth problem"
date: 2015-09-01
forum: General Help
---

### Post by gonzalo17 on 2015-09-01
Hi everyone :D.
I recently buy a notebook (lenovo b50 70) and was supposed to have bluetooth but until now I can't make it work. I also installed windows 7 and can't make it work there neither, so I'm suspecting that the notebook doesn't have bluetooth at all, but I want to be sure.
I already installed firmware with *apt-get install linux-firmware* and [I]apt-get install linux-firmware-nonfree
[/I]I can see the bluetooth icon in the top bar and activate it, but doesn't find any device.

These are the outputs of some commands that I think they can be useful:

rfkill list
```
0: ideapad_wlan: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: ideapad_bluetooth: Bluetooth
    Soft blocked: no
    Hard blocked: no
2: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no
3: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
4: brcmwl-0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
```

lsusb
```

Bus 001 Device 002: ID 8087:8000 Intel Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 002 Device 005: ID 138a:0011 Validity Sensors, Inc. VFS5011 Fingerprint Reader
Bus 002 Device 004: ID 105b:e065  
Bus 002 Device 003: ID 0bda:579c Realtek Semiconductor Corp. 
Bus 002 Device 002: ID 046d:c52f Logitech, Inc. Unifying Receiver
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```


dmesg | grep -i blue
```

[   23.432097] Bluetooth: Core ver 2.17
[   23.432109] Bluetooth: HCI device and connection manager initialized
[   23.432114] Bluetooth: HCI socket layer initialized
[   23.432115] Bluetooth: L2CAP socket layer initialized
[   23.432117] Bluetooth: SCO socket layer initialized
[   24.939583] Bluetooth: can't load firmware, may not work correctly
[   25.338504] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   25.338508] Bluetooth: BNEP filters: protocol multicast
[   25.338516] Bluetooth: BNEP socket layer initialized
[   25.347176] Bluetooth: RFCOMM TTY layer initialized
[   25.347187] Bluetooth: RFCOMM socket layer initialized
[   25.347192] Bluetooth: RFCOMM ver 1.11
[   26.945259] Bluetooth: hci0 command 0x1003 tx timeout

```


In the last command this linecaught my attention:

[   24.939583] Bluetooth:[B] can't load firmware, may not work correctly

[/B]but I tried to find a solution on the internet and I couldn't**,** andI'm just a beginner with linux.

---

