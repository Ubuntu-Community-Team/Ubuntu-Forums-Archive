---
title: "Hardwae Failure"
date: 2013-04-02
forum: General Help
---

### Post by garwoon on 2013-04-02
Hi

I have an Ubuntu 12.04 system, which has mirrored IDE disks running in it. The Power supply has just gone bang.

I have an Ubuntu Laptop and would like to copy the data onto it, I have a IDE to USB adapter, so tried taking out one disk and connecting it to the Laptop. Ubuntu disk utility sees the disk and says it is part of an Array but I have no option to mount. Can it be done ?

Thanks in advance

Nigel

---

### Post by tgalati4 on 2013-04-02
It looks like you need 2 adapters to set up both disks as a mirrored array, then recover the data.  I'm not aware of a method that can suppress the RAID header to mount the disk individually.  How about getting a new power supply and rebuilding your current system?  Is the data worth $50?

---

### Post by garwoon on 2013-04-02
Hi

Yes I will have to get a new power supplie, I guess, I was in the process of migrating to a new server that only has scsi no IDE.

But guess I might have to get one. thanks

---

### Post by tgalati4 on 2013-04-03
You could buy a SATA/IDE card for the server to hook up your old disks.

---

