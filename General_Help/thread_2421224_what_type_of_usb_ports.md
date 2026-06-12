---
title: "what type of usb ports?"
date: 2019-06-18
forum: General Help
---

### Post by old-nomad on 2019-06-18
Could someone tell me how i can find out what type of usb ports i have on my desktop computer.

---

### Post by CatKiller on 2019-06-18
The only reliable method is to read the manual.

There are conventions for colouring and labelling, but manufacturers just do their own thing.

---

### Post by kpatz on 2019-06-18
What make and model of desktop computer?  Or if you built it, what motherboard does it have?

Specs should be available online.

---

### Post by TheFu on 2019-06-18
> **old-nomad said:**
> Could someone tell me how i can find out what type of usb ports i have on my desktop computer.

If you need to do it remotely, here's a desktop ```

$ lsusb -t
/:  Bus 04.Port 1: Dev 1, Class=root_hub, Driver=xhci_hcd/4p, 5000M
/:  Bus 03.Port 1: Dev 1, Class=root_hub, Driver=xhci_hcd/4p, 480M
/:  Bus 02.Port 1: Dev 1, Class=root_hub, Driver=xhci_hcd/4p, 10000M
/:  Bus 01.Port 1: Dev 1, Class=root_hub, Driver=xhci_hcd/10p, 480M
    |__ Port 6: Dev 2, If 0, Class=Human Interface Device, Driver=usbhid, 1.5M
    |__ Port 6: Dev 2, If 1, Class=Human Interface Device, Driver=usbhid, 1.5M
```
This shows shows 4 "bus"es.  
> 01 - USB2
02 - USB 3.1
03 - USB2
04 - USB 3.0

The 1.5M listed devices are USB mouse and keyboard connections.  I put them specifically on the USB2 port. Don't want to use a faster bus if the device can't make use of the higher bandwidth.

But I know there are many more ports on the system and I know there are some USB headers that are not connected to the case from the motherboard.
 
As  CatKiller says, we have to look at the ports and hope they are wired correctly.  If you have a USB 3.1 storage device, you could connect it to each port and run lsusb to see what speed it shows.  

Here's the best image I could find for the different color codes, but all black ports could be any speed.[URL="https://www.sweetwater.com/sweetcare/media/2019/03/USB-Connections.png"]
image with usb color codes.[/URL]

A laptop:
```
$ lsusb -t
/:  Bus 02.Port 1: Dev 1, Class=root_hub, Driver=xhci_hcd/6p, 5000M
    |__ Port 1: Dev 5, If 0, Class=Hub, Driver=hub/4p, 5000M
        |__ Port 1: Dev 6, If 0, Class=Vendor Specific Class, Driver=ax88179_178a, 5000M
/:  Bus 01.Port 1: Dev 1, Class=root_hub, Driver=xhci_hcd/12p, 480M
    |__ Port 1: Dev 8, If 0, Class=Hub, Driver=hub/4p, 480M
    |__ Port 6: Dev 3, If 0, Class=Video, Driver=uvcvideo, 480M
    |__ Port 6: Dev 3, If 1, Class=Video, Driver=uvcvideo, 480M
    |__ Port 8: Dev 4, If 1, Class=Wireless, Driver=, 12M
    |__ Port 8: Dev 4, If 0, Class=Wireless, Driver=, 12M

```
It has 2 physical external ports - USB2 and USB3.  What are all the others?  Laptops use USB connections internally for the keyboard, touchpad, SDHC slot, webcam, wifi, .... We can see from the output above that these all share a single Bus 01, so combined, they are limited to 480Mbps, in theory.  In reality, 80% of that would be expected.
Notice Bus 02 has a hub connected which is showing a driver, ax88179... . That's a GigE network device using the USB3 speed. This laptop doesn't have an ethernet port, so I added one via USB3.

The announced port speed has little to do with the real throughput possible, though it definitely is a cap.

---

