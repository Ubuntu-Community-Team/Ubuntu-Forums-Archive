---
title: "Disk utility crashes when run self test is performed in ubuntu 12.04"
date: 2014-01-27
forum: General Help
---

### Post by krishna.988 on 2014-01-27
Disk utility crashes when run self test is performed in ubuntu 12.04. It also crashes when I check the Don't notify me of failure and also when I uncheck this. Any idea why this happens?

It crashes with "**[SIZE=3]palimpsest crashed with SIGSEGV in g_hash_table_foreach()" [/SIZE]**[https://bugs.launchpad.net/ubuntu/+source/gnome-disk-utility/+bug/1198508](https://bugs.launchpad.net/ubuntu/+source/gnome-disk-utility/+bug/1198508)

---

### Post by krishna.988 on 2014-01-28
I was able to solve this by adding gnome 3 ppa and updating the missing packages in 12.04..The disk utility software also was updated..Now I have Disk Utility at version 3.4.1..So lesson learnt is to upgrade gnome fully not only install it from software center..This inturn will update the missing packages and solve incompatibilities..

---

### Post by jcottier on 2014-01-29
I added the ppa, and yes it now works. But it looks awful compared to the stock Ubuntu version and seems to lack functionality. It now starts a test without crashing, but gives an error if you try to abort the long test.

---

### Post by krishna.988 on 2014-01-29
Does it crash or it is giving an error? can you please post a screenshot

---

