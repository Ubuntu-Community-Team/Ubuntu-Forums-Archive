---
title: "HP Laserjet 1022 printing in Kubuntu"
date: 2007-06-13
forum: General Help
---

### Post by MikePiff on 2007-06-13
I just spent the better part of a day trying to get this to print over a Belkin Print Server.  Finally I got it to work.  I removed the **1022** driver and installed the **1018** one.  The 1022 driver just made jobs hang, so this is surely a bug.

Moreover, it wasn't that easy to even find the 1018 driver!

---

### Post by bobpaul on 2007-07-06
Forums are kind of hear so we can learn from each others experiences. This is not the place to report bugs; developers read about bugs in the bugzilla pages on launchpad.

It would be nice if you posted what you did to fix it, so that people like me searching for a solution could find your post and know what to do. Glad to see it can be done, though. That at least gives me hope. :D

---

### Post by bobpaul on 2007-07-06
Ok, I got it now. First off, this printer does not store the firmware in the printer; it must be sent to the printer every time it's powered on. This part has been posted many times and instructions are on linuxprinting.org in the [user notes for this printer]("http://www.linuxprinting.org/show_printer.cgi?recnum=HP-LaserJet_1018"). Basically, in a term window do the following:

```

$ getweb 1018
$ sudo sh -c 'arm2hpdl sihp1018.img > /usr/share/foo2zjs/firmware/sihp1018.dl'

```

Next you need to configure the printer using the foo2zjs driver. For whatever reason, this was not showing up on Kubuntu in the printer manager (I was given driver selections for 1022, 1015, etc, but no 1018. Those other printers use foomatic, and not foo2zjs. So I had to use cups.

First, add yourself to the lpadmin group. This can be done through "System Administration: User Administration". Edit your user and add the 'lpadmin' secondary group.

Next connect to CUPS manually using a web browser. Connect to [http://localhost:631](http://localhost:631)
Click the Administration tab
Click "add this printer" next to the detected HP 1018. Mine showed up twice, use either or.
When you need to select drivers, Laserjet 1018 is near the bottom. It is not in the other group of Laserjet 1000s. You know it's the right one if the driver is foo2zjs.

Now you should be setup. If anyone knows an easier way, please share. On Ubuntu last week I only had to do the firmware part. I'm not sure why Kubuntu has to be difficult ;)

---

