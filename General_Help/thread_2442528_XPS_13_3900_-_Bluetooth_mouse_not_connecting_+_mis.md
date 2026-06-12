---
title: "XPS 13 3900 - Bluetooth mouse not connecting + missing bluetooth icon"
date: 2020-05-04
forum: General Help
---

### Post by makem2 on 2020-05-04
I have a generic bluetooth mouse which is working in this machine on windows 10. I cannot get it to connect in ubuntu 20.04. It connects fine in ubuntu 18.04 on another machine.

I also appear to have somehow 'lost' my panel bluetooth icon at some stage too.

Both bluetooth adapters and bluetooth manager do not work from 'activities'

Dell are not helpful as I have dual booted the machine. So far this bluetooth problem is the only one I have found, out of the box.

Information I can find is:

```

makem@XPS-13-9300:~$ rfkill list
0: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no
1: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
makem@XPS-13-9300:~

```

```

makem@XPS-13-9300:~$ dmesg | grep -i blue
[    4.235415] Bluetooth: Core ver 2.22
[    4.235426] Bluetooth: HCI device and connection manager initialized
[    4.235428] Bluetooth: HCI socket layer initialized
[    4.235430] Bluetooth: L2CAP socket layer initialized
[    4.235432] Bluetooth: SCO socket layer initialized
[    5.626821] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[    5.626822] Bluetooth: BNEP filters: protocol multicast
[    5.626825] Bluetooth: BNEP socket layer initialized
[    6.270101] Bluetooth: hci0: command 0xfc05 tx timeout
[    6.270388] Bluetooth: hci0: Reading Intel version information failed (-110)
makem@XPS-13-9300:~$

```

```

makem@XPS-13-9300:~$ hciconfig -a
hci0:    Type: Primary  Bus: USB
    BD Address: 00:00:00:00:00:00  ACL MTU: 0:0  SCO MTU: 0:0
    DOWN 
    RX bytes:0 acl:0 sco:0 events:0 errors:0
    TX bytes:3 acl:0 sco:0 commands:1 errors:0
    Features: 0x00 0x00 0x00 0x00 0x00 0x00 0x00 0x00
    Packet type: DM1 DH1 HV1 
    Link policy: 
    Link mode: SLAVE ACCEPT 
makem@XPS-13-9300:~$ 

```

Edit:

I have updated bluetooth:

[https://www.ubuntuupdates.org/package/core/focal/universe/base/bluetooth](https://www.ubuntuupdates.org/package/core/focal/universe/base/bluetooth)

bluez version (5.53-0ubuntu3)

blueman version (2.1.2-1)
[URL="https://www.ubuntuupdates.org/package/core/focal/universe/base/bluetooth"]
[/URL]

---

### Post by makem2 on 2020-05-04
Crash reports:

```

makem@XPS-13-9300:/var/crash$ ls -la
total 1832
drwxrwxrwt  2 root     root        4096 May  4 20:55 .
drwxr-xr-x 14 root     root        4096 May  4 09:52 ..
-rw-r-----  1 makem    makem     109753 May  4 10:25 _usr_bin_blueman-assistant.1000.crash
-rw-rw-r--  1 makem    makem          0 May  4 10:39 _usr_bin_blueman-assistant.1000.upload
-rw-------  1 whoopsie whoopsie       5 May  4 10:42 _usr_bin_blueman-assistant.1000.uploaded
-rw-r-----  1 makem    makem      85435 May  4 20:55 _usr_bin_blueman-tray.1000.crash
-rw-rw-r--  1 makem    makem          0 May  4 20:50 _usr_bin_blueman-tray.1000.upload
-rw-------  1 whoopsie whoopsie       5 May  4 20:55 _usr_bin_blueman-tray.1000.uploaded
-rw-r-----  1 makem    whoopsie 1655605 May  4 15:21 _usr_lib_x86_64-linux-gnu_xfce4_panel_wrapper-1.0.1000.crash
-rw-rw-r--  1 makem    makem          0 May  4 15:21 _usr_lib_x86_64-linux-gnu_xfce4_panel_wrapper-1.0.1000.upload
-rw-------  1 whoopsie whoopsie      37 May  4 15:21 _usr_lib_x86_64-linux-gnu_xfce4_panel_wrapper-1.0.1000.uploaded
makem@XPS-13-9300:/var/crash$ 

```

---

### Post by makem2 on 2020-05-04
Got the bluetooth icon back by renaming the ~/.config/xfce folder to xfce.ol and rebooting.

Xfce made a new folder with initial xfce desktop settings including the panel and bluetooth icon.

Removed the mouse pairing from bluetooth and re-paired. This time I was asked to give permission and from then the mouse worked.

Will mark it solved but I don't really know why that worked,

---

### Post by makem2 on 2020-05-04
Spoke to soon! Blueman-assistant crashed at 0011 on 5.4.20 thats about an hour after I got it working. The icon is still present though.

Still need help :)

---

### Post by ervinwatson on 2020-08-08
> **makem2 said:**
> I have a generic bluetooth mouse which is working in this machine on windows 10. [I]("https://www.walgreenslistens.mobi/") cannot get it to connect in ubuntu 20.04. It connects fine in ubuntu 18.04 on another machine.

I also appear to have somehow 'lost' my panel bluetooth icon at some stage too.

Both bluetooth adapters and bluetooth manager do not work from 'activities'

Dell are not helpful as I have dual booted the machine. So far this bluetooth problem is the only one I have found, out of the box.

Information I can find is:

```

makem@XPS-13-9300:~$ rfkill list
0: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no
1: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
makem@XPS-13-9300:~

```

```

makem@XPS-13-9300:~$ dmesg | grep -i blue
[    4.235415] Bluetooth: Core ver 2.22
[    4.235426] Bluetooth: HCI device and connection manager initialized
[    4.235428] Bluetooth: HCI socket layer initialized
[    4.235430] Bluetooth: L2CAP socket layer initialized
[    4.235432] Bluetooth: SCO socket layer initialized
[    5.626821] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[    5.626822] Bluetooth: BNEP filters: protocol multicast
[    5.626825] Bluetooth: BNEP socket layer initialized
[    6.270101] Bluetooth: hci0: command 0xfc05 tx timeout
[    6.270388] Bluetooth: hci0: Reading Intel version information failed (-110)
makem@XPS-13-9300:~$

```

```

makem@XPS-13-9300:~$ hciconfig -a
hci0:    Type: Primary  Bus: USB
    BD Address: 00:00:00:00:00:00  ACL MTU: 0:0  SCO MTU: 0:0
    DOWN 
    RX bytes:0 acl:0 sco:0 events:0 errors:0
    TX bytes:3 acl:0 sco:0 commands:1 errors:0
    Features: 0x00 0x00 0x00 0x00 0x00 0x00 0x00 0x00
    Packet type: DM1 DH1 HV1 
    Link policy: 
    Link mode: SLAVE ACCEPT 
makem@XPS-13-9300:~$ 

```

Edit:

I have updated bluetooth:

[https://www.ubuntuupdates.org/package/core/focal/universe/base/bluetooth](https://www.ubuntuupdates.org/package/core/focal/universe/base/bluetooth)

bluez version (5.53-0ubuntu3)

blueman version (2.1.2-1)
[URL="https://www.ubuntuupdates.org/package/core/focal/universe/base/bluetooth"]
[/URL]


[COLOR=#000000][FONT=Arial]Thanks for the clarification[/FONT][/COLOR]

---

### Post by makem2 on 2020-11-29
Ur welcome

---

