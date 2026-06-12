---
title: "X Errors and unable to Log In"
date: 2007-04-28
forum: General Help
---

### Post by el33tcapitan on 2007-04-28
During an attempt to get Beryl working on my Dell Inspiron E1505 with ATI Mobility X1400, my computer froze and I had to do a hard reboot. After that reboot, the X server was predictably wonky and refused to start up, feeding the error message "No Screens Found." I tried running "dpkg-reconfigure xserver-xorg" to reconfigure the X server, but neither the ati nor the vesa drivers would work. When using ati as the drivers I get the "No screens found" errors while using the vesa drivers yields "Fatal Server error: Caught signal 11. Server aborting."

To attempt to correct this somehow I even tried booting to a live CD, but even the live CD was unable to initialize the X server.

Any help would be greatly appreciated.

---

### Post by el33tcapitan on 2007-04-28
Fixed. Had to re-download fglrx drivers.

---

