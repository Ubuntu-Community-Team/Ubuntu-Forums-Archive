---
title: "Logitech  C270 usb webcam recognised in lsusb but not in software"
date: 2018-05-06
forum: General Help
---

### Post by z7APXKm on 2018-05-06
Hi,

Ubuntu 16.04 LTS, with a logitech usb c270 webcam attached.  Cheese / skype etc. don't see it, but it is present in lsusb:

```
# lsusb
Bus 002 Device 005: ID 046d:0825 Logitech, Inc. Webcam C270
Bus 002 Device 004: ID 1058:1001 Western Digital Technologies, Inc. Elements Desktop (WDE1U)
Bus 002 Device 003: ID 20e8:5861
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 005: ID 05e3:0608 Genesys Logic, Inc. Hub
Bus 001 Device 004: ID 05e3:070e Genesys Logic, Inc. USB 2.0 Card Reader
Bus 001 Device 003: ID 15c2:0036 SoundGraph Inc. LC16M VFD Display/IR Receiver
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
```

I've tried unplugging and plugging into a different usb port.  Can anyone suggest how to get it working?

thanks

---

### Post by z7APXKm on 2018-05-06
Saw this on another thread, unplugged and replugged in then dmesg:

```

[    4.866079] uvcvideo: Failed to query (GET_MIN) UVC control 3 on unit 1: -32 (exp. 1).
[    4.868888] uvcvideo: Failed to query (GET_MIN) UVC control 3 on unit 1: -32 (exp. 1).
[    4.871878] uvcvideo: Failed to query (GET_MIN) UVC control 3 on unit 1: -32 (exp. 1).
[    4.874632] uvcvideo: Failed to query (GET_MIN) UVC control 3 on unit 1: -32 (exp. 1).
[    4.877386] uvcvideo: Failed to query (GET_MIN) UVC control 3 on unit 1: -32 (exp. 1).
[    4.890496] uvcvideo: Failed to query (GET_MIN) UVC control 3 on unit 1: -32 (exp. 1).
[    4.893641] uvcvideo: Failed to query (GET_MIN) UVC control 3 on unit 1: -32 (exp. 1).
[    4.896265] uvcvideo: Failed to query (GET_MIN) UVC control 3 on unit 1: -32 (exp. 1).
[    4.899284] uvcvideo: Failed to query (GET_MIN) UVC control 3 on unit 1: -32 (exp. 1).
[    4.902576] uvcvideo: Failed to query (GET_MIN) UVC control 3 on unit 1: -32 (exp. 1).
[    4.905640] uvcvideo: Failed to query (GET_MIN) UVC control 3 on unit 1: -32 (exp. 1).
[    5.248708] IPv6: ADDRCONF(NETDEV_UP): enp3s0: link is not ready
[    5.352700] r8169 0000:03:00.0 enp3s0: link down
[    5.352785] IPv6: ADDRCONF(NETDEV_UP): enp3s0: link is not ready
[    5.353048] r8169 0000:03:00.0 enp3s0: link down
[    6.098080] ip_tables: (C) 2000-2006 Netfilter Core Team
[    7.352653] r8169 0000:03:00.0 enp3s0: link up
[    7.352660] IPv6: ADDRCONF(NETDEV_CHANGE): enp3s0: link becomes ready
[   11.272050] usb 2-1.7: reset high-speed USB device number 5 using ehci-pci
[   53.839664] uvcvideo: Failed to query (GET_MIN) UVC control 3 on unit 1: -32 (exp. 1).
[   55.825949] uvcvideo: Failed to query (GET_MIN) UVC control 3 on unit 1: -32 (exp. 1).
[   57.773452] uvcvideo: Failed to query (GET_MIN) UVC control 3 on unit 1: -32 (exp. 1).
[ 3819.400661] usb 2-1.7: USB disconnect, device number 5
[ 3842.407551] usb 2-1.7: new high-speed USB device number 6 using ehci-pci
[ 3842.732433] usb 2-1.7: New USB device found, idVendor=046d, idProduct=0825
[ 3842.732438] usb 2-1.7: New USB device strings: Mfr=0, Product=0, SerialNumber=2
[ 3842.732440] usb 2-1.7: SerialNumber: 7CD77CA0
[ 3842.732880] uvcvideo: Found UVC 1.00 device <unnamed> (046d:0825)
[ 3842.852737] uvcvideo 2-1.7:1.0: Entity type for entity Extension 4 was not initialized!
[ 3842.852741] uvcvideo 2-1.7:1.0: Entity type for entity Extension 6 was not initialized!
[ 3842.852743] uvcvideo 2-1.7:1.0: Entity type for entity Extension 7 was not initialized!
[ 3842.852745] uvcvideo 2-1.7:1.0: Entity type for entity Processing 2 was not initialized!
[ 3842.852747] uvcvideo 2-1.7:1.0: Entity type for entity Extension 3 was not initialized!
[ 3842.852749] uvcvideo 2-1.7:1.0: Entity type for entity Camera 1 was not initialized!
[ 3842.852861] input: UVC Camera (046d:0825) as /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.7/2-1.7:1.0/input/input21
[ 3844.014431] usb 2-1.7: set resolution quirk: cval->res = 384
[ 3844.157411] uvcvideo: Failed to query (GET_MIN) UVC control 3 on unit 1: -32 (exp. 1).
[ 3844.160163] uvcvideo: Failed to query (GET_MIN) UVC control 3 on unit 1: -32 (exp. 1).
[ 3844.162892] uvcvideo: Failed to query (GET_MIN) UVC control 3 on unit 1: -32 (exp. 1).
[ 3844.165650] uvcvideo: Failed to query (GET_MIN) UVC control 3 on unit 1: -32 (exp. 1).
[ 3844.168401] uvcvideo: Failed to query (GET_MIN) UVC control 3 on unit 1: -32 (exp. 1).
[ 3844.171152] uvcvideo: Failed to query (GET_MIN) UVC control 3 on unit 1: -32 (exp. 1).
[ 3844.174026] uvcvideo: Failed to query (GET_MIN) UVC control 3 on unit 1: -32 (exp. 1).
[ 3844.177026] uvcvideo: Failed to query (GET_MIN) UVC control 3 on unit 1: -32 (exp. 1).
[ 3844.179905] uvcvideo: Failed to query (GET_MIN) UVC control 3 on unit 1: -32 (exp. 1).
[ 3844.182777] uvcvideo: Failed to query (GET_MIN) UVC control 3 on unit 1: -32 (exp. 1).
[ 3844.185517] uvcvideo: Failed to query (GET_MIN) UVC control 3 on unit 1: -32 (exp. 1).
[ 3844.188400] uvcvideo: Failed to query (GET_MIN) UVC control 3 on unit 1: -32 (exp. 1).
[ 3844.191277] uvcvideo: Failed to query (GET_MIN) UVC control 3 on unit 1: -32 (exp. 1).
[ 3844.194145] uvcvideo: Failed to query (GET_MIN) UVC control 3 on unit 1: -32 (exp. 1).

# uname -a
Linux myth 4.13.0-38-generic #43~16.04.1-Ubuntu SMP Wed Mar 14 17:48:43 UTC 2018 x86_64 x86_64 x86_64 GNU/Linux

```

---

### Post by z7APXKm on 2018-05-09
Complete dmesg here:
[https://pastebin.com/SFuWqqHc](https://pastebin.com/SFuWqqHc)

---

### Post by z7APXKm on 2018-05-15
OK, I figured it out. C270 usb webcam is actually plug and play, but my sources.list file was messed up, meaning I needed to rebuild it, apt-get upgrade && apt-get update and reboot.

---

### Post by z7APXKm on 2018-05-15
I know I'm talking to myself again, but It worked for all of half an hour, then I reinstalled the open source driver for my TBS6280 freeview tuner card.  Now I'm back to square one. Any ideas?

---

