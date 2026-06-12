---
title: "usb-parallel cable problem"
date: 2007-10-18
forum: General Help
---

### Post by tstavely on 2007-10-18
I purchased a cheap usb to parallel cable ("cheap" may be the problem) to connect my thinkpad to a Laserjet 4P.  The up-to-date feisty on the laptop detects the printer just fine via this cable if the printer is running and plugged in when the computer boots.  However, if I plug the printer into the already running computer there is a failure of recognition -- lots and lots of these in the dmesg:

[PHP][ 4443.368000] usb 2-1: device descriptor read/64, error -71
[ 4443.592000] usb 2-1: device descriptor read/64, error -71
[ 4443.808000] usb 2-1: new full speed USB device using uhci_hcd and address 44
[ 4443.928000] usb 2-1: device descriptor read/64, error -71
[ 4444.152000] usb 2-1: device descriptor read/64, error -71
[ 4444.368000] usb 2-1: new full speed USB device using uhci_hcd and address 45
[ 4444.776000] usb 2-1: device not accepting address 45, error -71
[ 4444.888000] usb 2-1: new full speed USB device using uhci_hcd and address 46
[ 4445.296000] usb 2-1: device not accepting address 46, error -71
[ 4975.584000] usb 2-2: new full speed USB device using uhci_hcd and address 47
[ 4975.708000] usb 2-2: device descriptor read/64, error -71
[ 4975.932000] usb 2-2: device descriptor read/64, error -71
[ 4976.148000] usb 2-2: new full speed USB device using uhci_hcd and address 48
[ 4976.268000] usb 2-2: device descriptor read/64, error -71
[ 4976.492000] usb 2-2: device descriptor read/64, error -71
[ 4976.708000] usb 2-2: new full speed USB device using uhci_hcd and address 49
[ 4977.116000] usb 2-2: device not accepting address 49, error -71
[ 4977.228000] usb 2-2: new full speed USB device using uhci_hcd and address 50
[ 4977.636000] usb 2-2: device not accepting address 50, error -71
[/PHP]

The print spooler keeps trying to print and each time it does there's another error.  If I unplug the usb end of the cable and plug back in, even to the other usb port, another error.  Restart the printer and the document prints while the login screen waits for a password.

There ought to be some command that would reawaken the usb bus or something to recognize the printer without a cumbersome restart.

Thanks for any suggestions.

---

### Post by tstavely on 2007-10-18
Here is what one sees when the computer can see the printer via this cable:

~$ lsusb
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 002: ID 067b:2305 Prolific Technology, Inc. PL2305 Parallel Port
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000

If I power the printer down and back up it's still there.  Ditto if I plug it out and back in.  Maybe the problem has to do with hibernation....  I'm going to do that and come back in a few hours.  We'll see.

---

### Post by tstavely on 2007-10-18
Indeed, after hibernation the printer disappears:

~$ lsusb
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000

---

