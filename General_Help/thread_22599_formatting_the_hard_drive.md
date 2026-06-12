---
title: "formatting the hard drive"
date: 2005-03-28
forum: General Help
---

### Post by wurtel on 2005-03-28
Here's the problem:
A friend of mine can no longer use his keyboard in windows (the keyboard isn't broken but it must be some kind of driver conflict, i dont know)
Since he can't use the win xp disc to format his hard drive, I advised/suggested him to use a linux live cd and see if his keyboard still works (which it does).

Now, it would be very useful if he could format his hard disc from this live cd. I've been searching the net now for some time with no results :(
If there's anyone who knows if it's possible or how to format your hard disc with a gnoppix live cd, please let me know, it would be greatly appreciated!

Thanks in advance.

---

### Post by dare2dreamer on 2005-03-28
```
sudo fdisk -l
```
Will list of the partitions of the available drives, so you can determine which drive you need to format.

After that, you can use mkfs on the appropriate drive to create a filesystem.

read the man page for mkfs for details on creating various filesystems.

---

