---
title: "Palm TX Issues"
date: 2007-10-23
forum: General Help
---

### Post by jvc26 on 2007-10-23
Well, basically looks like there is fairly little information out there to assist with the problem, however, this is a summary: (Note I am using gutsy)

Having looked through a stack of links on making a palm work with ubuntu, I have jpilot, and have tried the methods listed [here]("https://help.ubuntu.com/community/PalmtopHowto") in an attempt to make my palm TX work with jpilot.

However, as sync didn't work, I had a look when I pressed the hotsync button at /var/log/messages which gave me:
```

tail -f /var/log/messages

```
Output
```

Oct 23 08:33:54 oncilla kernel: [  333.988000] usb 3-2: new full speed USB device using ohci_hcd and address 69
Oct 23 08:33:55 oncilla kernel: [  334.572000] usb 3-2: new full speed USB device using ohci_hcd and address 70
Oct 23 08:33:59 oncilla kernel: [  339.248000] usb 3-2: new full speed USB device using ohci_hcd and address 71
Oct 23 08:34:00 oncilla kernel: [  339.992000] usb 3-2: new full speed USB device using ohci_hcd and address 72
Oct 23 08:34:01 oncilla kernel: [  340.736000] usb 3-2: new full speed USB device using ohci_hcd and address 73
Oct 23 08:34:02 oncilla kernel: [  341.320000] usb 3-2: new full speed USB device using ohci_hcd and address 74

```
So far so good I thought, however, then with dmesg:
```

[  334.572000] usb 3-2: new full speed USB device using ohci_hcd and address 70
[  334.980000] usb 3-2: device not accepting address 70, error -62
[  339.248000] usb 3-2: new full speed USB device using ohci_hcd and address 71
[  339.428000] usb 3-2: device descriptor read/64, error -62
[  339.712000] usb 3-2: device descriptor read/64, error -62
[  339.992000] usb 3-2: new full speed USB device using ohci_hcd and address 72
[  340.172000] usb 3-2: device descriptor read/64, error -62
[  340.456000] usb 3-2: device descriptor read/64, error -62
[  340.736000] usb 3-2: new full speed USB device using ohci_hcd and address 73
[  341.144000] usb 3-2: device not accepting address 73, error -62
[  341.320000] usb 3-2: new full speed USB device using ohci_hcd and address 74
[  341.728000] usb 3-2: device not accepting address 74, error -62

```
Not good. Therefore an ls -l of /dev/ttyUSB* and /dev/pil* (looking for /dev/pilot which is a symlink which should be put up from the udev rule) threw back nothing. Does anyone know how to progress from here?
Thanks very much,
Il

---

### Post by jvc26 on 2007-10-24
Mysteriously this has managed to fix itself.
Il

---

