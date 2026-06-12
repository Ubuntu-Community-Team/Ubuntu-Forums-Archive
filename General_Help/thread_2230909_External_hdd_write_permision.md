---
title: "External hdd write permision"
date: 2014-06-22
forum: General Help
---

### Post by dcintes on 2014-06-22
Hi,

I have an external hdd with ntfs. It's mount correct but cant write, just can read the files.

The SO is ubuntu 14.04 but in my old 13.04 never have this problem, why?

What's is wrong with 14.04? I expect a stable version but just have lot of bugs. Last week ask because can't power off the computer and today can't do it. [http://ubuntuforums.org/showthread.php?t=2229742](http://ubuntuforums.org/showthread.php?t=2229742)


Someone have a recomendation? Other distribution or just go back to 13.04. I ask a friend to try linux, but can't install this.

Thx.

---

### Post by varunendra on 2014-06-26
To let us see what options the drive is mounted with, please open a terminal (Ctrl-Alt-T) and post back the outputs of -
```
mount
```

Linux mounts an NTFS partition read-only if it does not see a "Clean" flag on the partition table. It happens when the drive has not been properly removed ("Safely remove.." option in windows) from a system it was previously connected to. In this case, the best option (other than 'Force mounting' - which may be risky for the data) is to simply connect the drive again to a windows computer, then "Safely remove" it making sure it is removed _after_ windows shows the message that it can be safely removed.

---

### Post by dcintes on 2014-06-28
Hi,

Don't understant but today don't have any problem... Now works fine.

Thx

---

