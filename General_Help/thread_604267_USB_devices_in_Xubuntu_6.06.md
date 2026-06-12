---
title: "USB devices in Xubuntu 6.06"
date: 2007-11-05
forum: General Help
---

### Post by jamesr on 2007-11-05
Hi, 

I am using Xubuntu 6.06 on a file server file but I would like to add an external USB HD. I have installed a PCI USB controller card and seems to be recognised. I seem to have 2 problems :-

1)  only some of the USB connectors on the card work. I seem to have 3 ports whereas the card has 4 external connectors and 1 internal. I use one of the external connectors no USB keys are seen whereas  they are seen on others. Any comments please.

2) I can see the devices  with
```
lsusb
or
cat /proc/bus/usb/devices
```
but ultimatedly I would like to add an external HD. When using a USB key what devices are they setup as. I have seen information about ```
apt-get install sg3
```
 but this addition  seems to change all devices to SCSI devices but my current storeage devices are already SCSI so does that mean that they will also change from sd devices to sg devices, so does that mean I will have to change the way the system boots.
I would prefer not make  major changes likethis  to a running file server just in case all standard operations stop. Comments please


Update
 The problem may be related to problem (1) ie not all ports working, correctly!! after changing devices, some of the devices work in  some of the ports , but the port that I used originally no devices are seen. Again any comments

I will be purchasing an external HD or enclosure to try the next stage ie using an external HD.

---

