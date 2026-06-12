---
title: "Long Boot Time Since Last Kernel Update"
date: 2007-02-12
forum: General Help
---

### Post by OPaul on 2007-02-12
Since the last kernel update a few days ago my boot up time has increased considerably. It hangs at 

Checking file system
fsck 1.39 (29-May-2006)    [OK]

for a long time.

---

### Post by OPaul on 2007-02-13
Anyone else experience this?

---

### Post by kapetanski on 2007-02-17
Yeah, it's the same thing here, running xubuntu 6.10 with latest kernel

---

### Post by llamakc on 2007-02-17
That's because it is checking the filesystem, and is a feature.

---

### Post by OPaul on 2007-02-17
> **llamakc said:**
> That's because it is checking the filesystem, and is a feature.

It didn't used to check the file system? Anyway to disable it then?

---

### Post by llamakc on 2007-02-17
> **OPaul said:**
> It didn't used to check the file system? Anyway to disable it then?

Are you saying that it is fsck'ing with EVERY boot? I thought you originally meant that it had happened one time.

---

### Post by OPaul on 2007-02-17
> **llamakc said:**
> Are you saying that it is fsck'ing with EVERY boot? I thought you originally meant that it had happened one time.

Yea, every boot.

---

### Post by qpwoeiruty on 2007-02-17
Similar problem for me... Not every boot but similar. Last 20 boots (since kernel update), fsck has checked hda1 3 or 4 times

---

### Post by OPaul on 2007-02-20
Does anyone know what the new kernel might have done to cause this problem?

---

### Post by OPaul on 2007-02-26
I've attached the output from dmesg, if someone could take a look and see where the problem may be, I would be very grateful. This long boot time is getting to be a nuisance.

---

