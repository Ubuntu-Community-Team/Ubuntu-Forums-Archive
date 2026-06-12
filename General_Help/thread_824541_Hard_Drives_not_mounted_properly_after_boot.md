---
title: "Hard Drives not mounted properly after boot"
date: 2008-06-10
forum: General Help
---

### Post by Flobbes on 2008-06-10
A got a really strange problem.

After every boot my hard drives are iterated differently:
sda
sdb
...

So the same Hard drive has a different position next boot.

/
/home
etc
are mounted correctly, but i cant mount my own hard drives automaticly because of this accurance.

I have 3 Sata drives, 2 CD-Rom connected to the IDE-Port and 1 IDE HD that is connected to an PCI-Controller.

Anybody got an Idea what I can do to solve this problem?

---

### Post by cmnorton on 2008-06-11
Posting your /etc/fstab and the output of df would help.

---

### Post by Flobbes on 2008-06-11
Thx but i found something about HD UUIDs and its working fine this way. :)

---

