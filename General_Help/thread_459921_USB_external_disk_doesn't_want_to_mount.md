---
title: "USB external disk doesn't want to mount"
date: 2007-05-31
forum: General Help
---

### Post by Aerendil on 2007-05-31
Hello wink

I have a problem with my external USB HDD (MyBook 500Go), since yesterday it refused to mount...
First, when I have connected a usb Mp3, my hdd was aumaticilly unmounted Oo. And I had to remove the usb key to reboot my External HDD. But, since this, I cannot mount it...


 
Here is the log i've found with tail -f  /var/log/syslog and some of command that I've tested.

```
aerendil@aerendil:~$ lsusb
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
aerendil@aerendil:~$ lsusb
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
aerendil@aerendil:~$ lsusb
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 002 Device 011: ID 0928:ffff Oxford Semiconductor, Ltd 
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
 
(Why it's display "0928:ffff Oxford Semiconductor, Ltd " only after three time :???:)

///////////////////////////////////////////////////////////////

aerendil@aerendil:~$ /sbin/lsmod | grep usb
usbcore               134280  3 ehci_hcd,uhci_hcd


aerendil@aerendil:~$ /sbin/lsmod | grep vfat
vfat                   14208  0 
fat                    53916  1 vfat

/////////////////////////////////////////////////////////////////

aerendil@aerendil:~$ tail -f /var/log/syslog

May 31 11:41:22 aerendil kernel: [51340.148001] usb 2-1: new full speed USB device using uhci_hcd and address 12
May 31 11:41:23 aerendil kernel: [51340.296052] usb 2-1: configuration #1 chosen from 1 choice
May 31 11:41:23 aerendil NetworkManager: <debug info>^I[1180604483.155798] nm_hal_device_added (): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_928_ffff_noserial'). 
May 31 11:41:23 aerendil NetworkManager: <debug info>^I[1180604483.203826] nm_hal_device_added (): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_928_ffff_noserial_if0'). 
May 31 11:41:23 aerendil NetworkManager: <debug info>^I[1180604483.233739] nm_hal_device_added (): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_928_ffff_noserial_usbraw'). 


[51340.148001] usb 2-1: new full speed USB device using uhci_hcd and address 12
[51340.296052] usb 2-1: configuration #1 chosen from 1 choice

```

If you have any idea :s thanks in advance.

---

