---
title: "How to install Packet Tracer when there is 2 dependency required in Ubuntu 19.10?"
date: 2020-02-05
forum: General Help
---

### Post by pranav.bhattarai on 2020-02-05
I can't seem to install **Packet Tracer.** I tried multiple times.  It's my **7th** day of the CCNA lab. I already missed a day not installing this software. I don't want to miss what will happen tomorrow.

```

pranav@Exam &#57520; ~/Downloads &#57520; sudo dpkg -i PacketTracer_730_amd64.deb                          
Selecting previously unselected package packettracer.
(Reading database ... 242419 files and directories currently installed.)
Preparing to unpack PacketTracer_730_amd64.deb ...
Unpacking packettracer (7.3.0) ...
dpkg: dependency problems prevent configuration of packettracer:
 packettracer depends on libdouble-conversion1; however:
  Package libdouble-conversion1 is not installed.
 packettracer depends on qt-at-spi; however:
  Package qt-at-spi is not installed.

dpkg: error processing package packettracer (--install):
 dependency problems - leaving unconfigured
Processing triggers for gnome-menus (3.32.0-1ubuntu1) ...
Processing triggers for desktop-file-utils (0.24-1ubuntu1) ...
Processing triggers for mime-support (3.63ubuntu1) ...
Processing triggers for shared-mime-info (1.10-1) ...
Errors were encountered while processing:
 packettrace

```

Running: **sudo apt install -f **will uninstall/remove packettracer. I am running out of options. Please help me.

---

### Post by wildmanne39 on 2020-02-05
*Thread moved to **General Help a more appropriate sub-forum**.*

---

### Post by deadflowr on 2020-02-05
Neither of the dependencies listed are available in 19.10.
They are available in 18.04, though.

---

