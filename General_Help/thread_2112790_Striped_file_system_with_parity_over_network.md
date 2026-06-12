---
title: "Striped file system with parity over network"
date: 2013-02-05
forum: General Help
---

### Post by c@ssie on 2013-02-05
I have 12 hacked Segate "Goflex Home" NAS drives,  that are running Ubuntu.  They are actually 1 ghz ARM computers,  with 128MB of RAM, 512 MB of NAND,  gigabit ethernet, and a SATA drive.

I want to use them as a single file system that is  striped with parity, (like RAID 4 or RAID 5).     Is there a way to do this?


.

---

### Post by Cheesemill on 2013-02-05
Maybe GlusterFS?

[http://www.gluster.org/about/](http://www.gluster.org/about/)

---

### Post by c@ssie on 2013-02-05
> **Cheesemill said:**
> Maybe GlusterFS?

[http://www.gluster.org/about/](http://www.gluster.org/about/)


gluster doesn't do parity, I'd need to waste half my drives as backup.

---

