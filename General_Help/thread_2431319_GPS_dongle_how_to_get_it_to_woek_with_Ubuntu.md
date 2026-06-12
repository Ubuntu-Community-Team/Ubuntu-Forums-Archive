---
title: "GPS dongle how to get it to woek with Ubuntu"
date: 2019-11-14
forum: General Help
---

### Post by jlh68 on 2019-11-14
I have a G-mouse GPS USB dongle and I want to configure my laptop to use it and show the GPS data.  How do I go about getting it to work?

I can not find any new information on setting up GPS on a Ubuntu laptop.  Some how to's were posted in 2011 or 8 years ago, but not much for newer versions of Ubuntu (18.04 or newer)

---

### Post by HermanAB on 2019-11-15
Well, if a device doesn't work when you plug it in, then it likely means that there is no driver for it, so then you have to improvise.

If you are lucky, then the device uses a serial USB interface, in which case it will show up as /dev/ttyUSBxx and then you can read it with cat or netcat, but you need to know what the port speed is running at, so the first thing to do, is to find the data sheet of the widget.  Some googling should get one.

Then, you need to do something like this:
$ ls /dev/tty*
Look for the widget and note the name e.g ttyUSB0

echo "Set serial port USB0 to 9600N81"
$ stty -F /dev/ttyUSB0 9600
$ stty /dev/ttyUSB0

# Read the data to the terminal window
$ cat /dev/ttyUSB0

GPS serial data is easy to parse.  I've done it with an Arduino: 
[https://www.aeronetworks.ca/2016/08/minimalist-arduino-gps-parser.html](https://www.aeronetworks.ca/2016/08/minimalist-arduino-gps-parser.html)

Also see these:
[https://www.aeronetworks.ca/2015/10/reading-and-parsing-data-from-serial.html](https://www.aeronetworks.ca/2015/10/reading-and-parsing-data-from-serial.html)
[https://www.aeronetworks.ca/2014/10/serial-ports-revisited.html](https://www.aeronetworks.ca/2014/10/serial-ports-revisited.html)

---

### Post by jlh68 on 2019-11-15
I have a VK-162 Notebook USB GPS Navigation Module dongle.  It connect via USB, but does not show when ls /dev/tty* is used in the terminal.  I have downloaded using Synaptic Package Manager the GPSdaemon and GPS clients.  Not sure what else to get.
My dongle does not show when I do lsusb. Other USB devices will show when lsusb is used in CL.

---

### Post by cprofitt on 2019-11-15
I can not speak to your particular module, but I had an old Microsoft USB GPS dongle and it showed up when I did an lsub command. I suspect you do not have a driver as HermanAB said.

That said there are items on sale at Amazon that claim this device works with Linux and only requires gpsd and gpsd-clients. Have you tried installing those?

---

### Post by him610 on 2019-11-16
It may appear as something else. This is what mine looks like:
```

$ lsusb
...
Bus 001 Device 008: ID 067b:2303 Prolific Technology, Inc. PL2303 Serial Port
...
```
I don't believe my Prolific PL2303 needed a specific driver.
In addition to *gpsd*, you may need other programs to support GPS including  *foxtrotgps, gis-gps, gpsbabel, gpscorrelate, gpsd-clients, gpsman, gpx2shp, python-gps.* This list is not all inclusive, there may be others. 
I don't recall having to complete any configuration. It sort of self-configures when it is installed.  FoxtrotGPS is the program that shows where you are, and surrounding area.
You also might want to check out [http://opengps.org/]("http://opengps.org/") which has some good information about GPS.

---

