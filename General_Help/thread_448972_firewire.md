---
title: "firewire???"
date: 2007-05-19
forum: General Help
---

### Post by pugs on 2007-05-19
I am trying to follow a guide to setup my firewire card to connect to my comcast digital cable box.

This is what I am getting:

pugs@mythbox:/dev$ sudo plugreport
raw1394 - couldn't get handle: No such file or directory
This error usually means that the raw1394 driver is not loaded or that /dev/raw1394 does not exist.
pugs@mythbox:/dev$

I have been searching around trying to find some info on this but everything I find seems like they have already solved this problem and are on to other problems later on...LOL

---

### Post by bettlebrox on 2007-05-19
Have you loaded the raw1394 module?

---

### Post by voltagex on 2007-05-19
try
> sudo modprobe raw1394

---

### Post by pugs on 2007-05-20
Sorry, I am an idiot.  I finally found this page which helped greatly:

[http://www.mythtv.org/wiki/index.php/FireWire](http://www.mythtv.org/wiki/index.php/FireWire)

I did not have the raw1394 in the modules file.

No I have other issues...my comcast box doesnt seem to want to talk.  It seems as though both of its firewire ports work, but I cant get a P2P or Broadcast connection :(

---

