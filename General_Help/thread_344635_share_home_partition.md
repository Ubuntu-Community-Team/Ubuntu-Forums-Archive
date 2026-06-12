---
title: "share /home partition"
date: 2007-01-23
forum: General Help
---

### Post by jmvidalvia on 2007-01-23
¿can I create a /home partition and install, in two aditional partitions, two different linux distributions?
I mean, two linux systems using and sharing the same /home partition.
Thanks!

---

### Post by gwpritch on 2007-01-23
Sure you can.  I have noticed that certain distributions may reference eg. configuration files slightly differently so you may end up with redundant files but it shouldn't be a problem.

---

### Post by bodhi.zazen on 2007-01-23
You can share /home, however there may be occasional conflicting . files. These files save things like preferences and may vary between distro's.

Consider using a /data partition.

---

### Post by Pobega on 2007-01-23
It should work for the most part, just make sure that they both have the /home entry in each of their fstab files.

As bodhi.zazen said, there *might* be some conflicting, but I personally doubt there would be too much. A /data partition is nice to share data, but it doesn't share configuration.

---

### Post by jmvidalvia on 2007-01-23
Thank you very much.
Now I have dapper-kde and edgy-gnome, with two /home.
I will move from dapper-kde to edgy-xfce4, and create a new partition for both /home.
I hope that, as all will be Ununtu's apllications, there wont be any problem...
Thanks!

---

