---
title: "USB Device - Change/Assign driver"
date: 2012-12-14
forum: General Help
---

### Post by Hoosier205 on 2012-12-14
I have a USB device (a display colorimeter for calibration) that I need to get working. I have the drivers, but I do not know how to assign them to the device. 

I am not very good at working within Ubuntu yet, but here is the info I have:

Bus 001 Device 002: ID 0bda:0158 Realtek Semiconductor Corp. USB 2.0 multicard reader
Bus 002 Device 002: ID 5986:0180 Acer, Inc 
Bus 005 Device 003: ID 085c:0300 ColorVision, Inc. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

The ColorVision, Inc. device is the one I am talking about.

---

### Post by slickymaster on 2012-12-14
As root type:
```
echo $usbid > /sys/bus/usb/drivers/usb-storage/bind
``` 
It will bind the USB device with $usbid from the "usb-storage" driver.

Take a look at this [LWN article]("http://lwn.net/Articles/143397/") on manual driver binding and unbinding, it's extremely thorough and explanatory.

---

### Post by Hoosier205 on 2012-12-14
Oh boy...I'm confused. Sorry. 

How does it know which drivers to bind to that particular device?

I have the drivers (a .cat file and a .inf file) sitting on my desktop currently. Do I put them in the usb-storage folder before running that command?

Also, when I did as you said...I got this:

> -su: echo: write error: No such device

---

### Post by slickymaster on 2012-12-14
First things first, install tree in your machine if you don't already have it:
```
sudo apt-get install tree
```
Now, every driver has bind and unbind files associated with it, so type this command:
```
sudo tree /sys/bus/usb/drivers/
```
And you'll get something like this:
```
&#9500;&#9472;&#9472; btusb
&#9474;** &#9500;&#9472;&#9472; 2-1:1.0 -> ../../../../devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1:1.0
&#9474;** &#9500;&#9472;&#9472; 2-1:1.1 -> ../../../../devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1:1.1
&#9474;** &#9500;&#9472;&#9472; bind
&#9474;** &#9500;&#9472;&#9472; module -> ../../../../module/btusb
&#9474;** &#9500;&#9472;&#9472; new_id
&#9474;** &#9500;&#9472;&#9472; remove_id
&#9474;** &#9500;&#9472;&#9472; uevent
&#9474;** &#9492;&#9472;&#9472; unbind
&#9500;&#9472;&#9472; hub
&#9474;** &#9500;&#9472;&#9472; 1-0:1.0 -> ../../../../devices/pci0000:00/0000:00:1d.7/usb1/1-0:1.0
&#9474;** &#9500;&#9472;&#9472; 2-0:1.0 -> ../../../../devices/pci0000:00/0000:00:1d.0/usb2/2-0:1.0
&#9474;** &#9500;&#9472;&#9472; 3-0:1.0 -> ../../../../devices/pci0000:00/0000:00:1d.1/usb3/3-0:1.0
&#9474;** &#9500;&#9472;&#9472; 4-0:1.0 -> ../../../../devices/pci0000:00/0000:00:1d.2/usb4/4-0:1.0
&#9474;** &#9500;&#9472;&#9472; 5-0:1.0 -> ../../../../devices/pci0000:00/0000:00:1d.3/usb5/5-0:1.0
&#9474;** &#9500;&#9472;&#9472; bind
&#9474;** &#9500;&#9472;&#9472; module -> ../../../../module/usbcore
&#9474;** &#9500;&#9472;&#9472; new_id
&#9474;** &#9500;&#9472;&#9472; remove_id
&#9474;** &#9500;&#9472;&#9472; uevent
&#9474;** &#9492;&#9472;&#9472; unbind
&#9500;&#9472;&#9472; libusual
&#9474;** &#9500;&#9472;&#9472; bind
&#9474;** &#9500;&#9472;&#9472; module -> ../../../../module/usb_libusual
&#9474;** &#9500;&#9472;&#9472; new_id
&#9474;** &#9500;&#9472;&#9472; remove_id
&#9474;** &#9500;&#9472;&#9472; uevent
&#9474;** &#9492;&#9472;&#9472; unbind
&#9500;&#9472;&#9472; uas
&#9474;** &#9500;&#9472;&#9472; bind
&#9474;** &#9500;&#9472;&#9472; module -> ../../../../module/uas
&#9474;** &#9500;&#9472;&#9472; new_id
&#9474;** &#9500;&#9472;&#9472; remove_id
&#9474;** &#9500;&#9472;&#9472; uevent
&#9474;** &#9492;&#9472;&#9472; unbind
&#9500;&#9472;&#9472; usb
&#9474;** &#9500;&#9472;&#9472; 1-4 -> ../../../../devices/pci0000:00/0000:00:1d.7/usb1/1-4
&#9474;** &#9500;&#9472;&#9472; 2-1 -> ../../../../devices/pci0000:00/0000:00:1d.0/usb2/2-1
&#9474;** &#9500;&#9472;&#9472; bind
&#9474;** &#9500;&#9472;&#9472; uevent
&#9474;** &#9500;&#9472;&#9472; unbind
&#9474;** &#9500;&#9472;&#9472; usb1 -> ../../../../devices/pci0000:00/0000:00:1d.7/usb1
&#9474;** &#9500;&#9472;&#9472; usb2 -> ../../../../devices/pci0000:00/0000:00:1d.0/usb2
&#9474;** &#9500;&#9472;&#9472; usb3 -> ../../../../devices/pci0000:00/0000:00:1d.1/usb3
&#9474;** &#9500;&#9472;&#9472; usb4 -> ../../../../devices/pci0000:00/0000:00:1d.2/usb4
&#9474;** &#9492;&#9472;&#9472; usb5 -> ../../../../devices/pci0000:00/0000:00:1d.3/usb5
&#9500;&#9472;&#9472; usbfs
&#9474;** &#9500;&#9472;&#9472; bind
&#9474;** &#9500;&#9472;&#9472; module -> ../../../../module/usbcore
&#9474;** &#9500;&#9472;&#9472; new_id
&#9474;** &#9500;&#9472;&#9472; remove_id
&#9474;** &#9500;&#9472;&#9472; uevent
&#9474;** &#9492;&#9472;&#9472; unbind
&#9492;&#9472;&#9472; [COLOR="Red"]usb-storage
    &#9500;&#9472;&#9472; 1-4:1.0 -> ../../../../devices/pci0000:00/0000:00:1d.7/usb1/1-4/1-4:1.0
    &#9500;&#9472;&#9472; bind
    &#9500;&#9472;&#9472; module -> ../../../../module/usb_storage
    &#9500;&#9472;&#9472; new_id
    &#9500;&#9472;&#9472; remove_id
    &#9500;&#9472;&#9472; uevent
    &#9492;&#9472;&#9472; unbind[/COLOR]
```

To bind a device to a driver, the device must first not be controlled by any other driver. To ensure this, look for the "driver" symlink in the device directory:
(For example for my usb-drive - in red in the tree):
```
sudo tree /sys/bus/usb/devices/1-4:1.0
```
```
|-- bAlternateSetting
    |-- bInterfaceClass
    |-- bInterfaceNumber
    |-- bInterfaceProtocol
    |-- bInterfaceSubClass
    |-- bNumEndpoints
    |-- bus -> ../../../../../../bus/usb
    |-- modalias
    `-- power
        `-- state

```
Then, simply write the bus id of the device you wish to bind, into the bind file for that driver:
```
echo -n "1-4:1.0" > /sys/bus/usb/drivers/usb-storage/bind
```

---

