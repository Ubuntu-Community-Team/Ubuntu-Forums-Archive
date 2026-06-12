---
title: "Errors were found while checking disk drive /."
date: 2015-03-29
forum: General Help
---

### Post by mbksgx on 2015-03-29
hello all,

i have a similar but different disk error.

it is bad sectors, but when i try FSCK, it says it cant do anything due to a "super-blocks -b 8193" problem. and e2fsck of course doesnt work. its a ext4.
so what else can i do to rectify bad sectors? "dd" the whole disk?

---

### Post by Elfy on 2015-03-29
cut from hijacked thread and a bump

---

### Post by dragonfly41 on 2015-03-29
Search for "repair broken Superblock"

[https://linuxexpresso.wordpress.com/2010/03/31/repair-a-broken-ext4-superblock-in-ubuntu/](https://linuxexpresso.wordpress.com/2010/03/31/repair-a-broken-ext4-superblock-in-ubuntu/)

---

### Post by dragonfly41 on 2015-03-29
Search for "repair broken Superblock"

[https://linuxexpresso.wordpress.com/2010/03/31/repair-a-broken-ext4-superblock-in-ubuntu/](https://linuxexpresso.wordpress.com/2010/03/31/repair-a-broken-ext4-superblock-in-ubuntu/)

[http://unix.stackexchange.com/questions/33284/recovering-ext4-superblocks](http://unix.stackexchange.com/questions/33284/recovering-ext4-superblocks)

---

### Post by slickymaster on 2015-03-29
> **mbksgx said:**
> hello all,

i have a similar but different disk error.

it is bad sectors, but when i try FSCK, it says it cant do anything due to a "super-blocks -b 8193" problem. and e2fsck of course doesnt work. its a ext4.
so what else can i do to rectify bad sectors? "dd" the whole disk?
See this thread: [http://ubuntuforums.org/showthread.php?t=2177756](http://ubuntuforums.org/showthread.php?t=2177756)

---

