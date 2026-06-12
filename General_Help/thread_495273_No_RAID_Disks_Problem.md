---
title: "No RAID Disks Problem"
date: 2007-07-07
forum: General Help
---

### Post by dude_man111 on 2007-07-07
I also seem to be having the "No RAID Disks" error. I tried to retrieve the log files and I also tried to put it into a verbose mode but nothing changed. The error comes right after it says "boot" and then I believe it says "loading...". I never get into any part of Ubuntu. Once it says "No RAID Disks", nothing happens. I am surprised so many people are having the same error but we still cannot seem to get it resolved. 

-I am running Windows XP SP2. 
-I installed Wubi on to my secondary D: drive.

*If you need any more information to help I would be glad to attempt to get it for you. Thanks!*

**-bryce**

---

### Post by ago on 2007-07-08
The no raid disk problem is not an error. You should see the content of zenigata.log and lupin.log which you find ether under c:\wubi\logs in windows or under /tmp in linux.

So far the 2 cases where due to either use of raid, or unclean ntfs partition (you need to run chkfs /f and then reboot into windows twice and/or defragment).

---

