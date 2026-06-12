---
title: "Disk space dissapeared"
date: 2015-02-06
forum: General Help
---

### Post by philrosenberg on 2015-02-06
Hi
I have an Ubuntu 14.04 installation on an old Dell optiplex that I run as my home media server with mythtv. The PC has an 80 GB internal hard drive and a 2 TB usb drive. I have my home directory located on the USB drive and all my recordigns from mythtv go there too.

I just tried to download some files and found I was out of space. I downloaded some recordings and still no luck. I checked the disks application and it says my intenal drive has 55 GB free and my usb drive has 106 GB free, yet if I right click on any folder in my home directory it says I have a few tens of kB free.

Does anyone know what might be going on or how I can start trying to find out?

Phil

---

### Post by philrosenberg on 2015-02-06
So I rebooted before posting this and still the same, then after I posted this I checked again and suddenly I have 177 GB free space in my home directory when I right click a folder and check properties, and when I look in the drives app I have 260 GB free on my USB drive. The two still don't match, but at least some space has appeared. Something somewhere must have beed delaying the space becoming available I guess

---

### Post by Impavidus on 2015-02-06
By default, 5% of the file system (or about 100GB in this case) is reserved for root, so this is free space but not available space. This space is meant for emergencies, so that the root user has headroom to fix things and write logs when an ordinary user has filled the entire drive, and for headroom during normal operations, to keep things fast and prevent fragmentation. You can tune it using the command **tune2fs**. From the manual:```
       -m reserved-blocks-percentage
              Set the percentage of the filesystem which  may  only  be  allocated  by
              privileged  processes.    Reserving some number of filesystem blocks for
              use by privileged processes is done to avoid  filesystem  fragmentation,
              and to allow system daemons, such as syslogd(8), to continue to function
              correctly after non-privileged processes are prevented from  writing  to
              the  filesystem.  Normally, the default percentage of reserved blocks is
              5%.

```

---

