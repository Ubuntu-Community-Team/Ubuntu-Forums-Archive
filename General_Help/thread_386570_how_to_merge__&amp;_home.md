---
title: "how to merge / &amp; /home ?"
date: 2007-03-17
forum: General Help
---

### Post by kanha on 2007-03-17
hi,
my harddisk is partitioned as
/   ---->7Gb (sda1)
swap-->1Gb (sda2)
/home----->30Gb (sda3)
one extended partition after this which have 5 partition ,whatever

Now I want to merge my home and root partition.I mean I want to move my home in / partition.
how to do that? obviously without messing up settings and ubuntu install
please help

---

### Post by Kateikyoushi on 2007-03-17
Why do you want to merge it ?
I would follow these steps of course with changing where necessary. because it was written to move files to /home [LINK]("http://www.psychocats.net/ubuntu/separatehome")

---

### Post by kanha on 2007-03-17
actually i am trying to install mac osx10 for amd processors.it need a primary partition.and my hdd supports only upto 4
i have made /,/home,swap and one extended,so it add up to 4
i wanted to make one more primary partiton :confused:

---

### Post by Kateikyoushi on 2007-03-17
I would rather put swap in extended, and resize partitions so you have space for OSX. Then reactivate swap.

---

