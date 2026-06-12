---
title: "Accessing Physical Disk from Virtual Disk--Has Anyone Asked This??"
date: 2007-02-02
forum: General Help
---

### Post by chrisg0619 on 2007-02-02
Is there a way to access the partitions of the physical disk from a virtual operating system?  I'm using VMWare server and don't want to boot a virtual machine from the "raw disk"; I just want to be able to access my computer's files every once in a while.

Is this possible?

---

### Post by Paerez on 2007-02-02
I run Windows inside VMWare in linux. You can use Samba to share between the two. (Samba = windows sharing).

---

### Post by chrisg0619 on 2007-02-02
Ah, ok.  Just installed Samba with the howto on the forum, and it's quite nice.  Thanks!

---

