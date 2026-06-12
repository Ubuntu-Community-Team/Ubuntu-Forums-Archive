---
title: "Recognize SD Reader."
date: 2013-06-21
forum: General Help
---

### Post by MarkRod59 on 2013-06-21
I have fount the following terminal command(s) to get my system to recognize the SD reader.  " sudo su -l echo 1 > /sys/bus/pci/rescan "  How do I get these to automatically execute on bootup/startup?

---

### Post by Gillingham on 2013-06-22
Have a look at adding the command to /etc/rc.local, this should run the command as root at start up.

You'll probably want to read up a bit on rc.local to make sure it is suitable, but that is where I'd out it.

David

---

