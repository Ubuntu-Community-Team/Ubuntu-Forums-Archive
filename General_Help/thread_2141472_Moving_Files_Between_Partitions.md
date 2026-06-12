---
title: "Moving Files Between Partitions"
date: 2013-05-02
forum: General Help
---

### Post by NM5TF on 2013-05-02
I am wanting to move some files from partition sda7 to partition sda9...

Is this easily possible....if so, how do I proceed???

TIA, 

Tommy

---

### Post by ajgreeny on 2013-05-02
As long as thr partitions are mounted they will both show in the file  manager so you move any files the same way as you do from folder to  folder, ie in terminal with ```
mv /source/path/to/files  /destination/path/to/files
``` or using drag & drop with your  mouse in file manager.

---

### Post by Impavidus on 2013-05-03
It will take more time than moving a file within a partition, otherwise, it's the same.

---

### Post by NM5TF on 2013-05-04
> **ajgreeny said:**
> As long as thr partitions are mounted they will both show in the file  manager so you move any files the same way as you do from folder to  folder, ie in terminal with ```
mv /source/path/to/files  /destination/path/to/files
``` or using drag & drop with your  mouse in file manager.

I figured it would be something easy...

thanx for the replies guys...

Tommy

hmmmmmmmmmmmm.....can't seem to find how to mark thread as "solved" in tools anymore

---

### Post by Impavidus on 2013-05-04
That function got damaged during an upgrade of the forum. See here for a work-around: [http://ubuntuforums.org/showthread.php?t=2121377](http://ubuntuforums.org/showthread.php?t=2121377)

---

