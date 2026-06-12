---
title: "Upgrading Hard Disk - Need Help"
date: 2006-07-12
forum: General Help
---

### Post by kpkeerthi on 2006-07-12
I'm running ubuntu on a laptop so I do not have the luxury of mounting my new hard disk to my existing filesystem. I would like to backup my current partitions (1 primary ext3 and a swap) and copy them over to the new hard disk and be able to boot with all my data and customizations intact. I'm looking for your ideas for doing this.

---

### Post by simonn on 2006-07-12
Back them up to a CD/DVD, external hard disk*  or another computer.

Porbably best to use tar so that permissions will be retained regardless of the filesystem you backup to.

*You can get cheap cases or either just cables to plug into a bare drive, so you could set up your new hard drive before removing the old one.

---

### Post by hazart on 2006-07-12
You could also install both disks at the same time and then copy over the entire harddisk layout. I'm thinking of something like:

```
dd if=/dev/sda of=/dev/sdb
```

Then using gparted, or the like, resize your partitions to fit your needs. I have done this lots of times over network using udpcast.

Another way is to create the partitions as you like on the new disk, and copy over all the data. But remember, cp and tar does not handle special files like /dev/* and that stuff. Also remember to use the archive flag to preserve permissions and ownership of files.

---

### Post by kpkeerthi on 2006-07-12
Thank you guys.

---

