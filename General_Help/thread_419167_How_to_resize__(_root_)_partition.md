---
title: "How to resize / ( root ) partition"
date: 2007-04-22
forum: General Help
---

### Post by shankariyer on 2007-04-22
I used Partition Magic(windows xp) initially to partition my hard-drive, to give way for Linux( Ubuntu Feisty ).

Now Ubuntu is up and running, but while partitioning with in Ubuntu, I didn't create several sub-partitions ( mistake ).

Now how do split the / ( of 88G ) to smaller partitions/mount-points?

Also, would this affect Partition Magic and/or what ever it has created at the partition-table level?

Thanks!
Kramer.

---

### Post by crispy_420 on 2007-04-23
[GParted LiveCD]("http://gparted.sourceforge.net/livecd.php")

---

### Post by shankariyer on 2007-04-23
I had installed 'gparted' using Synaptics, but for the '/' partition, only 'unmount' is enabled. All other menu options are disabled - why?

---

### Post by nik on 2007-04-23
Because you cannot resize a mounted partition. And / has to be mounted. So you need to boot from the live cd privided in crispy_420's link...

---

### Post by ubu-for on 2007-04-23
> **crispy_420 said:**
> [GParted LiveCD]("http://gparted.sourceforge.net/livecd.php")

[GParted crashed and messed up my partition](http://ubuntuforums.org/showthread.php?t=386552), so backup your files first!

---

### Post by shankariyer on 2007-04-26
Hmmm... I decided to have a clean environment and reinstalled based on my plan, but these information were valuable, thanks!

---

### Post by nemesisrobot on 2007-04-26
use the GParted Live cd

---

