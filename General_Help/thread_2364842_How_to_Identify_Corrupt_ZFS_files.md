---
title: "How to Identify Corrupt ZFS files"
date: 2017-06-28
forum: General Help
---

### Post by wernerb1969 on 2017-06-28
Hi,

Need to identify what the reference below identifies...

Have a ZFS array with 8 drives (4 sets of mirrors), a bad drive caused some permanent errors as listed.  What does the hex addresses represent and how do I identify them so I can clear this list.  Thanks

zpool status zRAID -v

errors: Permanent errors have been detected in the following files:

        zRAID:<0x0>
        zRAID:<0x6b096>


Bill

---

### Post by wernerb1969 on 2017-06-30
Any ZFS experts??

---

### Post by ariek on 2017-07-15
Please try to use [*zpool  scrub*]("http://docs.oracle.com/cd/E23823_01/html/819-5461/gbbwa.html") to check the integrity of your data.

---

