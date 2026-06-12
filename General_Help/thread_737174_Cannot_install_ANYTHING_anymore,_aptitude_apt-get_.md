---
title: "Cannot install ANYTHING anymore, aptitude apt-get error!"
date: 2008-03-27
forum: General Help
---

### Post by linuxvacuum on 2008-03-27
How can I repair aptitude ? Now when I try to install anything or even repair apt-get I get the following!

> sudo apt-get -f install

Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
21 not fully installed or removed.
Need to get 0B of archives.
After unpacking, 0B of additional disk space will be used.
dpkg: parse error, in file `/var/lib/dpkg/status' near line 13391 package `libcroco3':
 field name `(' must be followed by colon
E: Sub-process /usr/bin/dpkg returned an error code (2)

Please help!

---

### Post by jakev383 on 2008-03-27
Try running
```
sudo apt-get update
```
and see what pops up after that.

---

### Post by kellemes on 2008-03-27
I just don't get it crap like this is still not solved in Ubuntu.
If you haven't resolved this yet you can try to replace /var/lib/dpkg/status with /var/lob/dpkg/status-old and see if that works..
Always create a backup first!

---

### Post by Tosa on 2008-03-27
Aptitude went nuts half an hour ago while updating Firefox. Anyway, after I had renamed status-old to status everything was OK.
Thanks!

---

### Post by linuxvacuum on 2008-03-27
):P YES kellemes! You solved it! THANKS!

---

