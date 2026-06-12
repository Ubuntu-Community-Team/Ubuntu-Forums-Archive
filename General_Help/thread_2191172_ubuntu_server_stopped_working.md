---
title: "ubuntu server stopped working"
date: 2013-12-01
forum: General Help
---

### Post by andrew.pal.42 on 2013-12-01
When i got home today and turned on my server, it didn't turn up on the network so i plugged in a keyboard and monitor and found the following error msg "this is a *freenas data disk* and cannot boot *system*. *system halted*".

I restarted it a few time and still kept getting the error msg so i turned it off and went to bed. when i got up i turned it back on and got this error msg "Reboot and select proper boot device or insert boot media in selected boot device and press a key".

Dose anyone know whats going on with it and how to fix it.

---

### Post by Iowan on 2013-12-01
I could be way off base, but it sounds like the hard drive is failing. I had one that would work "most of the time" - occasionally corrupting sectors. System would *usually* recover.

---

### Post by tgalati4 on 2013-12-01
If you are running *freenas* instead of Ubuntu, then typically, you have a separate boot disk or partition or USB stick to boot from.  Data is then stored on a separate disk or partition.  So is this a freenas system or an Ubuntu system?  How long has the server been running before it failed?

---

### Post by andrew.pal.42 on 2013-12-01
the server is running Ubuntu Server 12.04.3 LTS from a thumb drive and the data is stored on internal HDD in a ZFS pool. I set it up about 6 months ago but it spends a lot of time offline as i shut it down when i go away for work.

---

### Post by tgalati4 on 2013-12-01
Normal server installations will kill a thumb drive unless you have taken several precautions.  Freenas can boot from a thumb drive, but it runs completely in RAM.  Is your installation a LiveDVD session or did you simply install the server to the thumb drive with the log files saved to the thumb drive as well?

---

