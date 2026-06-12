---
title: "Change physical volume uuid"
date: 2018-06-14
forum: General Help
---

### Post by somdara on 2018-06-14
Hi All,

One of my Ubuntu accidentally failed and lost some metadata in lvm. 
I use Live CD boot and than restore disk to the wrong UUID in physical volume. 
I can assign those PVS to lvm but after mount file was corrupted and some file said need restructure.

[ATTACH=CONFIG]280098[/ATTACH]

Any idea how can I change UUID btw these two physical disks ?

Thanks,

---

### Post by ajgreeny on 2018-06-14
Have a look at [https://linuxconfig.org/how-to-retrieve-and-change-partitions-universally-unique-identifier-uuid-on-linux](https://linuxconfig.org/how-to-retrieve-and-change-partitions-universally-unique-identifier-uuid-on-linux) and see if that helps.

I have no knowledge of raid/lvm or encrypted systems which could add extra difficulties, but this may be a good starting place for you.

I suspect whatever method you use will require a live system as you can not usually make changes to partitions when they are mounted.

---

