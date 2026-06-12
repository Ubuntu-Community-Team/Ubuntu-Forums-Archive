---
title: "how to add disk space to primary partition?"
date: 2013-07-19
forum: General Help
---

### Post by vedantgp on 2013-07-19
[IMG]http://postimg.org/image/5awl1dget/[/IMG]

I just installed Ubuntu 13.04, i tried using g parted. i am trying to add space to the primary partition from the unallocated partition. it wont let me. all of the options are grayed out except for unmount, manage flags and information. i only want to keep 2 partitions,
data, and the system
i have a 320gb hdd

i am new here and i can use all the help i can get.

---

### Post by slickymaster on 2013-07-19
You can use the **resize2fs** command to increase as well as decrease the size of a partition. See```
man resize2fs
```for instructions.
Also see this link: [https://access.redhat.com/site/documentation/en-US/Red_Hat_Enterprise_Linux/6/html/Storage_Administration_Guide/ext4grow.html](https://access.redhat.com/site/documentation/en-US/Red_Hat_Enterprise_Linux/6/html/Storage_Administration_Guide/ext4grow.html)

---

### Post by coffeecat on 2013-07-19
Not a Cafe question.

*Thread moved to **General Help**.*

---

### Post by oldfred on 2013-07-19
Are you using live installer not your install on hard drive?
You have to unmount all partitions, so you cannot run from working system.
Even with live installer, you usually have to click on swap and swap off to unmount it.

       GParted partitioning software - Full tutorial 
[http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html)
Screenshots of using gparted
[http://www.howtoforge.com/partitioning_with_gparted](http://www.howtoforge.com/partitioning_with_gparted)
Partitioning basics with some info on /data, older but still good bodhi.zazen
[http://ubuntuforums.org/showthread.php?t=282018&highlight=separate+%2Fdata+partition]("http://ubuntuforums.org/showthread.php?t=282018&highlight=separate+%2Fdata+partition")

---

