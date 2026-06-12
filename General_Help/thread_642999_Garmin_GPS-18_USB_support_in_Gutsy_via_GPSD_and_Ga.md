---
title: "Garmin GPS-18 USB support in Gutsy via GPSD and Garmin kernel module"
date: 2007-12-17
forum: General Help
---

### Post by LarryJ2 on 2007-12-17
Support for the Garmin USB GPS-18 puck exists in Gutsy 7.10.

In a terminal window

******$ sudo modprobe garmin_gps.ko******
Wrong! Should be 
$sudo modprobe garmin_gps


then to test, plug in your usb garmin gps18 puck.  /dev/ttyUSB0 should appear

$ ls -al /dev/ttyUSB0
crw-rw---- 1 root dialout 188, 0 2007-12-24 08:21 /dev/ttyUSB0

Next you may have to load the USBFS as noted below by Moonstone

$ sudo mount -t usbfs none /proc/bus/usb/ 

next

$ sudo gpsd -nND4 /dev/ttyUSB0

should  start test messages streaming line after line in your terminal window.

If you have installed the package  gps-clients,  you can also test with  
$ sudo killall gpsd
$ sudo gpsd /dev/ttyUSB0 

then 

$ xgps
or
$ cgps

To find the location of the kernel module and other iterations of gps stuff, try
$ locate garmin
and
$ locate gpsd

---

### Post by moonstone on 2007-12-23
Not working.

$ sudo modprobe garmin_gps.ko
FATAL: Module garmin_gps.ko not found.

But if i try without .ko module garmin_gps gets loaded

then

$ sudo gpsd -nND4 /dev/ttyUSB0
gpsd: launching (Version 2.34)
gpsd: listening on port gpsd
gpsd: shmat(0,0,0) succeeded
gpsd: shmat(0,0,0) succeeded
gpsd: shmat(0,0,0) succeeded
gpsd: shmat(0,0,0) succeeded
gpsd: successfully connected to the DBUS system bus
gpsd: running with effective group ID 0
gpsd: running with effective user ID 0
gpsd: opening GPS data source at '/dev/ttyUSB0'
gpsd: speed 9600, 8N1
**gpsd: Can't open /proc/bus/usb/devices** <- device missing?!
gpsd: no probe matched...
gpsd: gpsd_activate(1): opened GPS (5)

and xgps shows absolutely nothing :(

Please help!

---

### Post by moonstone on 2007-12-23
Oh...

[https://bugzilla.novell.com/show_bug.cgi?id=232097](https://bugzilla.novell.com/show_bug.cgi?id=232097)
mount -t usbfs none /proc/bus/usb/

and garmin works! :)

---

