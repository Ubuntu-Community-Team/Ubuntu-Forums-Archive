---
title: "fsck stalled what do I do?"
date: 2007-05-03
forum: General Help
---

### Post by muguwmp67 on 2007-05-03
I'm running an fsck right now and its been on the same line for 25 minutes or so.

Is it hung?  If so, what do I do to safely exit it?

```
$ fsck.ext3 /dev/sdg1
e2fsck 1.40-WIP (14-Nov-2006)
Group descriptors look bad... trying backup blocks...
/dev/sdg1 was not cleanly unmounted, check forced.
Pass 1: Checking inodes, blocks, and sizes

```

---

### Post by tcarradine on 2007-05-03
did your system crash? a long hang could be a sign of your drive dying. you might want to boot from the CD and backup your data.

Tim

---

