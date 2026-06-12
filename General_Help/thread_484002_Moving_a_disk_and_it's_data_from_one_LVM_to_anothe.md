---
title: "Moving a disk and it's data from one LVM to another"
date: 2007-06-25
forum: General Help
---

### Post by feenster on 2007-06-25
Hi all,
I am trying to simplify my storage on a Ubuntu 7.04 server that I run. It currently has 2 x 500GB SATA drives in a RAID-1, setup as an LVM (called "user_data"). I've also got 2 x 300GB SATA drives in a RAID-1, which I have split in half, and started to build up a new LVM from (called "users"). Therefore, there is now a 600GB LVM, with 300GB free space.

What I want to do, is move one of the 500GB disks into the new LVM, but without trashing the data, and having to re-copy it. Is this possible? I know it would be easier to use fresh disks and re-copy the data, but that isn't possible in the situation.

Cheers,
  Matt

---

### Post by feenster on 2007-06-25
Any ideas anyone? I've had a good Google, and their is a lot out there about setting up LVM's, but not about taking them to pieces.

Matt

---

