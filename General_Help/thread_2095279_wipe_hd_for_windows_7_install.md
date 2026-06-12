---
title: "wipe hd for windows 7 install"
date: 2012-12-16
forum: General Help
---

### Post by beenpicking on 2012-12-16
I am trying to wipe a hard drive that Ubuntu installed.so I can install windows7. I have had no luck making dvd of DBAN. I have been looking for a way to wipe from in the system. I read this can from the terminal. Using (sudo dd if=/dev/zero of=/dev/device_name) I have not work command very much,and this is not working for me. I have also tried fdisk with no luck.

---

### Post by Cheesemill on 2012-12-16
If you just boot the Windows installer it should let you delete any existing partitions and then install Windows in the empty space, or do you really want to wipe the drive first?

If you do want to wipe the drive then dd is the way to go but you can't do it from the drive you're running Ubuntu from, you'll have to boot from a Live CD.

Once you've booted from a Live CD can you open a terminal and type:
```
sudo fdisk -l
```

If you post back with the result then I can tell you exactly what dd command to use although the command you've already tried should have worked (it doesn't show any output until its finished).

---

