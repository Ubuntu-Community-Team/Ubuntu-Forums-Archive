---
title: "codecs to play encrypted dvd and audio"
date: 2007-04-21
forum: General Help
---

### Post by Mia_tech on 2007-04-21
guys how do I install codecs to play encrypted dvd and audio?

thanks

---

### Post by vinnn on 2007-04-21
Open up the "Add/Remove" package tool in the Applications menu, select "All Available Applications", type **codecs** into the search box.
Up pops a bunch of stuff, voila.

Installing the GStreamer packages should give you all the media support you should want.

To install the DVD decryption package, open a terminal and type;
```
sudo apt-get install libdvdcss
```
or search for libdvdcss in the Synaptic package manager.

---

### Post by taurus on 2007-04-21
[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

---

