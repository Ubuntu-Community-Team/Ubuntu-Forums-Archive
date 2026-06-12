---
title: "USB Hub"
date: 2007-05-05
forum: General Help
---

### Post by Kalifornia909 on 2007-05-05
I have a belking 6 port usb hub that does not work with ubuntu. I tried microsuck and it powered up fine. i need this device because i own more usb devices then i do socks. I am using fiesty fox ubuntu. Please help. Thank you

---

### Post by Kalifornia909 on 2007-05-08
bump! can anyone give me some help please

---

### Post by Pikey Joe on 2007-05-08
This probably won't help, but I've got the Belkin F5U237 7-port hub, which works fine - I just plugged it in.

---

### Post by Kalifornia909 on 2007-05-08
im not sure why it is not getting power. it works fine with windows. my mobo has a usb keyboard and mouse plugged in. the hub is plugged in the same usb mobo hub. im baffled

---

### Post by dcstar on 2007-05-09
> **Kalifornia909 said:**
> im not sure why it is not getting power. it works fine with windows. my mobo has a usb keyboard and mouse plugged in. the hub is plugged in the same usb mobo hub. im baffled

I have a super-cheap 4 port USB hub plugged into my PC and it works ok.

In a terminal, run:
```
dmesg
```
when you plug things in (like the hub) and post the last few lines.

---

### Post by Kalifornia909 on 2007-05-09
i ran dmesg | tail and this is what i got 
[ 1024.377932] usb 3-4: new high speed USB device using ehci_hcd and address 18
[ 1024.489838] usb 3-4: device descriptor read/64, error -71
[ 1024.705664] usb 3-4: device descriptor read/64, error -71
[ 1024.921486] usb 3-4: new high speed USB device using ehci_hcd and address 19
[ 1025.033394] usb 3-4: device descriptor read/64, error -71
[ 1025.249215] usb 3-4: device descriptor read/64, error -71
[ 1025.465038] usb 3-4: new high speed USB device using ehci_hcd and address 20
[ 1025.872695] usb 3-4: device not accepting address 20, error -71
[ 1025.984613] usb 3-4: new high speed USB device using ehci_hcd and address 21
[ 1026.392267] usb 3-4: device not accepting address 21, error -71

---

### Post by dcstar on 2007-05-10
> **Kalifornia909 said:**
> i ran dmesg | tail and this is what i got 
[ 1024.377932] usb 3-4: new high speed USB device using ehci_hcd and address 18
[ 1024.489838] usb 3-4: device descriptor read/64, error -71
[ 1024.705664] usb 3-4: device descriptor read/64, error -71
[ 1024.921486] usb 3-4: new high speed USB device using ehci_hcd and address 19
[ 1025.033394] usb 3-4: device descriptor read/64, error -71
[ 1025.249215] usb 3-4: device descriptor read/64, error -71
[ 1025.465038] usb 3-4: new high speed USB device using ehci_hcd and address 20
[ 1025.872695] usb 3-4: device not accepting address 20, error -71
[ 1025.984613] usb 3-4: new high speed USB device using ehci_hcd and address 21
[ 1026.392267] usb 3-4: device not accepting address 21, error -71

It is possible that your USB hardware is not supported by the Linux kernel, do you get errors with other USB devices plugged into the same PC port?

---

### Post by mdurham on 2007-05-10
There is something screwy about using a hub. My web cam works fine if I plug it directly into a USB port but it won't work through a hub. It never has. I've seen quite a few posts about hubs not working.
This sort of thing never gets fixed, it goes from distro to distro, It seems they are too busy charging on to the next distro with rotating cubes etc. to fix these (apparently) insignificant problems.

---

### Post by Kalifornia909 on 2007-05-10
i can plug stuff directly in the port but not the hub. i do hope that petty stuff like this will get fixed

---

### Post by Kalifornia909 on 2007-05-12
Bump! Can anyone give me any insight

---

### Post by fragos on 2007-05-12
USB hubs are very simple devices.  I bought an iRock 4 port -- very cheap and it works well.  Your issue might be power.  If you don't have a separate power source for the hub I suggest that you get one.  Which devices you run off the hub might also make a difference.  My webcam only shows the top of the image when plugged into the hub but works fine with a direct connect.  I've connected my slow speed devices, mouse and wacom tablet, to the hub and direct connect the higher speed ones.  Lastly, some hubs are only USB 1.1 which could give you problems with USB 2.0 devices or at least not support USB 2.0 devices at the higher speed.

---

