---
title: "Download waypoints and tracks from Garmin GPS unit"
date: 2013-12-03
forum: General Help
---

### Post by BigBaka on 2013-12-03
A couple of years ago I made a post on these forums about this, but having upgraded several times, I forgot how I did this. I have a handheld GPS unit that I would like to get the waypoint data off via usb cord. I've tried Viking, GPSPrune and also QLandkarte GT, I have GPS babel installed but still I cannot get the software to recognise the GPS unit in order to download the data onto my desktop. Has anyone actually been able to get waypoint data off a garmin gps unit on a native ubuntu software package?

Regards,
BB
Ubuntu 12.04 64 bit - Garmin GPS 60

---

### Post by rclocher3 on 2013-12-03
I haven't tried on Ubuntu, but I have fiddled with GPSBabel on a different OS.  Does your GPS use a serial port or a USB port?  If it's a serial port, what protocol do you have it set to use?  I seem to remember that GPSBabel prefers the Garmin protocol, rather than the NMEA protocol.

When I'm dealing with a problem like that I like to determine if it's a hardware problem or a software problem.  You might try talking to the GPS using Google Earth or GPSBabel with a different computer (perhaps running a different OS, horrors) to see if that works; if it does, your problem might be software.  If you can't download from your GPS to another computer, then your gremlin is probably hardware-related.  On my GPS with a serial connection it's easy to get the cable on backwards, which causes the connection to fail every time.  Do you have fresh batteries in the GPS?

- Rob

---

### Post by rclocher3 on 2013-12-03
Ah, sorry, I just re-read your post and I see that you have a GPS 60 with a USB cable.

---

### Post by BigBaka on 2013-12-04
Actually I've already tried to troubleshoot the GPS unit too. Successfully downloaded waypoints via a Windows machine. Just looking for an Ubuntu option.

---

### Post by rclocher3 on 2013-12-04
You couldn't get GPSBabel to work?  I've been able to make it work on Windows, and I'm pretty sure that it was originally written for Linux.

---

### Post by BigBaka on 2013-12-06
Well I did have a play around with GPS Babel and eventually got it to work to an extent, but it is pretty bad. Firstly an error comes up when downloading from the gps to say that the gmapbase.html is missing. Seems there is some bug in the installation and the gmapbase.html file is not included in the installation. 
[http://osdir.com/ml/ubuntu-bugs/2012-06/msg27810.html](http://osdir.com/ml/ubuntu-bugs/2012-06/msg27810.html)

But more than that, when I download, it simply downloads everything. And for the tracks it is quite buggy and I can't select individual tracks on the active log. Every active log track is under the same attribute table when I import into GIS software. There must be something better. 

I've been looking around and it seems that the problem is something to do with the permissions on accessing the GPS unit itself. GPS babel does in as a superuser. But it seems there may also be ways to edit the GPS unit so that it doesn't have to be accessed as a superuser. I'll post here if I find something.

---

