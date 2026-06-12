---
title: "Bluetooth issue with Ubuntu 18.10"
date: 2019-01-02
forum: General Help
---

### Post by huskky on 2019-01-02
So, for a few years i have been using Ubuntu, and recently i got a bluetooth adapter and headset,
However, then i go to audiosink/handsfree it, it gives the error "Device Added Successfully, But failed to connect,"
The error shown below in the Bluetooth devices manager has something with DBus, which i did have to manually make a dbus folder for something else, which is why it is not owned by root,
Upon further messing with it, i run into more issues attempting to edit the things needed as i am not root, and pkexec won't work,


So i am basically at a loss, would i require to reinstall my whole system? (as i know upgrading does cause more issues if anything, at least for me,)
Or is this just a simple, easy fix? doing it with a video running didn't do anything to help,
I am posting with 18.10 due to everyone posting this issue but for lower versions,
(Also, if there is any issues with this post lemme know, it's my first time posting on these forums)

---

### Post by jeremy31 on 2019-01-02
Post results for ```
pactl list short | grep blue
```

---

### Post by huskky on 2019-01-02
8	module-bluetooth-policy		
9	module-bluetooth-discover		
10	module-bluez5-discover		

These are the results of the command,

---

### Post by jeremy31 on 2019-01-02
Post results for ```
lsusb
```
All the correct bluetooth modules are loaded in pulse

---

### Post by huskky on 2019-01-02
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 002: ID 18f8:0f97  
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 003: ID 0a12:0001 Cambridge Silicon Radio, Ltd Bluetooth Dongle (HCI mode)
Bus 006 Device 002: ID 0e6a:02c0 Megawin Technology Co., Ltd 
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 064e:a116 Suyin Corp. UVC 1.3MPixel WebCam
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

---

### Post by jeremy31 on 2019-01-02
Can you try the Live ISO to see if it works there to eliminate the DBUS owned by root issue?

---

### Post by huskky on 2019-01-02
I am sure to try that, i will come back for any updates!

---

### Post by huskky on 2019-01-14
Sorry for the late reply, 

The Live seems to connect without any issue, What could this mean?

---

