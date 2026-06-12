---
title: "Bluetooth not working on Ubuntu 18.04 LTS"
date: 2018-05-06
forum: General Help
---

### Post by kosekihan on 2018-05-06
[COLOR=#111111][FONT=Ubuntu]I want to send files from my phone to my Laptop and vice versa through Bluetooth. But the Bluetooth on my system doesn't work.[/FONT][/COLOR][COLOR=#111111][FONT=Ubuntu]
[/FONT][/COLOR][COLOR=#111111][FONT=Ubuntu]
Output of [/FONT][/COLOR]rfkill list[COLOR=#111111][FONT=Ubuntu] is as follows:[/FONT][/COLOR][COLOR=#111111][FONT=Ubuntu]
[/FONT][/COLOR]

0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: brcmwl-0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
2: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no

[COLOR=#111111][FONT=Ubuntu]Output of [/FONT][/COLOR]dmesg | grep Blues[COLOR=#111111][FONT=Ubuntu] is as follows:[/FONT][/COLOR]






   27.578384] Bluetooth: Core ver 2.22
[   27.578806] Bluetooth: HCI device and connection manager initialized
[   27.578810] Bluetooth: HCI socket layer initialized
[   27.578812] Bluetooth: L2CAP socket layer initialized
[   27.578820] Bluetooth: SCO socket layer initialized
[   27.709567] Bluetooth: hci0: BCM: chip id 70
[   27.710567] Bluetooth: hci0: BCM: features 0x06
[   27.726588] Bluetooth: hci0: han-Linux
[   27.726591] Bluetooth: hci0: BCM (001.001.011) build 0000
[   27.764908] Bluetooth: hci0: BCM: Patch brcm/BCM.hcd not found
[   29.788035] Bluetooth: hci0: command 0x1003 tx timeout
[   33.860933] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   33.860935] Bluetooth: BNEP filters: protocol multicast
[   33.860938] Bluetooth: BNEP socket layer initialized
[   36.316034] Bluetooth: hci0: command 0x1003 tx timeout
[  116.746587] Bluetooth: RFCOMM TTY layer initialized
[  116.746594] Bluetooth: RFCOMM socket layer initialized
[  116.746601] Bluetooth: RFCOMM ver 1.11
[  179.928651] Bluetooth: hci0: last event is not cmd complete (0x0f)
[ 1250.129323] Bluetooth: hci0: command 0x1003 tx timeout
[ 1501.839401] Bluetooth: hci0: last event is not cmd complete (0x0f)



[COLOR=#111111][FONT=Ubuntu]Output of [/FONT][/COLOR]lspci -knn | grep Net -A2; lsusb[COLOR=#111111][FONT=Ubuntu] is as follows:[/FONT][/COLOR]


08:00.0 Network controller [0280]: Broadcom Limited BCM43142 802.11b/g/n [14e4:4365] (rev 01)
    Subsystem: Hewlett-Packard Company BCM43142 802.11b/g/n [103c:2230]
    Kernel driver in use: wl
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 004: ID 0a5c:216c Broadcom Corp. BCM43142A0 Bluetooth Device
Bus 001 Device 003: ID 04f2:b40e Chicony Electronics Co., Ltd HP Truevision HD camera
Bus 001 Device 002: ID 046d:c534 Logitech, Inc. Unifying Receiver
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

AutoEnable=true[FONT=Ubuntu] at  [/FONT]etc/bluetooth/main.conf



[COLOR=#111111][FONT=inherit]I don't know if the drivers were installed or not and I don't know how to check it either.[/FONT][/COLOR]

[COLOR=#111111][FONT=Ubuntu]Any idea what the issue is?


Regards,
Han[/FONT][/COLOR]

---

### Post by verma.suraj on 2018-06-03
> **kosekihan said:**
> [COLOR=#111111][FONT=Ubuntu]I want to send files from my phone to my Laptop and vice versa through Bluetooth. But the Bluetooth on my system doesn't work.[/FONT][/COLOR][COLOR=#111111][FONT=Ubuntu]
[/FONT][/COLOR][COLOR=#111111][FONT=Ubuntu]
Output of [/FONT][/COLOR]rfkill list[COLOR=#111111][FONT=Ubuntu] is as follows:[/FONT][/COLOR][COLOR=#111111][FONT=Ubuntu]
[/FONT][/COLOR]

0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: brcmwl-0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
2: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no

[COLOR=#111111][FONT=Ubuntu]Output of [/FONT][/COLOR]dmesg | grep Blues[COLOR=#111111][FONT=Ubuntu] is as follows:[/FONT][/COLOR]






   27.578384] Bluetooth: Core ver 2.22
[   27.578806] Bluetooth: HCI device and connection manager initialized
[   27.578810] Bluetooth: HCI socket layer initialized
[   27.578812] Bluetooth: L2CAP socket layer initialized
[   27.578820] Bluetooth: SCO socket layer initialized
[   27.709567] Bluetooth: hci0: BCM: chip id 70
[   27.710567] Bluetooth: hci0: BCM: features 0x06
[   27.726588] Bluetooth: hci0: han-Linux
[   27.726591] Bluetooth: hci0: BCM (001.001.011) build 0000
[   27.764908] Bluetooth: hci0: BCM: Patch brcm/BCM.hcd not found
[   29.788035] Bluetooth: hci0: command 0x1003 tx timeout
[   33.860933] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   33.860935] Bluetooth: BNEP filters: protocol multicast
[   33.860938] Bluetooth: BNEP socket layer initialized
[   36.316034] Bluetooth: hci0: command 0x1003 tx timeout
[  116.746587] Bluetooth: RFCOMM TTY layer initialized
[  116.746594] Bluetooth: RFCOMM socket layer initialized
[  116.746601] Bluetooth: RFCOMM ver 1.11
[  179.928651] Bluetooth: hci0: last event is not cmd complete (0x0f)
[ 1250.129323] Bluetooth: hci0: command 0x1003 tx timeout
[ 1501.839401] Bluetooth: hci0: last event is not cmd complete (0x0f)



[COLOR=#111111][FONT=Ubuntu]Output of [/FONT][/COLOR]lspci -knn | grep Net -A2; lsusb[COLOR=#111111][FONT=Ubuntu] is as follows:[/FONT][/COLOR]


08:00.0 Network controller [0280]: Broadcom Limited BCM43142 802.11b/g/n [14e4:4365] (rev 01)
    Subsystem: Hewlett-Packard Company BCM43142 802.11b/g/n [103c:2230]
    Kernel driver in use: wl
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 004: ID 0a5c:216c Broadcom Corp. BCM43142A0 Bluetooth Device
Bus 001 Device 003: ID 04f2:b40e Chicony Electronics Co., Ltd HP Truevision HD camera
Bus 001 Device 002: ID 046d:c534 Logitech, Inc. Unifying Receiver
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

AutoEnable=true[FONT=Ubuntu] at  [/FONT]etc/bluetooth/main.conf



[COLOR=#111111][FONT=inherit]I don't know if the drivers were installed or not and I don't know how to check it either.[/FONT][/COLOR]

[COLOR=#111111][FONT=Ubuntu]Any idea what the issue is?


Regards,
Han[/FONT][/COLOR]

me too having same problem, no luck.

---

### Post by mIk3_08 on 2018-06-03
Try to look at under System settings --> Hardware 

If Bluetooth is present.

---

### Post by Jesbus on 2018-06-20
I think I have the same problem.
In Settings -> Bluetooth, it says "Searching for devices" all the time but it never actually finds anything.
I also get the "Bluetooth: hci0: last event is not cmd complete (0x0f)" message regularly.

:~$ dmesg | grep Blue
[    3.687600] Bluetooth: Core ver 2.22
[    3.687610] Bluetooth: HCI device and connection manager initialized
[    3.687613] Bluetooth: HCI socket layer initialized
[    3.687615] Bluetooth: L2CAP socket layer initialized
[    3.687619] Bluetooth: SCO socket layer initialized
[    5.661412] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[    5.661413] Bluetooth: BNEP filters: protocol multicast
[    5.661416] Bluetooth: BNEP socket layer initialized
[   19.802032] Bluetooth: RFCOMM TTY layer initialized
[   19.802037] Bluetooth: RFCOMM socket layer initialized
[   19.802042] Bluetooth: RFCOMM ver 1.11
[   34.269988] Bluetooth: hci0: last event is not cmd complete (0x0f)
[   46.458050] Bluetooth: hci0: last event is not cmd complete (0x0f)
[   57.508987] Bluetooth: hci0: last event is not cmd complete (0x0f)
[   64.429107] Bluetooth: hci0: last event is not cmd complete (0x0f)
[   81.582986] Bluetooth: hci0: last event is not cmd complete (0x0f)
[   97.456031] Bluetooth: hci0: last event is not cmd complete (0x0f)
[  113.584039] Bluetooth: hci0: last event is not cmd complete (0x0f)
[  129.456044] Bluetooth: hci0: last event is not cmd complete (0x0f)

---

### Post by winston_nolan on 2018-07-11
I have this bug, I am unable to pair any bluetooth device - these devices all pair fine with my android phone

I get the message constantly

Jul 11 19:59:55 win-Dell-Precision-M3800 kernel: [ 1128.122591] Bluetooth: hci0: last event is not cmd complete (0x0f)
Jul 11 20:00:11 win-Dell-Precision-M3800 kernel: [ 1144.249660] Bluetooth: hci0: last event is not cmd complete (0x0f)
Jul 11 20:00:27 win-Dell-Precision-M3800 kernel: [ 1160.121575] Bluetooth: hci0: last event is not cmd complete (0x0f)
Jul 11 20:00:43 win-Dell-Precision-M3800 kernel: [ 1176.253683] Bluetooth: hci0: last event is not cmd complete (0x0f)

I am on
Linux win-Dell-Precision-M3800 4.15.0-24-generic #26-Ubuntu SMP Wed Jun 13 08:44:47 UTC 2018 x86_64 x86_64 x86_64 GNU/Linux

---

### Post by mihail-cosmin on 2018-07-24
Same here.
Also on Windows the Bluetooth works.
Is there any solution for this? Is anybody checking this bug ?

```

mihail-cosmin@mihailcosmin-HP-Pavilion-Notebook:~$  rfkill list
0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: brcmwl-0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
2: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no
mihail-cosmin@mihailcosmin-HP-Pavilion-Notebook:~$ dmesg | grep Blue
[   15.771435] Bluetooth: Core ver 2.22
[   15.771464] Bluetooth: HCI device and connection manager initialized
[   15.771469] Bluetooth: HCI socket layer initialized
[   15.771473] Bluetooth: L2CAP socket layer initialized
[   15.771480] Bluetooth: SCO socket layer initialized
[   15.913364] Bluetooth: hci0: BCM: chip id 70
[   15.916361] Bluetooth: hci0: BCM: features 0x06
[   15.934358] Bluetooth: hci0: BCM43142A
[   15.934365] Bluetooth: hci0: BCM (001.001.011) build 0000
[   15.936966] Bluetooth: hci0: BCM: Patch brcm/BCM.hcd not found
[   17.417963] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   17.417967] Bluetooth: BNEP filters: protocol multicast
[   17.417975] Bluetooth: BNEP socket layer initialized
[   38.260984] Bluetooth: RFCOMM TTY layer initialized
[   38.261021] Bluetooth: RFCOMM socket layer initialized
[   38.261032] Bluetooth: RFCOMM ver 1.11
[  921.315012] Bluetooth: hci0: last event is not cmd complete (0x0f)
[  959.205327] Bluetooth: hci0: last event is not cmd complete (0x0f)
[  975.336331] Bluetooth: hci0: last event is not cmd complete (0x0f)
[  991.205338] Bluetooth: hci0: last event is not cmd complete (0x0f)
[ 1007.332892] Bluetooth: hci0: last event is not cmd complete (0x0f)
[ 1023.205340] Bluetooth: hci0: last event is not cmd complete (0x0f)
[ 1039.332880] Bluetooth: hci0: last event is not cmd complete (0x0f)
[ 1055.205301] Bluetooth: hci0: last event is not cmd complete (0x0f)
[ 1071.334067] Bluetooth: hci0: last event is not cmd complete (0x0f)
[ 1087.204863] Bluetooth: hci0: last event is not cmd complete (0x0f)
mihail-cosmin@mihailcosmin-HP-Pavilion-Notebook:~$  lspci -knn | grep Net -A2; lsusb
03:00.0 Network controller [0280]: Broadcom Limited BCM43142 802.11b/g/n [14e4:4365] (rev 01)
    Subsystem: Hewlett-Packard Company BCM43142 802.11b/g/n [103c:804a]
    Kernel driver in use: wl
Bus 001 Device 002: ID 0438:7900 Advanced Micro Devices, Inc. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 002 Device 004: ID 046d:c52b Logitech, Inc. Unifying Receiver
Bus 002 Device 003: ID 0a5c:216d Broadcom Corp. 
Bus 002 Device 002: ID 04f2:b50d Chicony Electronics Co., Ltd 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```

---

### Post by redpoppet on 2019-01-18
It appears that this may not be solved.  I don't know if I have an answer for your circumstances or not.  But I had the same problem.  Two dells that I have (same model) would pick up bluetooth, but another Dell, different model wouldn't.  I couldn't find an answer anywhere.  I replicated the software environment on the problem machine from the others to no avail.  For me at least the problem was in the bios. I had to go into two settings under "wireless" and the bluetooth options there weren't checked.  Checked these and no drama.  Seeing as though you have it working on Windows this may not be applicable, but this worked for me.  Hope it helps.

---

