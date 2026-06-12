---
title: "Android phone mounting poblem."
date: 2017-03-30
forum: General Help
---

### Post by Furycd001 on 2017-03-30
Hey guys.

Done a reinstall of minimal xubuntu 16.04 xenial using the xubuntu netinstaller / mini.iso. As of reinstalling my os I can no longer access my huawei p9 as a drive. Before it used to automatically connect without any problems. All I had to do was to click on the icon to mount it. The phone would also automatically connect and automatically mount a virtual disk which had windows installer stuff and what not available. As of now when the phone is connected the virtual disk still automatically connects as always, but the phone itself does not appear as a drive as it used to. The phone will appear under lsusb but not under any other terminal command or gparted. From what I found online I ran the code below which installed a bunch of stuff. Once everything was installed I then ran the command directly below. I also ran dmesg which I have attached below also. Thank you very much for taking the time to read this and for taking the time to comment or help.

[B]
lsusb[/B]
```

Bus 002 Device 007: ID 12d1:107e Huawei Technologies Co., Ltd. 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 003: ID 05ac:8215 Apple, Inc. Built-in Bluetooth 2.0+EDR HCI
Bus 004 Device 002: ID 0a5c:4500 Broadcom Corp. BCM2046B1 USB 2.0 Hub (part of BCM2046 Bluetooth)
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 003: ID 05ac:8300 Apple, Inc. Built-in iSight (no firmware loaded)
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 004: ID 05ac:022a Apple, Inc. Internal Keyboard/Trackpad (MacBook Pro) (ISO)
Bus 003 Device 003: ID 05ac:8242 Apple, Inc. Built-in IR Receiver
Bus 003 Device 002: ID 04f3:0212 Elan Microelectronics Corp. Laser Mouse
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

```

**apt**
```
[COLOR=#000000]sudo apt-get update && sudo apt-get upgrade && sudo apt-get install gvfs-backends mtpfs jmtpfs libmtp-common mtp-tools libmtp-dev libmtp-runtime libmtp9 gmtp libdbus-cpp5 libgflags2v5 libgoogle-glog0v5 libmtp-dbg libmtp-doc libmtpserver-dev libmtpserver1 libprocess-cpp3 mtp-server[/COLOR]
```
[B]
sudo mtpfs -o allow_other /media/mtp[/B]
```
Listing raw device(s)
Device 0 (VID=12d1 and PID=107e) is UNKNOWN in libmtp v1.1.10.
Please report this VID/PID and the device model to the libmtp development team
   Found 1 device(s):
   12d1:107e @ bus 2, dev 4
Attempting to connect device
Android device detected, assigning default bug flags

```

**dmesg output:** [http://paste.ubuntu.com/24282376/](http://paste.ubuntu.com/24282376/)

---

### Post by Furycd001 on 2017-04-01
Anyone got any suggestions ?? I cannot find a fix to this problem...

---

### Post by leunam12 on 2017-04-01
Permissions? Have you edited the /etc/udev/rules.d/51-android.rules file to allow Huawei? The line should look like this:```
#Huawei Technologies Co., Ltd. 
SUBSYSTEM=="usb", ATTR{idVendor}=="12d1", MODE="0666", GROUP="plugdev"
```

---

### Post by Furycd001 on 2017-04-02
> **leunam12 said:**
> Permissions? Have you edited the /etc/udev/rules.d/51-android.rules file to allow Huawei? The line should look like this:```
#Huawei Technologies Co., Ltd. 
SUBSYSTEM=="usb", ATTR{idVendor}=="12d1", MODE="0666", GROUP="plugdev"
```

No I have not done this. Never had to do it before but will try it now thanks...

---

### Post by Furycd001 on 2017-04-04
> **leunam12 said:**
> Permissions? Have you edited the /etc/udev/rules.d/51-android.rules file to allow Huawei? The line should look like this:```
#Huawei Technologies Co., Ltd. 
SUBSYSTEM=="usb", ATTR{idVendor}=="12d1", MODE="0666", GROUP="plugdev"
```

Ok so I'm very sorry for the late reply but I was in hospital receiving surgery. I opened up that file and it was completly blank. I copied / pasted in those two lines of code you provided above and everything is working perfectly now. Thank you very much for your help.

---

