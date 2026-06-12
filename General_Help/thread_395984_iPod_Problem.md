---
title: "iPod Problem"
date: 2007-03-28
forum: General Help
---

### Post by HarrisonHopkins on 2007-03-28
Okay, so today I went out and bought a new iPod USB cabled, due to me losing my original.  When I plug in my iPod not,nothing happens on the iPod or on Ubuntu. Any help?

---

### Post by alberto.m.vasquez on 2007-03-28
i had the same problem. look for my post, search for "ipod".
i got a solution and now i am able to manage the ipod with
gtkpod. havent been able to use it with banshee or amarok
though, but gtkpod does all the basics (and more).

---

### Post by HarrisonHopkins on 2007-03-29
I just tried what you did, and my iPod still does not connect to Ubuntu at all.

---

### Post by HarrisonHopkins on 2007-03-29
I really don't want to have to go to Windows to be able to charge my iPod.

---

### Post by HarrisonHopkins on 2007-03-29
I would really like this fixed by tomorrow so I can use my iPod on the bus.

---

### Post by tgm4883 on 2007-03-29
Sounds like a problem with your usb cable or usb port.  It should still charge even if ubuntu doesn't recognize it

---

### Post by HarrisonHopkins on 2007-03-29
No, not the port because I usually use it to use my wireless mouse, and not the cable because it works fine if I have it plugged in when I boot up the computer.

---

### Post by HarrisonHopkins on 2007-03-29
Port worksfine, using it for mouse right now. Cable works fin, tried it on a friends computer. Any one have an idea why my Linux decided it doesn't want to use it?

---

### Post by HarrisonHopkins on 2007-03-29
Okay, I just tried Disk Mode, and it went to do not disconnect, and was charging for about half a second, and then when to "Okay to Disconnect. Which really makes no sense right now.

---

### Post by tdwester on 2007-03-29
What type of Ipod is it?

---

### Post by HarrisonHopkins on 2007-03-29
Its an old 4G B&W iPod. It worked fine before, I don't know why it won't now.

---

### Post by tdwester on 2007-03-29
It sounds like the cable may be bad.

---

### Post by HarrisonHopkins on 2007-03-29
As I said, earlier I tested it on a friends computer, and it worked fine. Windows recognized it, iTunes recognized, the whole 9 yards.

---

### Post by tdwester on 2007-03-29
I do not have any Idea. Are the usb ports OK?

---

### Post by HarrisonHopkins on 2007-03-29
Yes, I'm using the one that I tried the iPod on right now for my mouse.

---

### Post by tdwester on 2007-03-29
Try lsubs in terminal,with Ipod pluged in to see if is there at all.

---

### Post by HarrisonHopkins on 2007-03-29
Bus 002 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 005 Device 001: ID 0000:0000  
Bus 003 Device 002: ID 045e:00e1 Microsoft Corp. 
Bus 003 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000 

The Microsoft thing is my mouse.

---

### Post by tdwester on 2007-03-29
Wow I have no idea then.

---

### Post by HarrisonHopkins on 2007-03-29
Thanks for trying to help...

---

### Post by HarrisonHopkins on 2007-03-29
That's odd. It's charging now, but it had never mounted. I don't get why it will charge, but not mount.

---

### Post by HarrisonHopkins on 2007-03-29
Okay, I just rann dmesg like I had read to do in another thread, and it is saying that the iPod will not accept the address that it is being given.

```
[17195176.816000] usb 1-3: new high speed USB device using ehci_hcd and address 36
[17195177.336000] usb 1-3: device not accepting address 36, error -71
[17195177.448000] usb 1-3: new high speed USB device using ehci_hcd and address 37
[17195177.560000] usb 1-3: device descriptor read/64, error -71
[17195178.184000] usb 1-3: device not accepting address 37, error -71
[17195178.296000] usb 1-3: new high speed USB device using ehci_hcd and address 38
[17195178.704000] usb 1-3: device not accepting address 38, error -71
[17195178.816000] usb 1-3: new high speed USB device using ehci_hcd and address 39
[17195179.224000] usb 1-3: device not accepting address 39, error -71
[17195487.028000] usb 1-3: new high speed USB device using ehci_hcd and address 40
[17195487.140000] usb 1-3: device descriptor read/64, error -71
[17195487.376000] usb 1-3: string descriptor 0 read error: -71
[17195487.376000] usb 1-3: string descriptor 0 read error: -71
[17195487.376000] usb 1-3: configuration #1 chosen from 1 choice
[17195487.468000] usbcore: registered new driver libusual
[17195487.488000] Initializing USB Mass Storage driver...
[17195487.488000] scsi2 : SCSI emulation for USB Mass Storage devices
[17195487.488000] usb-storage: device found at 40
[17195487.488000] usbcore: registered new driver usb-storage
[17195487.488000] usb-storage: waiting for device to settle before scanning
[17195487.488000] USB Mass Storage support registered.
[17195492.488000] usb-storage: device scan complete
[17195492.600000] usb 1-3: reset high speed USB device using ehci_hcd and address 40
[17195493.120000] usb 1-3: device not accepting address 40, error -71
[17195493.232000] usb 1-3: reset high speed USB device using ehci_hcd and address 40
[17195493.344000] usb 1-3: device descriptor read/64, error -71
[17195493.560000] usb 1-3: device descriptor read/64, error -71
[17195493.776000] usb 1-3: reset high speed USB device using ehci_hcd and address 40
[17195493.796000] usb 1-3: device descriptor read/8, error -71
[17195493.916000] usb 1-3: device descriptor read/8, error -71
[17195494.132000] usb 1-3: reset high speed USB device using ehci_hcd and address 40
[17195494.540000] usb 1-3: device not accepting address 40, error -71
[17195494.540000] usb 1-3: USB disconnect, address 40
[17195494.652000] usb 1-3: new high speed USB device using ehci_hcd and address 41
[17195494.764000] usb 1-3: device descriptor read/64, error -71
[17195494.980000] usb 1-3: device descriptor read/64, error -71
[17195495.196000] usb 1-3: new high speed USB device using ehci_hcd and address 42
[17195495.328000] usb 1-3: device descriptor read/all, error -71
[17195495.444000] usb 1-3: new high speed USB device using ehci_hcd and address 43
[17195495.852000] usb 1-3: device not accepting address 43, error -71
[17195495.964000] usb 1-3: new high speed USB device using ehci_hcd and address 44
[17195496.372000] usb 1-3: device not accepting address 44, error -71
[17195526.592000] usb 1-3: new high speed USB device using ehci_hcd and address 45
[17195526.704000] usb 1-3: device descriptor read/64, error -71
[17195526.920000] usb 1-3: device descriptor read/64, error -71
[17195527.136000] usb 1-3: new high speed USB device using ehci_hcd and address 46
[17195527.248000] usb 1-3: device descriptor read/64, error -71
[17195527.464000] usb 1-3: device descriptor read/64, error -71
[17195527.680000] usb 1-3: new high speed USB device using ehci_hcd and address 47
[17195527.904000] usb 1-3: unable to read config index 0 descriptor/start
[17195527.904000] usb 1-3: can't read configurations, error -71
[17195528.020000] usb 1-3: new high speed USB device using ehci_hcd and address 48
[17195528.428000] usb 1-3: device not accepting address 48, error -71
[17195537.932000] usb 1-3: new high speed USB device using ehci_hcd and address 49
[17195538.064000] usb 1-3: unable to read config index 0 descriptor/all
[17195538.064000] usb 1-3: can't read configurations, error -71
[17195538.180000] usb 1-3: new high speed USB device using ehci_hcd and address 50
[17195538.292000] usb 1-3: device descriptor read/64, error -71
[17195538.508000] usb 1-3: device descriptor read/64, error -71
[17195538.724000] usb 1-3: new high speed USB device using ehci_hcd and address 51
[17195539.132000] usb 1-3: device not accepting address 51, error -71
[17195539.244000] usb 1-3: new high speed USB device using ehci_hcd and address 52
[17195539.652000] usb 1-3: device not accepting address 52, error -71
[17198180.404000] usb 1-3: new high speed USB device using ehci_hcd and address 53
[17198180.516000] usb 1-3: device descriptor read/64, error -71
[17198180.732000] usb 1-3: device descriptor read/64, error -71
[17198180.948000] usb 1-3: new high speed USB device using ehci_hcd and address 54
[17198181.060000] usb 1-3: device descriptor read/64, error -71
[17198181.276000] usb 1-3: device descriptor read/64, error -71
[17198181.492000] usb 1-3: new high speed USB device using ehci_hcd and address 55
[17198181.900000] usb 1-3: device not accepting address 55, error -71
[17198182.012000] usb 1-3: new high speed USB device using ehci_hcd and address 56
[17198182.420000] usb 1-3: device not accepting address 56, error -71
[17198281.960000] usb 1-3: new high speed USB device using ehci_hcd and address 57
[17198282.072000] usb 1-3: device descriptor read/64, error -71
[17198282.288000] usb 1-3: device descriptor read/64, error -71
[17198282.504000] usb 1-3: new high speed USB device using ehci_hcd and address 58
[17198282.616000] usb 1-3: device descriptor read/64, error -71
[17198282.832000] usb 1-3: device descriptor read/64, error -71
[17198283.048000] usb 1-3: new high speed USB device using ehci_hcd and address 59
[17198283.456000] usb 1-3: device not accepting address 59, error -71
[17198283.568000] usb 1-3: new high speed USB device using ehci_hcd and address 60
[17198283.976000] usb 1-3: device not accepting address 60, error -71
[17198285.488000] usb 1-3: new high speed USB device using ehci_hcd and address 61
[17198285.600000] usb 1-3: device descriptor read/64, error -71
[17198285.816000] usb 1-3: device descriptor read/64, error -71
[17198286.032000] usb 1-3: new high speed USB device using ehci_hcd and address 62
[17198286.144000] usb 1-3: device descriptor read/64, error -71
[17198286.360000] usb 1-3: device descriptor read/64, error -71
[17198286.576000] usb 1-3: new high speed USB device using ehci_hcd and address 63
[17198286.984000] usb 1-3: device not accepting address 63, error -71
[17198287.096000] usb 1-3: new high speed USB device using ehci_hcd and address 64
[17198287.504000] usb 1-3: device not accepting address 64, error -71

```

---

