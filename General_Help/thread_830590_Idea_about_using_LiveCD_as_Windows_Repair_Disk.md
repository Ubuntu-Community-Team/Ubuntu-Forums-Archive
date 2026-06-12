---
title: "Idea about using LiveCD as Windows Repair Disk"
date: 2008-06-16
forum: General Help
---

### Post by wozzinator on 2008-06-16
I was wondering if anyone had any insight on a topic such as this: I was wondering if it would be at all possible to install Wine to a LiveUSB and also install some Windows XP/Vista Antivirus through Wine onto the LiveUSB so that I could scan Windows XP hard disks for errors and viruses (virii) through the LiveUSB. This would be of great help since I wouldn't have to back up everything on a clients computer just to reformat it.

Also, if someones already come up with this idea, if they could link me to some info on it.

Thanks.

---

### Post by aysiu on 2008-06-16
There are native Linux antivirus programs (no need for Wine) that mainly scan for Windows viruses.

Check out [Scanning for viruses with Knoppix](http://www.oreillynet.com/sysadmin/blog/2004/06/scanning_for_viruses_with_knop.html)

---

### Post by stream303 on 2008-06-16
+1 for Knoppix.

Typically you can install the CD-version onto a 1gb or larger usb stick, or the DVD version onto a 4gb or larger stick.  You can also let it create "persistent" partitions that can also be encrypted as well if you want some semi-permanent storage.

To make it even more convenient, you can run

```
mkbootdev
```

from a terminal and it will help set up the bootable usb stick for you.  From there, you can run clamav or install f-prot or some other scanner of your choice.

---

