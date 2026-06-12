---
title: "Palm Zire72, No ttyUSB in dev, not syncing"
date: 2007-07-26
forum: General Help
---

### Post by gimfred on 2007-07-26
Okay, two nights ago I synced my palm, and was happy. Today, I went to install a pdf on it and it wouldn't sync! I have installed software, but it was compiz and kvm software, plus updates. (I'm not sure what has been updated over the past two days.)

```
XXXX@XXXXXXXXX:~$ ls /dev/ttyUSB*
ls: /dev/ttyUSB*: No such file or directory
``` 

```
XXXXXX@XXXXXXXX:~$ lsmod | grep usb
usb_storage            80448  1
libusual               22184  1 usb_storage
usblp                  16768  0
usbhid                 29088  0
hid                    34048  1 usbhid
usbcore               154416  7 usb_storage,libusual,usblp,usbhid,uhci_hcd,ehci_hcd
scsi_mod              166968  4 sg,sd_mod,usb_storage,libata
```
Under /sys/bus/usb/devices/ a file keeps starting/altering /sys/bus/usb/devices/usb2, /sys/bus/usb/devices/2-1:1.0 & /sys/bus/usb/devices/2-1

I am unsure how to proceed to get back USB* in /dev/...

When I use ```
tail -f /var/log/messages
```
with the palm off, I get:
```

Jul 26 16:25:59 gimfred-desktop kernel: [ 5714.272234] usb 2-1: new full speed USB device using uhci_hcd and address 19
Jul 26 16:25:59 gimfred-desktop kernel: [ 5714.443763] usb 2-1: configuration #1 chosen from 1 choice
Jul 26 16:26:03 gimfred-desktop kernel: [ 5717.805409] usb 2-1: USB disconnect, address 19
```
with it on I get:
```
Jul 26 16:25:59 gimfred-desktop kernel: [ 5714.272234] usb 2-1: new full speed USB device using uhci_hcd and address 19
Jul 26 16:25:59 gimfred-desktop kernel: [ 5714.443763] usb 2-1: configuration #1 chosen from 1 choice
Jul 26 16:26:03 gimfred-desktop kernel: [ 5717.805409] usb 2-1: USB disconnect, address 19
Jul 26 16:33:37 gimfred-desktop kernel: [ 6171.046524] usb 2-1: new full speed USB device using uhci_hcd and address 20
Jul 26 16:33:37 gimfred-desktop kernel: [ 6171.221800] usb 2-1: configuration #1 chosen from 1 choice
Jul 26 16:33:38 gimfred-desktop kernel: [ 6172.567589] usb 2-1: USB disconnect, address 20
Jul 26 16:33:43 gimfred-desktop kernel: [ 6177.082824] usb 2-1: new full speed USB device using uhci_hcd and address 21
Jul 26 16:33:43 gimfred-desktop kernel: [ 6177.256888] usb 2-1: configuration #1 chosen from 1 choice
Jul 26 16:33:44 gimfred-desktop kernel: [ 6178.603892] usb 2-1: USB disconnect, address 21
```
so it is being seen.

---

### Post by Dougga on 2008-01-05
I have the identical problem. I've posted on here but received no response.  The interesting point is three days ago it worked fine and I got the creation of the ttyUSB1 & 2 devices when I plugged in my Treo.  Now they're not created.  

The only think I can think of is some update has killed the synchronization with Palms.

sorry no help... I'm still looking.:(

---

### Post by jhipkiss on 2008-01-30
Have you tried this page, it worked for me and my symtoms were identical to yours?

[https://help.ubuntu.com/community/PalmDeviceSetup](https://help.ubuntu.com/community/PalmDeviceSetup)

Jonathan

---

### Post by gimfred on 2008-02-14
Thanks jhipkiss. I remember trying a page like this back in July, but it didn't work. It is currently backing up the zire now. :)

---

### Post by aonegodman on 2008-03-29
Thanks to all. I just tried to SYNC my old Palm Zire to Gutsy via USB cable. After the reads and finding that I had a "Palm O/S Devices" under "System > Preferences >" I began to attack the no link problem.

Here's what finally worked for me -

I used the default settings under gnome-pilot except I had to change the dev setting to ttyUSB1 and then was able to sink.

Hope this helps someone else.   :)

---

