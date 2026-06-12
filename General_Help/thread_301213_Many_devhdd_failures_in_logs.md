---
title: "Many /dev/hdd failures in logs"
date: 2006-11-16
forum: General Help
---

### Post by Halmonster on 2006-11-16
I am seeing these errors in both /var/log/kern.log and /var/log/syslog.  They look like this:

```
Nov 16 16:39:14 HOSTNAME kernel: (17597418.348000) hdd: error code: 0x70  sense_key: 0x02  asc: 0x53  ascq: 0x00
```

These messages are appearing in pairs, two every other second.

/dev/hdd is my cd-rom drive, which is empty.  No one is logged on at the console, so neither GNOME nor KDE should be polling the device.  My CPU is a VIA Samuel running at 600 MHz.  The machine is primarily a firewall/router and fileserver, though it also handles a light email load and occasional browsing with Firefox.

Any help would be much appreciated.

Thanks,
Hal

---

### Post by MJN on 2006-11-17
Do you still get the messages if a CD is in (and mounted)?
 
(Note: I'm no expert here, just suggesting something which might strike a chord with someone)
 
Mathew

---

