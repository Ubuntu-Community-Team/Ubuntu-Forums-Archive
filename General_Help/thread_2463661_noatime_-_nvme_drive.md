---
title: "noatime - nvme drive"
date: 2021-06-16
forum: General Help
---

### Post by Quarkrad on 2021-06-16
Running 20.04 mate.  My nvme/ssd has a number of partitions on it each with their own UUID.  In fstab I include noatime:

```
# / was on /dev/nvme0n1p2 during installation
UUID=35d5b79d-ae24-4c02-8d96-4ae452ed88d1 /               ext4    noatime,errors=remount-ro 0       1
```

Should I also include noatime for all the other partitions?  So:

```
# /home was on /dev/nvme0n1p3 during installation
UUID=d9203686-5296-45b7-9691-ce778a122e5d /home           ext4    defaults        0       2
```

becomes

```
# /home was on /dev/nvme0n1p3 during installation
UUID=d9203686-5296-45b7-9691-ce778a122e5d /home           ext4    noatime,defaults        0       2
```

---

### Post by sudodus on 2021-06-16
I don't use noatime on modern SSH drives (connected via NVMe or SATA). I am looking forward to the replies in this thread ...

---

### Post by CatKiller on 2021-06-16
Back in the day, when SSDs had a very limited number of writes they could do, noatime (don't write the last-accessed time to the file) extended the life of the drive. These days, though the number of writes is still finite, the number of writes is much bigger; you'll likely stop using the drive for other reasons before you run out of writes. So noatime is less of a big deal. 

If you're trying to extend the life by not writing the last-accessed time to files on your / partition, then you probably don't want to be writing the last-accessed time to files on your /home partition, either.

---

### Post by oldfred on 2021-06-16
My first SSD was about 10 years ago, a tiny 60GB boot drive of unkown manufacturer from Microcenter computer store, store brand. 

So I have used noatime for all SSD mounts and relatime for all HDD mounts.
It was my understanding only a few apps (mutt for one), needed the update time. I have not used any apps that I know of that caused issues.

I also use noatime for all flash drive mounts with full installs to flash drive.

---

