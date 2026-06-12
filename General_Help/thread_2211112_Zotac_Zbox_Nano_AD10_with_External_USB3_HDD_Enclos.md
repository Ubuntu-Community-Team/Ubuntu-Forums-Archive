---
title: "Zotac Zbox Nano AD10 with External USB3 HDD Enclosure woes"
date: 2014-03-14
forum: General Help
---

### Post by butters12 on 2014-03-14
Hi all, as the title states, I have these two devices.  I was using the hard drives with the Zotec Nano PC formatted in windows with no issue, but I can't get the hard drives to detect in Ubuntu 12.04 Server LTS!  When I plug the enclosure in, no disks show in fdisk or lsblk.  The dmesg | tail contains:

```
[  208.214809] usb 8-1: new high-speed USB device number 2 using xhci_hcd[  208.214987] usb 8-1: Device not responding to set address.
[  208.418728] usb 8-1: Device not responding to set address.
[  208.622592] usb 8-1: device not accepting address 2, error -71
```

I am running kernel 3.11.0.15-generic with pretty much a fresh install - no options installed (I planned on building it up from scratch, just the basics, SSH, Samba and Plex Media Server).

I have done a bit of searching, some people having similar issues were able to fix it by turning off autosuspend in usbcore (didn't work for me).  Others suggested just unplugging everything and letting it sit unpowered for five minutes to eliminate any excess charge on the USB ports (didn't work for me).  Finally, I saw a post that fixed a similar issue with by setting the 'Old Scheme First' to true and re-connect the enclosure.  When I did this I got:

```
[  231.886995] hub 9-0:1.0: Cannot enable port 1.  Maybe the USB cable is bad?[  549.623870] usb 8-1: new high-speed USB device number 4 using xhci_hcd
[  549.646637] usb 8-1: New USB device found, idVendor=152d, idProduct=0551
[  549.646653] usb 8-1: New USB device strings: Mfr=1, Product=2, SerialNumber=5
[  549.646662] usb 8-1: Product: USB to ATA/ATAPI Bridge
[  549.646671] usb 8-1: Manufacturer: JMicron
[  549.646679] usb 8-1: SerialNumber: 5D3C6AFFFFFF
[  549.649589] usb-storage 8-1:1.0: USB Mass Storage device detected
[  549.649828] scsi7 : usb-storage 8-1:1.0
[  549.654163] usb 8-1: USB disconnect, device number 4
```

So it seems to detect the enclosure but then disconnects for some reason?  If I plug the enclosure into my Macbook, it is detected and mounted with no issue.
 
I am reaching my wits end here, I am a relatively inexperienced linux user.  Is it a driver issue?  Where would I find the right driver?

---

### Post by phidia on 2014-03-14
In a brief search on the last line of the terminal output you provided I saw some posts that suggested that the usb bus didn't have enough power to support the drive. Although I see you say it worked with windows so this is mostly guessing. You might still try with external power provided you can power those drives externally. Just a thought...

---

