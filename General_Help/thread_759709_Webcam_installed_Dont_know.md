---
title: "Webcam installed? Dont know"
date: 2008-04-19
forum: General Help
---

### Post by mfreeze1 on 2008-04-19
New to Ubuntu.. read the posts about installing a webcam and still getting nowhere.

The cam is a Prolink Pcc1300

tried camorama.. says could not connect to video device
tried easycam . . could not download it or figure it out.. 

below seems to be what everyone wants to see

My Lsusb is
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 004: ID 0c45:627b Microdia 
Bus 003 Device 003: ID 04d9:0499 Holtek Semiconductor, Inc. 
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  


can anyone help a brother out?
my dmesg after I unplugged and plugged it back in..is
[ 1997.612000] usb 3-1: USB disconnect, address 2
[ 2000.372000] usb 3-1: new full speed USB device using uhci_hcd and address 4
[ 2000.516000] usb 3-1: not running at top speed; connect to a high speed hub
[ 2000.548000] usb 3-1: configuration #1 chosen from 1 choice
[ 2655.584000] usb 3-1: USB disconnect, address 4
[ 2659.856000] usb 3-1: new full speed USB device using uhci_hcd and address 5
[ 2660.000000] usb 3-1: not running at top speed; connect to a high speed hub
[ 2660.032000] usb 3-1: configuration #1 chosen from 1 choice

My syslog says
Apr 19 23:00:01 msf-desktop NetworkManager: <debug> [1208620801.086529] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/usb_device_c45_627b_noserial_usbraw'). 
Apr 19 23:00:01 msf-desktop NetworkManager: <debug> [1208620801.087019] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/usb_device_c45_627b_noserial_if0'). 
Apr 19 23:00:01 msf-desktop NetworkManager: <debug> [1208620801.087512] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/usb_device_c45_627b_noserial'). 
Apr 19 23:00:05 msf-desktop kernel: [ 2659.856000] usb 3-1: new full speed USB device using uhci_hcd and address 5
Apr 19 23:00:05 msf-desktop kernel: [ 2660.000000] usb 3-1: not running at top speed; connect to a high speed hub
Apr 19 23:00:05 msf-desktop NetworkManager: <debug> [1208620805.576393] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_c45_627b_noserial'). 
Apr 19 23:00:05 msf-desktop NetworkManager: <debug> [1208620805.625949] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_c45_627b_noserial_if0'). 
Apr 19 23:00:05 msf-desktop NetworkManager: <debug> [1208620805.655966] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_c45_627b_noserial_usbraw'). 
Apr 19 23:00:05 msf-desktop kernel: [ 2660.032000] usb 3-1: configuration #1 chosen from 1 choice

---

### Post by ryanhaigh on 2008-04-19
This page may help [https://help.ubuntu.com/community/Webcam](https://help.ubuntu.com/community/Webcam)

Unfortunately I have little experience dealing with webcams under linux (they have always just worked) I would check for an entry under /dev/v4l/ for the camera or looking at the output of lsmod and seeing if any of the driver modules mentioned on the above page are in use. 

This line: configuration #1 chosen from 1 choice, indicates to me that something is claiming the device although it may be the audio component if you have a mic onboard with the cam.

---

