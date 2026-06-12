---
title: "Bluetooth headset paired, trusted &amp; connected but no sound output."
date: 2017-07-28
forum: General Help
---

### Post by makem2 on 2017-07-28
I have a problem with one Bluetooth device, others are paired and connect correctly. However, this is the only headest I have attempted to connect.

The device is a MPOW Crescent Bluetooth headset. I have paired and trusted this device but although it shows as connected, I cannot hear sound. Nor does it take over the sound output from the laptop as it does from my S8.

When connected the Device Manager says:

Received Signal Strength: 49% (Optimal)
Link Quality: 100%
Transmit Power: 51% (Optomal)

Initially I had difficulty getting a pairing and succeeded using information from this post:

[https://askubuntu.com/questions/801404/bluetooth-connection-failed-blueman-bluez-errors-dbusfailederror-protocol-no](https://askubuntu.com/questions/801404/bluetooth-connection-failed-blueman-bluez-errors-dbusfailederror-protocol-no)

```

sudo apt-get install pulseaudio-module-bluetooth
pactl load-module module-bluetooth-discover
```

Although I don't know if it would ever be possible to use the laptop without sound distracting HWMBO whilst watching a soap, it would be great!

```

makem@ssdTOSH:~$ lsb_release -a
LSB Version:    core-9.20160110ubuntu0.2-amd64:core-9.20160110ubuntu0.2-noarch:security-9.20160110ubuntu0.2-amd64:security-9.20160110ubuntu0.2-noarch
Distributor ID:    Ubuntu
Description:    Ubuntu 16.04.2 LTS
Release:    16.04
Codename:    xenial

makem@ssdTOSH:~$ hciconfig
hci0:    Type: BR/EDR  Bus: USB
    BD Address: 34:E6:AD:BA:1F:D4  ACL MTU: 1021:5  SCO MTU: 96:6
    UP RUNNING PSCAN 
    RX bytes:110043 acl:170 sco:1680 events:1046 errors:0
    TX bytes:117560 acl:160 sco:1666 commands:713 errors:0


makem@ssdTOSH:~$ hcitool dev
Devices:
    hci0    34:E6:AD:BA:1F:D4
makem@ssdTOSH:~$


```

---

### Post by leozinho29_eu on 2017-07-28
I believe the bluetooth sound is not set to default automatically if it was never set as default in any moment. Opening pavucontrol and choosing the sound output device as the bluetooth would make this work, and the option to set it as default is, at least on my usage, remembered.

Maybe the bluetooth sound is not configured, this can be done with pavucontrol.

---

### Post by makem2 on 2017-07-28
Thanks

---

