---
title: "Access hard drive"
date: 2007-01-20
forum: General Help
---

### Post by kenmiles on 2007-01-20
I am new to Linux so please be gentle.

I made a partition on my C drive and installed Ubuntu 6.10 with no problems.

I then partitioned my other hard drive with Gnome Partition Editor and it made a partition named hdb2. but I cannot find out how to access this partition to write to it. In the device manager fot this partition it says :
volume.is_mounted  bool  false
but I can't see to mount it.

Thanks in advance for any hekp.

Regards, Kenneth.
[http://kmiles.co.uk](http://kmiles.co.uk)

---

### Post by teaker1s on 2007-01-20
this is a great guide on all common questions and there is a section on mounting drives
[http://ubuntuguide.org/wiki/Ubuntu:Edgy]("http://ubuntuguide.org/wiki/Ubuntu:Edgy")

---

### Post by randiroo76073 on 2007-01-20
Ken, in device manager click once on line "volume.is_mounted bool false" to highlight, then click on word "false" and change it to true.  Close device manager.  This should mount your drive for you.  Here's a tutorial[lost bookmark] in a txt file that should help with any mount problems.

---

