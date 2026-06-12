---
title: "Removing this"
date: 2007-11-02
forum: General Help
---

### Post by yongkailoon on 2007-11-02
Referring to this thread [http://ubuntuforums.org/showthread.php?t=193470]("http://ubuntuforums.org/showthread.php?t=193470") , there is a method mentioned to change the mount point to /mnt. I would like to know if I am suppose to put /mnt or something like /mnt/hdd1 at the Mount Point ?

---

### Post by Thyme on 2007-11-02
Hi yongkailoon,

The mount point is the folder in your filesystem where you want the media to show up. The most commonly used ones are /media and /mnt. It does not matter where you mount it to ..

Having said this, the <file system> column is where you specifiy the device you want to mount, such as /dev/hda, /dev/hdb, /dev/hdc etc ..

Did you manage to get it right?

---

### Post by mikewhatever on 2007-11-02
> **yongkailoon said:**
> Referring to this thread [http://ubuntuforums.org/showthread.php?t=193470]("http://ubuntuforums.org/showthread.php?t=193470") , there is a method mentioned to change the mount point to /mnt. I would like to know if I am suppose to put /mnt or something like /mnt/hdd1 at the Mount Point ?

The second option is correct. You might also think of better mount points like /mnt/XP or /mnt/storage or /mnt/data, etc. Each partition gets its own mount point, just in case.

---

### Post by yongkailoon on 2007-11-02
Hi guys, thanks for the reply. I really appreciate it. :)

---

