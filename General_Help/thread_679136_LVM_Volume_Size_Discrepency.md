---
title: "LVM Volume Size Discrepency"
date: 2008-01-26
forum: General Help
---

### Post by SuperDodge on 2008-01-26
I am trying to set up an LVM drive on my new MythTV box...
I am using two partitions  One is 100% of a 500 GB drive.  The other is about 180 GB worth of a 320 GB drive.
I have successfully created a volume group called MythRecordings
I have successfully created a logical volume called MythRecordings

If I run sudo lvscan MythRecordings,  I am told that my logical volume is 740 GB in size.

I then run sudo mkfs -t ext3 /dev/MythRecordings/MythRecordings

I then mount this new logical volume to a directory I have created called /MythMedia

When I click in that directory I am told I have 692 GB of free space.

WHAT GIVES?

---

### Post by SuperDodge on 2008-01-26
Bump

---

### Post by SuperDodge on 2008-01-29
I never found a solution to this problem.  Formatting as JFS fixed the problem though...

---

