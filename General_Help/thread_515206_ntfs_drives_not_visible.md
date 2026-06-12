---
title: "ntfs drives not visible"
date: 2007-08-01
forum: General Help
---

### Post by matrunner on 2007-08-01
recentlyi edited grub for del entry of older kernel version to be avail on booting....now with kernel 2.16...
later found that my 4 drivers of ntfs not visible on ubuntu fiesty fawn 7.02....
how to rectify this....
was this due to grub editing...i am sure i didnt del any details othert than that older ver kernal detail...no uninstalling or any else ....

---

### Post by merlinus on 2007-08-01
Post the usual....

```

sudo fdisk -l
cat /etc/fstab/
cat /boot/grub/menu.lst

```

To save time and bandwidth, edit out top part of the latter.

-merlin

---

