---
title: "udev rule for raw"
date: 2008-03-28
forum: General Help
---

### Post by Rotbert on 2008-03-28
Hi 
I created an udev rule (50-raw.rules) for raw devices and it didn't work:

ACTION=="add", KERNEL=="hdc1", RUN+="/sbin/raw /dev/raw/raw0 %N"
ACTION=="add", KERNEL=="hdc2", RUN+="/sbin/raw /dev/raw/raw1 %N"
ACTION=="add", KERNEL=="hdc3", RUN+="/sbin/raw /dev/raw/raw2 %N"
ACTION=="add", KERNEL=="hdc4", RUN+="/sbin/raw /dev/raw/raw3 %N"
ACTION=="add", KERNEL=="/raw/raw*", OWNER="dba", GROUP="dbs", MODE="0660"

The makenod's have been created in /lib/udev/devices and will be copied corretly into /dev/raw/raw*. The udev should execute the raw statement and change the ownership.

After system startup executing "raw -qa" shows that raw hasn't been executed correctly.

Thanks

---

### Post by justleen on 2008-03-28
try to create bash script, that is executed bij udev RUN+.
in that script start with a sleep 5 orso then do what you need to do.. 

I had some similair probs with mounting a usb stick, when mounted i copy a backup to it.. that only worked when i tried the above

---

### Post by Rotbert on 2008-03-31
Works fine! Using RUN and sleep did it!

---

