---
title: "trouble with ext3"
date: 2007-10-12
forum: General Help
---

### Post by atlfalcons866 on 2007-10-12
hi
i only have 2.9GB left on my 11GB /. But the problem is that it says i have 6.9Gb free. That is way more than the 5% reserved for ext3. Is there a way to reclaim that space reserved by ext3? If not i might look into using JFS again:(

---

### Post by taurus on 2007-10-12
```
sudo apt-get clean
df -h
```
Also, look in /var to make sure you don't have anything big taking up space.

```
sudo du -h /var
```

---

### Post by atlfalcons866 on 2007-10-12
none of that helped but i did read man tune2fs and it says ext3 reserved 39% of the space for root. Is there a way to fix it?

---

### Post by thirddeep on 2007-10-12
Default for ext3 is 5% for reserved space.  You may tune that online as you see fit.

Thd.

---

### Post by atlfalcons866 on 2007-10-12
> **thirddeep said:**
> Default for ext3 is 5% for reserved space.  You may tune that online as you see fit.

Thd.

if i do will my max inodes decrease or will it stay fixed?

---

### Post by thirddeep on 2007-10-12
Max inodes have nothing to do with free or reserved space.

I doubt you will run into max inode troubles in any case :=)

Also, you can reduce the reserved space on-line.

Thd.

---

### Post by atlfalcons866 on 2007-10-12
the inodes are not stored in the reserved space?

---

### Post by thirddeep on 2007-10-12
No, inodes are not in the reserved space.  That space is only accessible by root, in case you fill up your partition.  

Here is some more info on linux file systems : [http://tldp.org/LDP/intro-linux/html/sect_03_01.html](http://tldp.org/LDP/intro-linux/html/sect_03_01.html)

Thd.

---

### Post by atlfalcons866 on 2007-10-12
ok i always thought the reserved space was used for the inodes. The inodes have there own space. Its not like i will use 17Million inodes on my 133Gb /home:)

---

### Post by atlfalcons866 on 2007-10-13
i switched to jfs again:KS this time jfs is faster than ext3 and i have dynamic inode allocation thanks to JFS

---

