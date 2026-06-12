---
title: "Viewing Hard Drive Partitions"
date: 2008-02-09
forum: General Help
---

### Post by tom_the_drummer on 2008-02-09
Hi guys,

How can I view the other partitions on my computer from inside Ubuntu Studio, Ubuntu and Windows?

In Ubuntu I can see "Filesystem" and "sda2" but not the Windows partition, in Ubuntu Studio I can see "Filesystem" and "sda1" and in windows I can only see the windows partition.

How can I set it so I can see all the partitions in all the operating systems?


Thanks


Tom

P.S. I read somewhere that it was system - administration - disks, but I do not have this option.

---

### Post by SpaceTeddy on 2008-02-09
open a termial (applications->accessories->terminal)

see all partitions 
> sudo fdisk -l

see all mounted partitions
> df

if you acctually want to do something with them you will need to mount them.

---

### Post by jan quark on 2008-02-09
here is a great site dealing with mounting and partitions

[http://users.bigpond.net.au/hermanzone/p10.htm](http://users.bigpond.net.au/hermanzone/p10.htm)

if you have questions ask please

---

