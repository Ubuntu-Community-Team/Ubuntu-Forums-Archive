---
title: "tascorp 17a1 webcam"
date: 2008-06-18
forum: General Help
---

### Post by chedog on 2008-06-18
I have a tascorp 17a1 webcam and have searched everywhere but cannot find drivers that work for it. can anyone please help

---

### Post by linuxwizard on 2008-06-18
Post the results of the command > lsusb

---

### Post by chedog on 2008-06-18
Bus 002 Device 001: ID 0000:0000
Bus 001 Device 006: ID 04e8:326c Samsung Electronics Co., Ltd
Bus 001 Device 004: ID 17a1:0128
Bus 001 Device 003: ID 058f:9254 Alcor Micro Corp. Hub
Bus 001 Device 001: ID 0000:0000

---

### Post by linuxwizard on 2008-06-18
Your webcam > ID 17a1:0128 > looks like the driver is under development. You can look over these links and decide if you want to try the driver or wait for final release.

[http://article.gmane.org/gmane.linux.drivers.spca50x.devel/2946](http://article.gmane.org/gmane.linux.drivers.spca50x.devel/2946)

[http://sourceforge.net/mailarchive/forum.php?forum_name=spca50x-devs](http://sourceforge.net/mailarchive/forum.php?forum_name=spca50x-devs)

---

### Post by MarkMissesWindowsNOT on 2008-08-24
I have the same webcam. Can you tell me what to do once I get to  [http://article.gmane.org/gmane.linux.drivers.spca50x.devel/2946](http://article.gmane.org/gmane.linux.drivers.spca50x.devel/2946)

Much Aprreciated

Mark

---

### Post by Crafty Kisses on 2008-08-25
> **chedog said:**
> I have a tascorp 17a1 webcam and have searched everywhere but cannot find drivers that work for it. can anyone please help

The drivers are in development, which means you're gonna have to wait on the drivers.

In the meantime to say if MAYBE your webcam might work, try the following:

Open Ekiga and see if the webcam works/detected. You may have to work with the settings > Open Ekiga > Edit > Preferences > Devices > Video Devices > try changing some of the settings. (try both V4L and V4L2)

To test your webcam you can do this:
There are 6 icons on the left side of the main Ekiga window. Push the 4th button from the top (a grey round webcam). If eveything is ok, you'll see the output of the webcam. If not, you'll see the Ekiga logo bouncing slowly.

---

