---
title: "Hard Drive Partitions"
date: 2008-03-02
forum: General Help
---

### Post by Maxcore on 2008-03-02
Hey I've been running Ubuntu for a couple of days now on the same hdd as my windows install. Now that I have tranferred all the files off my windows install I would like to delete the partition and add the space to my ubuntu one. How do I do this?

---

### Post by kdarkentity on 2008-03-02
You can download the same partitioning tool that comes with the Ubuntu live-cd, open up a terminal and type 

sudo apt-get install gparted, 

and to run it as an administrator use the terminal and type

gksu gparted.

So in Gparted simple just delete your windows partition and you should be able to resize ubuntu to fill the space of you where your windows partition was. 

-enjoy-!

---

### Post by Maxcore on 2008-03-02
You're the man now dog thanks

---

