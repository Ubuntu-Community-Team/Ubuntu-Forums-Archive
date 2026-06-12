---
title: "LVM: Is this article accurate?"
date: 2008-01-05
forum: General Help
---

### Post by *Legion* on 2008-01-05
I was reading this article called [Demystifying LVM in Linux]("http://articles.techrepublic.com.com/5100-10879_11-6153549.html"), and it stated something that confused me. 

Specifically, it related to the notion of using *pvcreate* on an entire disk.

The pertinent quote:

> Before you can use a disk (or partition), you have to first initialize it. To initialize a disk (or partition), you use the pvcreate command. So if you want to initialize /dev/hdd5, you would run the command:
[INDENT][I]
pvcreate /dev/hdd5[/I][/INDENT]

which would create a volume group descriptor at the start of the disk where we want /var/www/html to live.

**You would not want to run the command on the entire disk. Using the entire disk as a volume would cause problems because any other OS would fail to recognize the LVM metadata, see the space as free, and possibly overwrite the data. This is only a problem if the volumes are going to be accessed by other OSs (i.e., Windows writing to a Linux disk via Samba).**

Can someone explain the bold part? I haven't been able to find anything else that suggests that if I use *pvcreate* to create a volume that uses a disk's entire space, and then share that volume over Samba, there would be a risk of Samba overwriting the LVM metadata.

If I'm not supposed to use the entire disk, what am I supposed to do? Leave some arbitrary amount of space free? Create a single partition the size of the drive, and then use that with *pvcreate*?

---

