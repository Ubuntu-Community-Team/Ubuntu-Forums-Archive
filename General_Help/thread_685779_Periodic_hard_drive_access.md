---
title: "Periodic hard drive access"
date: 2008-02-02
forum: General Help
---

### Post by Holy-Fire on 2008-02-02
Hi. I'm using Ubuntu 7.10. Once every few seconds, my hard drive is accessed and makes noise for a split second - even when I'm not doing anything. Is there some way to prevent this? Thanks.
Edit: Some more searching has revealed that people have been encountering a similar-sounding problem on *laptops*. I would like to emphasize that I am using a *desktop* computer. If it is in any way relevant, the drive in question is a WD1500ADFD (WD Raptor Sata 150GB 10k RPM).

---

### Post by articpenguin on 2008-02-02
If your filesystem is ext3 then its normal for it to that. Its writing to the journal every 5 seconds.

---

### Post by Holy-Fire on 2008-02-03
Thanks. Is it possible to make it not do that, or at least do it in longer intervals? Is there a file system in which this doesn't exist?

---

### Post by seventyeights on 2008-02-03
You could try to add noatime and nodiratime for each partition in your /etc/fstab.

e.g.
```
# /dev/sda1 UUID=xxx   /   ext3    noatime,nodiratime,defaults        0       2
```

---

### Post by Holy-Fire on 2008-02-03
> **seventyeights said:**
> You could try to add noatime and nodiratime for each partition in your /etc/fstab.

e.g.
```
# /dev/sda1 UUID=xxx   /   ext3    noatime,nodiratime,defaults        0       2
```

This seems to have reduced the problem considerably. Thanks!

---

### Post by seventyeights on 2008-02-03
Glad to help. Btw, this turns off the last-accessed-timestamp for files, but you probably wouldn't notice unless you sort out your files that way.

---

