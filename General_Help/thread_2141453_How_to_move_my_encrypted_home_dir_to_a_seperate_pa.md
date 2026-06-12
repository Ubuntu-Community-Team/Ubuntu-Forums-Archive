---
title: "How to move my encrypted home dir to a seperate partition on a seperate hd"
date: 2013-05-02
forum: General Help
---

### Post by f1ndingwalden on 2013-05-02
So recentley I wanted to branch out and try out other linux distros, and the biggest factor deterring me from doing so is the amount of personal data in my home dir (movies, music, writings, ebook, programs (almost 1TB)). In order to make it easier for my to change my os I was wandering what the best way would be for me to put my home dir on a separate partition. My current home dir is encrypted, and I would like to do that with the new home dir, but I have no idea how to set any of that up. Any advice?

---

### Post by NM5TF on 2013-05-02
> **f1ndingwalden said:**
> So recentley I wanted to branch out and try out other linux distros, and the biggest factor deterring me from doing so is the amount of personal data in my home dir (movies, music, writings, ebook, programs (almost 1TB)). In order to make it easier for my to change my os I was wandering what the best way would be for me to put my home dir on a separate partition. My current home dir is encrypted, and I would like to do that with the new home dir, but I have no idea how to set any of that up. Any advice?

Just did this myself last month......very easy tutorial here:

[https://help.ubuntu.com/community/Partitioning/Home/Moving](https://help.ubuntu.com/community/Partitioning/Home/Moving)

good luck

Tommy

---

### Post by f1ndingwalden on 2013-05-02
Thanks! 
However, I have run into a new problem.. 
The secondary hdd that I am trying to transfer to has two partitions. I wanted to delete and repartition so that it is just one, however when I attempted this I ran into this error;
```
Error deleting partition /dev/sdb1: Command-line `parted --script "/dev/sdb" "rm 1"' exited with non-zero exit status 1: Error: Can't have a partition outside the disk!
 (udisks-error-quark, 0) 
```
Any ideas?

---

### Post by NM5TF on 2013-05-03
I am no software guru by any measure, just another on the path to Linux understanding....

don't know what the error messages mean that you got while trying to delete partition....

have you tried using gParted to delete/resize the /dev/sdb1 ???

you MAY have to use a Live-CD to load the OS so that gParted can work on the partition...

others much more knowlegable than I can help I'm certain...

---

