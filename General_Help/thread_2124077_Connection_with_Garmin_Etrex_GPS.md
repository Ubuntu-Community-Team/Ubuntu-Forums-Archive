---
title: "Connection with Garmin Etrex GPS"
date: 2013-03-09
forum: General Help
---

### Post by tulioportilho on 2013-03-09
Hi,

I use Ubuntu 12.10. I have a GPS (Garmin Etrex 30) that I use to record my flights into track logs. The only software for Linux that can download valid track logs is called GPS Dump. It is downloadable here: [http://www.gethome.no/stein.sorensen/](http://www.gethome.no/stein.sorensen/)

There was a lot of tricks I used to make it work. For those who are having problems, this link is very useful: [http://wiki.openstreetmap.org/wiki/USB_Garmin_on_GNU/Linux](http://wiki.openstreetmap.org/wiki/USB_Garmin_on_GNU/Linux)

However, I am still having problems most of the times I try to download a new log. The error that I get from gpsdump is:
"Product data request response timeout"

Explaining what I already did:

In the last link, it explains how to create a new udev rule so that the device file is created with the right permissions. I put it MODE = 666. Also, it says this: 
"Much of the software that reads the current position from GPS devices does so via [gpsd]("http://wiki.openstreetmap.org/wiki/Making_Tracks_with_Homebrew-ware#Gpsd").  gpsd is a daemon that understands various protocols used by GPS devices  and presents a consistent interface that other applications such as [Gpsdrive]("http://wiki.openstreetmap.org/wiki/Gpsdrive") and [TangoGPS]("http://wiki.openstreetmap.org/wiki/TangoGPS")  can use. To use a Garmin USB device with gpsd, you will need to use the  garmin_gps kernel module, or trick gpsd into reading NMEA data from  gpsbabel."

I did the first: I loaded the garmin_gps module (also following instructions from the page).

Then, I could sometimes load the log files from the GPS. But, as I said, most times I get the message: "Product data request response timeout", and nothing happens.

I don't know practically anything about the communication between  external devices and Ubuntu. Assuming GPS Dump uses this "daemon" (?) gpsd, maybe the right thing to do is to configure this daemon, but I don't have a clue about how to do it. I found this about gpsd: [http://catb.org/gpsd/installation.html](http://catb.org/gpsd/installation.html) . In the very first test (stty -F /dev/ttyUSB0 ispeed 4800 && cat </dev/ttyUSB0), to know if Ubuntu can get data from the GPS, it failed.

Can anyone help me?

---

### Post by tulioportilho on 2013-03-16
What can I do to make this thread be noticed?

---

