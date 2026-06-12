---
title: "USB errors in dmesg and messages file"
date: 2006-07-26
forum: General Help
---

### Post by jimsfishing on 2006-07-26
I seem to have a problem with a usb device on my system.  I am using a usb mouse and my case has the normal usb hub attached to the mb.  Has anyone seen these errors before?

/var/log/messages -->

Jul 26 15:17:43 localhost kernel: [17381422.756000] usb 3-2: new low speed USB device using uhci_hcd and address 113
Jul 26 15:17:43 localhost kernel: [17381423.316000] usb 3-2: new low speed USB device using uhci_hcd and address 114
Jul 26 15:17:44 localhost kernel: [17381423.836000] usb 3-2: new low speed USB device using uhci_hcd and address 115
Jul 26 15:17:44 localhost kernel: [17381424.484000] usb 3-1: new low speed USB device using uhci_hcd and address 116
Jul 26 15:17:45 localhost kernel: [17381425.044000] usb 3-1: new low speed USB device using uhci_hcd and address 117
Jul 26 15:17:45 localhost kernel: [17381425.604000] usb 3-1: new low speed USB device using uhci_hcd and address 118
Jul 26 15:17:46 localhost kernel: [17381426.124000] usb 3-1: new low speed USB device using uhci_hcd and address 119
Jul 26 15:17:47 localhost kernel: [17381426.772000] usb 3-2: new low speed USB device using uhci_hcd and address 120
Jul 26 15:17:47 localhost kernel: [17381427.332000] usb 3-2: new low speed USB device using uhci_hcd and address 121
Jul 26 15:17:48 localhost kernel: [17381427.892000] usb 3-2: new low speed USB device using uhci_hcd and address 122
Jul 26 15:17:48 localhost kernel: [17381428.412000] usb 3-2: new low speed USB device using uhci_hcd and address 123
Jul 26 15:17:49 localhost kernel: [17381429.060000] usb 3-1: new low speed USB device using uhci_hcd and address 124
Jul 26 15:17:49 localhost kernel: [17381429.628000] usb 3-1: new low speed USB device using uhci_hcd and address 125
Jul 26 15:17:50 localhost kernel: [17381430.188000] usb 3-1: new low speed USB device using uhci_hcd and address 126
Jul 26 15:17:51 localhost kernel: [17381430.708000] usb 3-1: new low speed USB device using uhci_hcd and address 127



output from dmesg -->

[17381555.780000] usb 3-2: new low speed USB device using uhci_hcd and address 93
[17381555.900000] usb 3-2: device descriptor read/64, error -71
[17381556.124000] usb 3-2: device descriptor read/64, error -71
[17381556.340000] usb 3-2: new low speed USB device using uhci_hcd and address 94
[17381556.748000] usb 3-2: device not accepting address 94, error -71
[17381556.860000] usb 3-2: new low speed USB device using uhci_hcd and address 95
[17381557.268000] usb 3-2: device not accepting address 95, error -71
[17381557.508000] usb 3-1: new low speed USB device using uhci_hcd and address 96
[17381557.628000] usb 3-1: device descriptor read/64, error -71
[17381557.852000] usb 3-1: device descriptor read/64, error -71
[17381558.068000] usb 3-1: new low speed USB device using uhci_hcd and address 97
[17381558.188000] usb 3-1: device descriptor read/64, error -71
[17381558.412000] usb 3-1: device descriptor read/64, error -71
[17381558.628000] usb 3-1: new low speed USB device using uhci_hcd and address 98
[17381559.036000] usb 3-1: device not accepting address 98, error -71
[17381559.148000] usb 3-1: new low speed USB device using uhci_hcd and address 99

---

