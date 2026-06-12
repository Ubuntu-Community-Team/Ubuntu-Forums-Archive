---
title: "internal error - usr/lib/upower/upowerd"
date: 2014-12-12
forum: General Help
---

### Post by gizzacroggy on 2014-12-12
Hi I have been getting this error upon start up for a long time now and just getting round to trying to fix it. 

It is possible it started when i upgraded to 14.04

usr/lib/upower/upowerd.

i have had quick search on forums and found this link to this patch that might fix it but i dont know what to do with this.

[https://launchpadlibrarian.net/186569634/0001-upowerd-Fix-cleanup-in-up_device_idevice_coldplug-fi.patch](https://launchpadlibrarian.net/186569634/0001-upowerd-Fix-cleanup-in-up_device_idevice_coldplug-fi.patch)

any advice and support will cheer me up on this grey wintery day

thanks

scarlet

---

### Post by fddm on 2015-03-09
Did you get anywhere with this? My desktop is throwing up the same error on startup...

---

### Post by rufiocity on 2015-09-11
Did this happen to occur after connecting an iOS device? I had the same issued but ran this and it solved it

sudo apt-get install libimobiledevice-utils

---

### Post by Randy_Stephens on 2015-10-23
I had the same error while logging in with a connected iOS device.  sudo apt-get install libimobiledevice-utils and a reboot solved my issue.  Thanks so much for the suggestion.

---

### Post by adv0cat3 on 2015-10-26
> **rufiocity said:**
> Did this happen to occur after connecting an iOS device? I had the same issued but ran this and it solved it

sudo apt-get install libimobiledevice-utils

thank you this fixed it for me!

---

### Post by orlandocainelli on 2016-04-12
Hi there! 
I've got the same problem even if I already have libimobile-utils! 
I also have an Iphone 4s and just upgraded to ubuntu 14.04
:) CHeers

---

