---
title: "How to mount root as read-only?"
date: 2007-09-20
forum: General Help
---

### Post by syko on 2007-09-20
I have a computer that I'd like to be able to shut down at a moment's notice without having to properly shut it down, i.e., hit the power button when I'm done using it. To avoid corrupting files, it seems the way to go is to mount the root filesystem read-only...but how do I do that on Ubuntu? Any ideas?

---

### Post by psusi on 2007-09-20
The only thing you risk damaging from sudden power loss are files that were being written at the time, or had recently been written.  You can fix the latter by mounting with the sync flag, but this will slow down writes as they won't be cached.

---

### Post by syko on 2007-09-20
Hm, then is there maybe a way of preventing fsck from running every time you do a bad power-off?

Also, wouldn't there be some system processes writing to files often that could get corrupted?

---

### Post by kellemes on 2007-09-20
Some reading..
[http://gentoo-wiki.com/HOWTO_Read-only_root_filesystem]("http://gentoo-wiki.com/HOWTO_Read-only_root_filesystem")

---

### Post by psusi on 2007-09-20
Unless you have some servers installed, the only things that should be written to regularly on an out of the box install are system log files, and since they are only appended to, the worst that can happen is the last few log messages get lost.  

I didn't think fsck ran after a crash with ext3.  I know it doesn't for me on reiserfs.  It might depend on the fsck number you set in /etc/fstab.

---

### Post by dcstar on 2007-09-20
> **psusi said:**
> ........
I didn't think fsck ran after a crash with ext3.  I know it doesn't for me on reiserfs.  It might depend on the fsck number you set in /etc/fstab.

fsck should always run if the "Dirty" filesystem flag is set, this is usually if the system shuts down before cached data could be written to the disk.

Sometimes you can power off immediately without any corruption, and modern filesystems are designed to be as resilient as possible because power outages (and suchlike) are not uncommon.

I think that you can "tune" a parameter that forces a disk sync more often than default, and possibly you could turn off write caching altogether which would make the machine's disk performance a bit worse, but more reliable in this circumstance.

---

### Post by psusi on 2007-09-20
> **dcstar said:**
> fsck should always run if the "Dirty" filesystem flag is set, this is usually if the system shuts down before cached data could be written to the disk.


Nope, not with Journaling filesystems - that's their whole point.

---

