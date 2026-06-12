---
title: "Bluetooth only works after booting first in Windows"
date: 2018-06-30
forum: General Help
---

### Post by seriouslysupersonic on 2018-06-30
Hello everyone,

I'll start by noting that I am complete Linux beginner, so excuse me any obvious troubleshooting I might have overlooked before posting.

I recently installed Ubuntu 18.04 on a second SSD and I am currently dual booting Windows 10 on my desktop. After the OS installation, Bluetooth worked out of the box, and I could pair my mouse, speakers, etc. However, the second time in a row I booted into Ubuntu, the Bluetooth icon in the system tray started flickering and all my devices stopped working.
I booted back into Windows to check if Bluetooth still worked fine, and it did. Then, I went back into Ubuntu to dig further into the issue and, for my surprise, everything was working again. This problem happens repeatedly every 1,2 or 3 times I boot back into Ubuntu and it can be fixed by just booting into Windows.

I tried to use the manufacturer drivers for my wireless card in Software & Updates > Additional Drivers (using Broadcom 802.11 Linux STA wireless driver from bcmwl-kernel-source), but the issue remains. I am truly puzzled by this, so any help is greatly welcomed.

If it helps, ```
lshw -class network
``` retrieves

```

       description: Wireless interface
       product: BCM4352 802.11ac Wireless Network Adapter
       vendor: Broadcom Limited
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wlp3s0
       version: 03
       serial: 24:0a:64:49:78:65
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=wl0 driverversion=6.30.223.271 (r587334) latency=0 multicast=yes wireless=IEEE 802.11
       resources: irq:17 memory:df400000-df407fff memory:df200000-df3fffff

```

Btw, sorry for my English.

---

### Post by jeremy31 on 2018-06-30
What is the results for ```
lsusb; dmesg | egrep -i 'blue|firm'
```

---

### Post by seriouslysupersonic on 2018-06-30
This is it:

```

Bus 002 Device 002: ID 8087:8000 Intel Corp. Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 8087:8008 Intel Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 003: ID 0480:0110 Toshiba America Inc 
Bus 004 Device 002: ID 174c:3074 ASMedia Technology Inc. ASM1074 SuperSpeed hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 005: ID 1b1c:0c04 Corsair 
Bus 003 Device 003: ID 0b05:17cf ASUSTek Computer, Inc. 
Bus 003 Device 006: ID 04b4:0101 Cypress Semiconductor Corp. Keyboard/Hub
Bus 003 Device 004: ID 0738:1705 Mad Catz, Inc. 
Bus 003 Device 002: ID 174c:2074 ASMedia Technology Inc. ASM1074 High-Speed hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
[    0.032076] Spectre V2 : Enabling Restricted Speculation for firmware calls
[    0.057619] ACPI: [Firmware Bug]: BIOS _OSI(Linux) query ignored
[    3.349413] Bluetooth: Core ver 2.22
[    3.349441] Bluetooth: HCI device and connection manager initialized
[    3.349445] Bluetooth: HCI socket layer initialized
[    3.349448] Bluetooth: L2CAP socket layer initialized
[    3.349453] Bluetooth: SCO socket layer initialized
[    3.469459] Bluetooth: hci0: BCM: chip id 63
[    3.470452] Bluetooth: hci0: BCM: features 0x07
[    3.486477] Bluetooth: hci0: NUNO
[    3.487455] Bluetooth: hci0: BCM20702A1 (001.002.014) build 1469
[    3.487864] bluetooth hci0: Direct firmware load for brcm/BCM20702A1-0b05-17cf.hcd failed with error -2
[    3.487865] Bluetooth: hci0: BCM: Patch brcm/BCM20702A1-0b05-17cf.hcd not found
[    4.569598] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[    4.569599] Bluetooth: BNEP filters: protocol multicast
[    4.569602] Bluetooth: BNEP socket layer initialized
[   34.098347] hid-generic 0005:046D:B01A.0005: input,hidraw4: BLUETOOTH HID v0.03 Keyboard [MX Anywhere 2S] on 24:0A:64:39:1A:79
[   50.855727] Bluetooth: RFCOMM TTY layer initialized
[   50.855731] Bluetooth: RFCOMM socket layer initialized
[   50.855734] Bluetooth: RFCOMM ver 1.11
[  498.150022] Bluetooth: hci0: last event is not cmd complete (0x0f)
[  514.274031] Bluetooth: hci0: last event is not cmd complete (0x0f)
[  530.146048] Bluetooth: hci0: last event is not cmd complete (0x0f)
[  546.275062] Bluetooth: hci0: last event is not cmd complete (0x0f)
[  562.148084] Bluetooth: hci0: last event is not cmd complete (0x0f)
[  578.275123] Bluetooth: hci0: last event is not cmd complete (0x0f)
[  594.146111] Bluetooth: hci0: last event is not cmd complete (0x0f)
[  610.275142] Bluetooth: hci0: last event is not cmd complete (0x0f)
[  626.147190] Bluetooth: hci0: last event is not cmd complete (0x0f)
[  642.274167] Bluetooth: hci0: last event is not cmd complete (0x0f)
[  658.148195] Bluetooth: hci0: last event is not cmd complete (0x0f)
[  674.276200] Bluetooth: hci0: last event is not cmd complete (0x0f)
[  690.146230] Bluetooth: hci0: last event is not cmd complete (0x0f)
[  706.275248] Bluetooth: hci0: last event is not cmd complete (0x0f)
[  722.148287] Bluetooth: hci0: last event is not cmd complete (0x0f)
[  738.275305] Bluetooth: hci0: last event is not cmd complete (0x0f)
[  754.146318] Bluetooth: hci0: last event is not cmd complete (0x0f)
[  770.276304] Bluetooth: hci0: last event is not cmd complete (0x0f)
[  786.147363] Bluetooth: hci0: last event is not cmd complete (0x0f)
[  802.274371] Bluetooth: hci0: last event is not cmd complete (0x0f)
[  818.148378] Bluetooth: hci0: last event is not cmd complete (0x0f)
[  834.276393] Bluetooth: hci0: last event is not cmd complete (0x0f)
[  850.146415] Bluetooth: hci0: last event is not cmd complete (0x0f)
[  866.277421] Bluetooth: hci0: last event is not cmd complete (0x0f)
[  882.148466] Bluetooth: hci0: last event is not cmd complete (0x0f)
[  898.275464] Bluetooth: hci0: last event is not cmd complete (0x0f)
[  914.146472] Bluetooth: hci0: last event is not cmd complete (0x0f)
[  930.276500] Bluetooth: hci0: last event is not cmd complete (0x0f)
[  946.147538] Bluetooth: hci0: last event is not cmd complete (0x0f)
[  962.274558] Bluetooth: hci0: last event is not cmd complete (0x0f)
[  978.148574] Bluetooth: hci0: last event is not cmd complete (0x0f)
[  994.276589] Bluetooth: hci0: last event is not cmd complete (0x0f)
[ 1010.146603] Bluetooth: hci0: last event is not cmd complete (0x0f)
[ 1026.275605] Bluetooth: hci0: last event is not cmd complete (0x0f)
[ 1042.148647] Bluetooth: hci0: last event is not cmd complete (0x0f)
[ 1058.275635] Bluetooth: hci0: last event is not cmd complete (0x0f)
[ 1074.147645] Bluetooth: hci0: last event is not cmd complete (0x0f)
[ 1090.276688] Bluetooth: hci0: last event is not cmd complete (0x0f)
[ 1106.149679] Bluetooth: hci0: last event is not cmd complete (0x0f)
[ 1122.275736] Bluetooth: hci0: last event is not cmd complete (0x0f)
[ 1138.148706] Bluetooth: hci0: last event is not cmd complete (0x0f)
[ 1154.277741] Bluetooth: hci0: last event is not cmd complete (0x0f)
[ 1170.148737] Bluetooth: hci0: last event is not cmd complete (0x0f)
[ 1186.277777] Bluetooth: hci0: last event is not cmd complete (0x0f)
[ 1202.149801] Bluetooth: hci0: last event is not cmd complete (0x0f)
[ 1218.276792] Bluetooth: hci0: last event is not cmd complete (0x0f)
[ 1234.150819] Bluetooth: hci0: last event is not cmd complete (0x0f)
[ 1250.278866] Bluetooth: hci0: last event is not cmd complete (0x0f)
[ 1266.149857] Bluetooth: hci0: last event is not cmd complete (0x0f)
[ 1282.276905] Bluetooth: hci0: last event is not cmd complete (0x0f)
[ 1303.270901] Bluetooth: hci0: last event is not cmd complete (0x0f)
[ 1326.311949] Bluetooth: hci0: last event is not cmd complete (0x0f)
[ 1355.239962] Bluetooth: hci0: last event is not cmd complete (0x0f)
[ 1374.183996] Bluetooth: hci0: last event is not cmd complete (0x0f)
[ 1393.383004] Bluetooth: hci0: last event is not cmd complete (0x0f)
[ 1409.255045] Bluetooth: hci0: last event is not cmd complete (0x0f)
[ 1425.387076] Bluetooth: hci0: last event is not cmd complete (0x0f)
[ 1441.258073] Bluetooth: hci0: last event is not cmd complete (0x0f)

```

---

### Post by jeremy31 on 2018-06-30
Try
```
wget https://www.dropbox.com/s/9yfcg4e2mn1zcs0/fw-0b05-17cf.hcd
sudo cp fw-0b05-17cf.hcd /lib/firmware/brcm/BCM20702A1-0b05-17cf.hcd
```
Shut down and boot into Ubuntu

---

### Post by seriouslysupersonic on 2018-06-30
Unfortunately wget cannot find the file:

```

--2018-06-30 12:49:08--  https://www.dropbox.com/s/9yfcg4e2mn1zcs0/fw-0b05-17cf.hcd
Resolving www.dropbox.com (www.dropbox.com)... 162.125.68.1, 2620:100:6024:1::a27d:4401
Connecting to www.dropbox.com (www.dropbox.com)|162.125.68.1|:443... connected.
HTTP request sent, awaiting response... 302 Found
Location: /s/raw/9yfcg4e2mn1zcs0/fw-0b05-17cf.hcd [following]
--2018-06-30 12:49:09--  https://www.dropbox.com/s/raw/9yfcg4e2mn1zcs0/fw-0b05-17cf.hcd
Reusing existing connection to www.dropbox.com:443.
HTTP request sent, awaiting response... 404 Not Found
2018-06-30 12:49:09 ERROR 404: Not Found.

```

---

### Post by jeremy31 on 2018-06-30
Try ```
wget https://github.com/winterheart/broadcom-bt-firmware/raw/master/brcm/BCM20702A1-0b05-17cf.hcd
sudo cp BCM20702A1-0b05-17cf.hcd /lib/firmware/brcm/
```
Shut down and boot

---

### Post by seriouslysupersonic on 2018-07-01
This time it took a little longer for the Bluetooth to stop working, but it eventually happened again today.
I am very pleased to confirm that on the next boot after installing the recommended firmware, Bluetooth started working again without having to boot first into Windows.

Thank you! :p

---

