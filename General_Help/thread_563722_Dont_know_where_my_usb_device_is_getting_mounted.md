---
title: "Dont know where my usb device is getting mounted"
date: 2007-09-30
forum: General Help
---

### Post by punitrathore on 2007-09-30
hi, 

i have this modem which for which i have installed the drivers correctly, but i dont know where the device is getting mounted.

The 'lsusb' command gives the following output.
Bus 005 Device 001: ID 0000:0000
Bus 001 Device 003: ID 0a12:0001 Cambridge Silicon Radio, Ltd Bluetooth Dongle (HCI mode)
Bus 001 Device 001: ID 0000:0000
Bus 004 Device 001: ID 0000:0000
Bus 003 Device 001: ID 0000:0000
Bus 002 Device 002: ID 06e0:f111 Multi-Tech Systems, Inc.
Bus 002 Device 001: ID 0000:0000


The 'Multi-tech systems, inc' is my modem. Is there a way to know where it is getting mounted??
Thanks in advance.

---

### Post by geraldm on 2007-09-30
A standard practice is to place the name of the device in the log.  /var/log/syslog

If you have a file /proc/bus/usb/devices then a driver may be shown for the device
when a module drives the device; 
Module cdc_acm may use /dev/ttyACMx (x is a number from 0 to 15)
and file /var/log/syslog would have lines like this:

cdc_acm 2-1:2.0: ttyACM0: USB ACM device
usbcore: registered new interface driver cdc_acm

The /sys filesystem entry can then be identified by using the find command:

% find /sys -name 'ttyACM0' -print
/sys/class/tty/ttyACM0
/sys/devices/pci0000:00/0000:00:10/1.2/usb2/2-1/2-1:2.0/ttyACM0

Gerald

---

### Post by punitrathore on 2007-10-01
hey gerald.. thanks for your prompt reply!

As you said i looked at the /var/log/syslog file and it had the foll lines.. 

     new full speed USB device using uhci_hcd and address 13  
     usb 2-1: configuration #1 chosen from 2 choices
    <debug info>^I[1191262985.178763] nm_hal_device_added (): New device added (hal udi is'/org/freedesktop/Hal/devices/usb_device_6e0_f111_noserial').
    ti_usb_3410_5052 2-1:1.0: TI USB 3410 1 port adapter converter detected
    ti_usb_3410_5052: probe of 2-1:1.0 failed with error -5
    usb 2-1: device_add(2-1:1.0) --> -5

Does this mean that the drivers arent installed properly or am i missing something??

-punit-

---

### Post by geraldm on 2007-10-01
-5 is an Input/Output error.   Try switching the device to different hub ports or plug it 
in as the only device on a root port.  The device would not show up if there is a -5 error.

Gerald

---

### Post by punitrathore on 2007-10-02
i tried plugging it into all of  the ports and i still get the same error.
What exactly is a root port and how do i know which one is a root port?

---

### Post by geraldm on 2007-10-02
A root port would be one on the computer case, and not any port which is on an external 
hub.  If the file /proc/bus/usb/devices for the device is examined, the line
"T:  Bus=02 Lev=01"
shows lev=00 for a root port, and any device plugged into this port would be level 01.
For some computers, there may be ports showing at level 01, and this would not be a
root port.

The point is to place the device as close to the root as possible, and not have any other
devices plugged in to the same level.  This is to eliminate any chance of interference by
any other device.
If you have tried this and no other devices were at the same level on that bus number,
then the device is not going to work.

Gerald

---

