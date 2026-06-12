---
title: "Finding which USB port does what: low-, high-, and full-speed"
date: 2012-12-09
forum: General Help
---

### Post by Paddy Landau on 2012-12-09
While booting my USB into Recovery Mode, I noticed some text skipping past. There were mentions of three different USB speeds for my four USB ports:

```
usb 1-1.5: new high-speed USB device number 3 using ehci_hcd
usb 1-1.6: new full-speed USB device number 4 using ehci_hcd
usb 2-1.3: new low-speed USB device number 3 using ehci_hcd
usb 2-1.8: new high-speed USB device number 4 using ehci_hcd
```Does this mean that one of my USB ports is low speed (1½Mbit/s), one is full-speed (12Mbit/s) and two are high speed (480Mbit/s)?

If so, how do I tell which USB port is which?

I would like to plug my keyboard and mouse into the low-speed port, my ancient device into the full-speed one, and my modern devices into the two high-speed ones.

**Extra information**

[FONT=Lucida Console]lsusb[/FONT] gives the following information.
```
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 003: ID 04f2:b28b Chicony Electronics Co., Ltd 
Bus 001 Device 004: ID 0408:3003 Quanta Computer, Inc. 
Bus 002 Device 003: ID 046d:c517 Logitech, Inc. LX710 Cordless Desktop Laser
Bus 002 Device 004: ID 0bda:8172 Realtek Semiconductor Corp. RTL8191SU 802.11n WLAN Adapter
Bus 001 Device 005: ID 04e8:1323 Samsung Electronics Co., Ltd 
```[FONT=Lucida Console]lsusb -t[/FONT] gives the following information.
```
/:  Bus 02.Port 1: Dev 1, Class=root_hub, Driver=ehci_hcd/2p, 480M
    |__ Port 1: Dev 2, If 0, Class=hub, Driver=hub/8p, 480M
        |__ Port 3: Dev 3, If 0, Class=HID, Driver=usbhid, 1.5M
        |__ Port 3: Dev 3, If 1, Class=HID, Driver=usbhid, 1.5M
        |__ Port 8: Dev 4, If 0, Class=vend., Driver=r8712u, 480M
/:  Bus 01.Port 1: Dev 1, Class=root_hub, Driver=ehci_hcd/2p, 480M
    |__ Port 1: Dev 2, If 0, Class=hub, Driver=hub/6p, 480M
        |__ Port 1: Dev 5, If 0, Class=stor., Driver=usb-storage, 480M
        |__ Port 5: Dev 3, If 0, Class='bInterfaceClass 0x0e not yet handled', Driver=uvcvideo, 480M
        |__ Port 5: Dev 3, If 1, Class='bInterfaceClass 0x0e not yet handled', Driver=uvcvideo, 480M
        |__ Port 5: Dev 3, If 2, Class=audio, Driver=snd-usb-audio, 480M
        |__ Port 5: Dev 3, If 3, Class=audio, Driver=snd-usb-audio, 480M
        |__ Port 6: Dev 4, If 0, Class=HID, Driver=usbhid, 12M
```

---

### Post by Rebelli0us on 2012-12-09
There is/was an app in Synaptic called "device manager" that shows all devices in treeview-like format. There you can see which devices are plugged in the various USBs.  The app title is a misnomer, it's a device-viewer as it doesn't manage anything. It's handy for setting resume from S3 via keyboard.

---

### Post by Paddy Landau on 2012-12-09
Hmm, I don't find anything like that in Synaptic or in Ubuntu Software Centre.

You have a point, though; there must be a way to find out what is plugged into what. That would give the answer.

But I don't know how to find out this information.

---

### Post by haqking on 2012-12-09
> **Paddy Landau said:**
> Hmm, I don't find anything like that in Synaptic or in Ubuntu Software Centre.

You have a point, though; there must be a way to find out what is plugged into what. That would give the answer.

But I don't know how to find out this information.

Am i missing something ?

Your Wireless is plugged into a High Speed.
Your keyboard is already plugged into a low speed

etc

The lsusb-t tells you whats in what

---

### Post by Paddy Landau on 2012-12-09
> **haqking said:**
> Am i missing something ?
No… it is I who is missing something! I speak from ignorance :(

> **haqking said:**
>  Your Wireless is plugged into a High Speed.
Your keyboard is already plugged into a low speed
Please explain how you know. I've looked and frowned at the output that I posted, but I can't put 2 and 2 together. I'm sure it's quite obvious if you know what you are looking at, but I can't figure it out.

---

### Post by haqking on 2012-12-09
> **Paddy Landau said:**
> No… it is I who is missing something! I speak from ignorance :(


Please explain how you know. I've looked and frowned at the output that I posted, but I can't put 2 and 2 together. I'm sure it's quite obvious if you know what you are looking at, but I can't figure it out.

OK for example:

Port 8: Dev 4, If 0, Class=vend., Driver=r8712u, **480M**

Shows you your wireless device is plugged into a High Speed Device

---

### Post by westie457 on 2012-12-09
As usual when someone posts a normal command with an option I have never heard of, I try it out.

As far as I can work things out the lsusb -t command with nothing connected to USB ports will return the default speed capabilities of the ports and with something connected - eg a mouse - the speed returned will be the speed of the device.

Of course I could be wrong.

---

### Post by Paddy Landau on 2012-12-09
Thank you for your responses.

From what you have said, it looks to me that:

[LIST]
[*]I must have more than four USB ports, but some of them are hidden from me; for example, the wireless seems to be plugged in to a USB port.
[/LIST]

[LIST]
[*]All of the ports probably have the same capability, but they just appear to be different because of what is plugged into them at that particular time.
[/LIST]
Does that seem right? If so, I don't need to bother myself.

---

### Post by haqking on 2012-12-09
> **Paddy Landau said:**
> Thank you for your responses.

From what you have said, it looks to me that:

[LIST]
[*]I must have more than four USB ports, but some of them are hidden from me; for example, the wireless seems to be plugged in to a USB port.
[/LIST]

[LIST]
[*]All of the ports probably have the same capability, but they just appear to be different because of what is plugged into them at that particular time.
[/LIST]
Does that seem right? If so, I don't need to bother myself.

the speeds are listed in /sys/bus/usb/devices/

So if you cat /sys/bus/usb/devices/usb1/speed

It will show you the speed for the the usb1 port. or use "usb?" to list all ports.

such as on mine the output is as follows:

480
480
480
5000
480
5000


Which means port 1,2,3 are high speed, 4 and 6 are USB 3 so 5Gb etc.

But your first ouptut shows you devices connected, your ports are likely to all be at least USB 2.0 I imagine, so the speed shown will be the device, you dont get high speeds keyboards for example

hid means human interface device by the way so refers usually to a keyboard/mouse etc.  You can also do a verbose output with your lsusb for more information. (lsusb -v)

---

### Post by Paddy Landau on 2012-12-09
Thank you; that is most informative.

I think I can mark this thread as solved.

---

