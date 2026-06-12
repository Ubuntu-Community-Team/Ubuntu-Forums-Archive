---
title: "delete in hardy"
date: 2008-05-12
forum: General Help
---

### Post by satterle on 2008-05-12
My main data store is a FAT partition on my hard drive - from the days of Feisty. Under Gutsy, the trash function worked when I deleted from the partition. Under Hardy, the trash function doesn't work - modal box says can't move file to trash. Is this a bug or a feature?

---

### Post by Glaxed on 2008-05-12
if you are trying to delete something from your FAT partition, then this is because you are not root.

***There is a very good reason why. Being root gives you complete control over your system - which is potentially destructive!**
_The command I am posting should be used with EXTREME CAUTION._

Open a terminal and type "sudo rm -rf " with a space after "-rf". Then drag the file you want to delete from the file browser onto the terminal screen and press enter.
Type your password and hit enter - the file should be gone.

Do not do this to valuable files or directories (like /, /home, /dev, /proc, /etc, /tmp or anything like those).

---

### Post by chrisccoulson on 2008-05-12
The OP was asking why trash doesn't work on his FAT volume - as far as I can tell, he doesn't have any problems actually deleting stuff from it.

I think the behaviour seen it expected at the moment. Have a look at [https://bugs.launchpad.net/glib/+bug/192629]("https://bugs.launchpad.net/glib/+bug/192629")

---

