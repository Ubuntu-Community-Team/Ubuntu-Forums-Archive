---
title: "Mystery of the Phantom Swap Space"
date: 2007-06-02
forum: General Help
---

### Post by insane_alien on 2007-06-02
curious thing i noticed just now, my laptop is reporting a bigger swap space than i partitioned.

I have a 1.46GB swap partition yet conky and system monitor both report a 2.93GB swap space.

my question is where is this extra swap space coming from if it isn't in the swap partition. i have 1GB of RAM if thats important.

---

### Post by bollix47 on 2007-06-02
I had that happen to me once when I loaded a second version of linux on my system and gave it a swap partition.  When it booted it added both the new swap and the old swap.  Ended up with double the swap.  

When I put on a new version now I don't bother creating a swap partition as the system will pick up the existing swap partition, even when it's on a different physical disc.

Perhap you have two versions or an old swap partition?

Have you tried 

```
cat /etc/fstab
```

to see if there is more than one swap listed?

---

### Post by Denn1s on 2007-06-02
if you have no clue, maybe gParted will help you since it lets you see your hard disks graphically

---

### Post by insane_alien on 2007-06-02
just got the one swap partition. gparted and fstab show one partition gparted shows the correct size(it should since it created it :P)

---

### Post by bollix47 on 2007-06-02
What is the output from 

```
sudo fdisk -l
```

?

---

### Post by insane_alien on 2007-06-02
```
Disk /dev/hda: 40.0 GB, 40007761920 bytes
255 heads, 63 sectors/track, 4864 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1               1        1020     8193118+  83  Linux
/dev/hda2            1021        4673    29342722+  83  Linux
/dev/hda3            4674        4864     1534207+  82  Linux swap / Solaris
```

still says 1 partition of swap

---

### Post by bollix47 on 2007-06-02
Perhaps you might have more luck in the [Gutsy Gibbon forum]("http://ubuntuforums.org/forumdisplay.php?f=238").

---

### Post by insane_alien on 2007-06-02
this is on feisty though. i do the gutsy testing on a seperate machine. if it was a gutsy problem i would have posted there

---

### Post by DoktorSeven on 2007-06-02
Output of
```

cat /proc/swaps

```
?

---

### Post by insane_alien on 2007-06-02
cat /proc/swaps pruduces:

```
Filename                                Type            Size    Used    Priority
/dev/hda3                               partition       1534196 37264   -1
/dev/mapper/hda3                        partition       1534196 0       -2

```

so the swap has been mapped twice? how do i fix this?

---

### Post by insane_alien on 2007-06-03
bumpity bump bump

---

### Post by kaurman on 2007-08-09
You could try editing /etc/fstab.

Get rid of the swap partitions UUID stuff and replace that with /dev/hda3

---

