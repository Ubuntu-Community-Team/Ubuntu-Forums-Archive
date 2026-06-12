---
title: "Exclude HDDs from Natitilus automount"
date: 2012-11-29
forum: General Help
---

### Post by Marc Desrochers on 2012-11-29
System has multiple SATA disks, Only /dev/sda is part of the OS. 

drives /dev/sdb, /dev/sdc, & /dev/sdd are physically present, but I want to exclude one or more of them so that they are *NEVER* seen in Nautilus. 

The reason: I am trying to get Virtualbox to use a raw device as virtual machine's disk. This is supported, albeit with a few warnings. I want to do this so that I can take a client's HDD, plug it in and boot it under VBOX. I don't want my host OS taking *any* action on this disk other than knowing that it is physically attached. You can probably figure out why, having two OSes trying to get at the same disk spells doom for the data on that disk.

I read that Ubuntu server does not automount, however this is my desktop, and I use it as such. As much as I like the automounting features, I want to know if I can, and if so how do I go about telling my system to ignore certain devices and never automount them all the while retaining to ability to automount other attached HDDs. 

Any thoughts?

---

### Post by dannyboy79 on 2012-11-29
i believe you'll have to look at udev rules. you can create a specific rule based on drive information/identity and in that rule instruct it to NOT automount.

---

### Post by Marc Desrochers on 2012-11-29
I looked at udev and from what I am understanding it would simply prevent the device from appearing in /dev/ at all.

I still want the device to be recognized, I just want it not to get mounted. Your reply did get me looking at udisks which seems to be closer to what I'm looking for. 

Having a bit of trouble understanding what it does and when though.

---

### Post by dannyboy79 on 2012-11-29
see here: [http://ubuntuforums.org/showthread.php?p=11898362](http://ubuntuforums.org/showthread.php?p=11898362)

---

