---
title: "Seriously poor SATA Performance"
date: 2006-07-08
forum: General Help
---

### Post by jtarrats on 2006-07-08
I have an Intel based Laptop w/SATA HDD. WinXP was installed and I recently added Ubuntu to 20GB Partition.

When I run hdparm -Tt /dev/sda2 my results are:
Timing cached reads: 4320 MB in 1.9 seconds = 2274.03 MB/sec
Timing buffered disk reads: 12 MB in 3.33 seconds = 3.60 MB/sec

This seems extremely slow to me and running anything on the desktop is painful.

Any Suggestions?

---

### Post by Boomy on 2006-07-18
Your performance way better than mine. Bump!

---

### Post by ticool on 2006-07-18
Use the search Button and Check for hdparm issues!

---

### Post by jerrykenny on 2008-01-13
That seems very sloooow, is it possible the wrong kernel module for your sata controller is being loaded ?

have a look at your lspci, and lsmod output, and see if that relates to what you already know about your hardware.

---

### Post by logos34 on 2008-01-13
what does this show?

sudo hdparm -i -v /dev/sda

---

