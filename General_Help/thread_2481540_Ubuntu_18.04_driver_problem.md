---
title: "Ubuntu 18.04 driver problem"
date: 2022-12-02
forum: General Help
---

### Post by ygzm75 on 2022-12-02
hello, I installed ubuntu 18.04 on my OMEN by HP Laptop 16-b1003nt, but no drivers seem to be installed.


Wifi not found
Bluetooth not found


No drivers are showing, including my video card. when I try to install it, I suddenly see a black screen and it stays on stopping user manager for UID 121.

---

### Post by TheFu on 2022-12-02
18.04 standard support ends in about 3 months.  It isn't the time to be installing that release anywhere.
Today, either 20.04 or 22.04 should be installed.
I don't know the era of the machine involved, but if it is newer than 2018, you'll want a newer release to get driver support for new hardware.  Google says it was released in May 2022 ... welcome to the bleeding edge, dude.  I wait at least a year to get any new hardware, so the driver support can be in place for me.  Live and learn.

If the machine is less than a year old, you'll probably need 22.10 to get the latest HW support which isn't an LTS release.  You might be able to load 22.04.1 and get most of the new hardware support.

BTW, wifi chips are changing all the time, so while 95% of us are handled fine, the systems with the newest chips don't have support and you'll need to find and build the drivers yourself.  It becomes a bit of a chicken/egg issue and will last until the kernel ships with the driver needed.

BT really shouldn't be used by anyone who cares about security at all.

---

