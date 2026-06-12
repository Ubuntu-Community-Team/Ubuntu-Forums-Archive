---
title: "Partitions"
date: 2007-12-31
forum: General Help
---

### Post by KillerZ on 2007-12-31
I have a question about partitions. In my computer there are two hard drives a 250GB and a 500GB and I have vista installed on the 250GB and the 500GB for storage. I wanted to split the 250GB in half, one half windows and the other half linux (I know how to do this). But my question was about the 500GB hard drive, right now it is NTSF and I want to use it as storage for linux and windows, so would linux be alright leaving as NTSF so I could just make two folders on the hard drive and put all my windows stuff in one and all my linux stuff in the other because I don't want to partition the 500GB hard drive in two.

---

### Post by jken146 on 2007-12-31
Ubuntu has built in read and write support for NTFS.  You shouldn't have a problem.

---

### Post by NilsE on 2007-12-31
It will work. 

ntfs-3g is the driver that is used to access an NTFS partition in RW mode in Ubuntu.

---

### Post by KillerZ on 2007-12-31
ok thanks.

---

### Post by insane_alien on 2007-12-31
if the ntfs partition you want to acess is compressed or encrypted then you are out of luck. if it isn't then you will be fine.

---

