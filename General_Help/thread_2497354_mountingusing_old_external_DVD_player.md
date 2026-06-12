---
title: "mounting/using old external DVD player"
date: 2024-05-02
forum: General Help
---

### Post by JamButty on 2024-05-02
My desktop DVD/CD player developed delirium tremens and would not stop opening and closing so I had to just unplugit from the board.
Which led me to an old external player, a Samsung SE-208, I still have. When the system would not recognize it I went looking for answers but the little material I found is 13-15 years old so I am hoping something more current is known out there. One of those ancient refs suggested determining how the system sees it via
```
lsusb
dmesg | tail
ls /dev/sr*
```
then mounting with proper dev e.g.
```
udisks --mount /dev/sr0
```

but udisks command is not found and DMESG gives
"dmesg: read kernel buffer failed: Operation not permitted"

here full output I got from those first three
```
lsusb
Bus 002 Device 002: ID 8087:8000 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 8087:8008 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 002: ID 0bc2:231a Seagate RSS LLC Expansion Portable
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 005: ID 0bda:0158 Realtek Semiconductor Corp. USB 2.0 multicard reader
Bus 003 Device 041: ID 0e8d:1806 MediaTek Inc. Samsung SE-208 Slim Portable DVD Writer
Bus 003 Device 004: ID 046d:c52b Logitech, Inc. Unifying Receiver
Bus 003 Device 003: ID 0424:2412 Microchip Technology, Inc. (formerly SMSC) 
Bus 003 Device 007: ID 0cf3:0036 Qualcomm Atheros Communications AR9462 Bluetooth
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
fred@fred-Inspiron-3847:~$ dmesg | tail
dmesg: read kernel buffer failed: Operation not permitted
fred@fred-Inspiron-3847:~$ ls /dev/sr*
/dev/sr0

```

thanks.

---

### Post by ubfan1 on 2024-05-02
Use sudo dmesg  to read those messages. See if the output of df includes the device automamtically mounted.

---

### Post by Holger_Gehrke on 2024-05-02
udisksctl is the program to request a mount from udisksd, either passing the -p option and an dbus object-path for the drive or the -b option and the name of the block-device-file.

Holger

---

### Post by JamButty on 2024-05-26
After struggling with this for a while and almost, but never quite, succeeding in mounting it, it became clear it was a hardware issue, so I tossed the unit.

---

