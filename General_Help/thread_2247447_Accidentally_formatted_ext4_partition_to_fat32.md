---
title: "Accidentally formatted ext4 partition to fat32"
date: 2014-10-08
forum: General Help
---

### Post by shanemikel1 on 2014-10-08
I have had a long day and it just got a whole lot longer.

I just accidentally formatted a very important ext4 partition using gparted to fat32.  Any help would be much appreciated.

---

### Post by Irihapeti on 2014-10-08
Firstly, don't do anything further with that partition. If you write to it, you may overwrite something important.

If this has only just happened, it's possible that [testdisk]("http://www.cgsecurity.org/wiki/TestDisk") might be able to help. It can restore the earlier partition table. It's in the Ubuntu repositories and can be used from a live DVD/USB.

I've not had to do this myself, so if you have any further questions, I'll let someone else answer.

---

