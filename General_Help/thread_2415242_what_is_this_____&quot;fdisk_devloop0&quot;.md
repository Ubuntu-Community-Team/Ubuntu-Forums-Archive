---
title: "what is this????     &quot;fdisk /dev/loop0&quot;"
date: 2019-03-22
forum: General Help
---

### Post by 777funk on 2019-03-22
Fdisk -l 

gives me what I have in the Title
```

Disk /dev/loop0: 53.7 MiB, 56315904 bytes, 109992 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop1: 143.6 MiB, 150556672 bytes, 294056 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop2: 34.6 MiB, 36216832 bytes, 70736 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop3: 143.6 MiB, 150556672 bytes, 294056 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop4: 153.7 MiB, 161198080 bytes, 314840 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop5: 87.9 MiB, 92114944 bytes, 179912 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop6: 35.3 MiB, 37027840 bytes, 72320 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop7: 91.1 MiB, 95522816 bytes, 186568 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes



```


What is this? Why is this? I'm used to seeing actual devices and have never seen this before.

---

### Post by deadflowr on 2019-03-22
Most likely snap packages, which are special files that get mounted as loop devices.
df should list them, or snap list to see what snaps are installed.

---

### Post by 777funk on 2019-03-23
Thanks! I wonder why I'm seeing them all of the sudden and not before.

---

### Post by Impavidus on 2019-03-24
Maybe you had no snaps installed before.

---

