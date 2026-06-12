---
title: "Boot Errors"
date: 2008-02-29
forum: General Help
---

### Post by TheThingfish42 on 2008-02-29
Hello,

About a week ago, I deleted out my Vista partition, reformatted to ext3 and set it up to automount (with the help of the lovely Ubuntu Forums!) Suddenly today, when my laptop went to do the file system scan, its finding errors in my extra partition (sda1) my primary partition that has my filesystem on it is fine (sda3), and if I choose to skip the maintenence command and boot up anyways, everything appears to be functional. Im a touch confused here, I also went into the maintenence command line, unmounted sda1 and ran fsck from there. It has been going and then gets an error saying: Attempt to read block from filesystem resulted in short read while getting inode from scan. Ignore error?
If I choose yes, it asks if I want to force a rewrite, if I say no, it allows me to boot into Ubuntu just fine. I am thoroughly bewildered by this. Can anyone elaborate as to whats going on here, and possibly explain what I should do? I fear for my laptop!

Thank you :)

---

### Post by taurus on 2008-02-29
Post

```
sudo fdisk -l
cat /etc/fstab
```

---

### Post by TheThingfish42 on 2008-02-29
Alright, scrap that last post, I was able to get the partition mounted again, and for all intent purposes, I cannot find anything wrong on a gui level with it, but the file check still is giving me errors :/

---

