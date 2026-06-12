---
title: "Mount points moved in Gutsy"
date: 2007-11-05
forum: General Help
---

### Post by scotta on 2007-11-05
I have a second IDE hard drive with an NTFS partition. I had the mounted read only but as soon as I upgraded to Gutsy it would no longer mount. I tried the ntfs-3g driver, did everything I could think of to mount /dev/sdb1 to no avail.

Turns out on Gutsy /dev/sdb1 is no more I had to use /dev/mapper/sdb1 as the device and as soon as I did this all worked fine.

Anyone know why the change?

Thanks
Scott

---

### Post by ofb on 2007-11-05
Not a solution, but information.

[http://en.wikipedia.org/wiki/Device_mapper](http://en.wikipedia.org/wiki/Device_mapper)
[http://sources.redhat.com/dm/](http://sources.redhat.com/dm/)

---

