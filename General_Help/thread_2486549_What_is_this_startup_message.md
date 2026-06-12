---
title: "What is this startup message?"
date: 2023-05-04
forum: General Help
---

### Post by sofasurfer on 2023-05-04
Ubuntu 20.04. During boot, right after the splash screen and during the black screen I see this message ```
  Home: clean, 176294/9158656 files, 28557621/36621056 blocks 
``` What is it trying to tell me?

---

### Post by yancek on 2023-05-04
I expect that is from running fsck (filesystem check) on your home partition and showing no problems.

---

### Post by ActionParsnip on 2023-05-04
Just an fsck. Do you see it every boot?

---

### Post by sofasurfer on 2023-05-04
Yes every boot. What are the numbers?

---

### Post by ajgreeny on 2023-05-04
The numbers are simply telling you the size of the disk or partitions and that it is clean; it is nothing to worry about. I see the same message every time I boot, which is very seldom as I just put things in suspend mode and reboot only when an update tells me to do so.

Running a full fsck would take a much longer time than I think you are probably seeing and this message is just telling you that the filesystem is clean and good to go.

---

