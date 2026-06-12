---
title: "Bluetooth Hearing Aid Support"
date: 2014-08-14
forum: General Help
---

### Post by geronl on 2014-08-14
A fellow Linux user says that his Bluetooth does not work with his Phonak Compilot hearing aids, it "pairs" but does not connect and nothing happens. I cannot find anything about this online at all. I suppose not a lot of Linux programmers are using hearing aids... yet. He says he has tried Bluex and Blueman. He uses Ubuntu and Mint. How would this be different than other Bluetooth audio devices?

---

### Post by geronl on 2014-08-14
A friend uses Ubuntu and Mint and cannot get Bluetooth working properly with his Phonak Compilot hearing aids. How do hearing aids differ from other audio devices enough to be a problem? He has tried Bluex and Blueman, he can get them "paired", but not connected. I suppose that not a lot of programmers are yet using hearing aids because a Google (okay DuckDuckGo) search came up really, really empty.

If anyone has any idea on getting them to function with Bluetooth, it would be helpful.

---

### Post by QIII on 2014-08-14
Threads merged.

Please do not post the same question in multiple areas of the forums.  It dilutes the community's efforts to help by having different people answering in different places and may be confusing.

Thanks.

---

### Post by geronl on 2014-08-15
I thought the first post had been rejected from "chat"

---

### Post by tgalati4 on 2014-08-16
What tools do you have on your system?  Open a terminal:

```
tgalati4@Mint14-Extensa ~/Desktop $ apropos bluetooth
blueman-applet (1)   - a tray applet for managing bluetooth
blueman-assistant (1) - application for configuring and pairing bluetooth devices
blueman-manager (1)  - bluetooth device manager
blueman-sendto (1)   - application for sending files to bluetooth devices
blueman-services (1) - Configure local bluetooth services
bluetooth-agent (1)  - Bluetooth pass agent
bluetoothd (8)       - Bluetooth daemon
bluez-simple-agent (1) - A PIN management and agent program for pairing to Bluetooth device.
ciptool (1)          - Bluetooth Common ISDN Access Profile (CIP)
hciconfig (8)        - configure Bluetooth devices
hcitool (1)          - configure Bluetooth connections
hid2hci (8)          - Bluetooth HID to HCI mode switching utility
mate-bluetooth-applet (1) - MATE applet for prompting the user for a Bluetooth passkey (PIN)
mate-bluetooth-properties (1) - GTK dialog for managing properties of the Linux Bluetooth stack
mate-bluetooth-sendto (1) - GTK application for transfering files over Bluetooth
mate-bluetooth-wizard (1) - GTK wizard for setting up devices with the Linux Bluetooth stack

```

It might look like:

> tgalati4@Mint14-Extensa ~/Desktop $ apropos bluetooth
blueman-applet (1)   - a tray applet for managing bluetooth
blueman-assistant (1) - application for configuring and pairing bluetooth devices
blueman-manager (1)  - bluetooth device manager
blueman-sendto (1)   - application for sending files to bluetooth devices
blueman-services (1) - Configure local bluetooth services
bluetooth-agent (1)  - Bluetooth pass agent
bluetoothd (8)       - Bluetooth daemon
bluez-simple-agent (1) - A PIN management and agent program for pairing to Bluetooth device.
ciptool (1)          - Bluetooth Common ISDN Access Profile (CIP)
hciconfig (8)        - configure Bluetooth devices
hcitool (1)          - configure Bluetooth connections
hid2hci (8)          - Bluetooth HID to HCI mode switching utility
mate-bluetooth-applet (1) - MATE applet for prompting the user for a Bluetooth passkey (PIN)
mate-bluetooth-properties (1) - GTK dialog for managing properties of the Linux Bluetooth stack
mate-bluetooth-sendto (1) - GTK application for transfering files over Bluetooth
mate-bluetooth-wizard (1) - GTK wizard for setting up devices with the Linux Bluetooth stack


After pairing, examine:

```
hcitool dev
dmesg | tail -40
```

Only paste the bluetooth-related messages.

---

