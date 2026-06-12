---
title: "help me out"
date: 2007-02-27
forum: General Help
---

### Post by panfil on 2007-02-27
i have a windows partition and i can`t accses it, nethier withs linux, i don`t want to format it. i don`t know if is fat or ntfs? i can see it but i can`t accses! thx

---

### Post by panfil on 2007-02-27
i have a windows partition and i can`t accses it, nethier withs linux, i don`t want to format it. i don`t know if is fat or ntfs? i can see it but i can`t accses! thx

---

### Post by nsleiman on 2007-02-27
did u try to chown or chmod 777 /dev/xxx ?

maybe the u must change the group only!

---

### Post by 7h35ur930n on 2007-02-27
did you have windows OS on it, did you use encryption software on the OS if you did? what software have you used to try access it? how big is the partition? does it not say if its ntfs or fat32? more information would make it easier to answer!!!

---

### Post by Bachstelze on 2007-02-27
[https://wiki.ubuntu.com/MountingWindowsPartitions](https://wiki.ubuntu.com/MountingWindowsPartitions)

If you need more specific halp, you'll have to be more specific about the problem you have.

---

### Post by 3rdalbum on 2007-02-27
We'll be able to help you better with some more information. Copy and paste the outputs of these commands:

```

sudo fdisk -l
cat /etc/fstab
ls /media

```

Then we'll be able to know what you've done already in your attempts, and how to get it all working.

---

### Post by Bachstelze on 2007-02-27
And creating two threads for the same issue is not a good idea, either.

---

### Post by urk_nono on 2007-02-27
Using **gparted** makes it a lot easier messing about with partitions.

[HTML]sudo apt-get install gparted

sudo gparted[/HTML]

From there you can find out whether it's FAT32 or NTFS (though I doubt it's FAT32) and mount/unmount. Wish you the best of luck.

Urk

---

