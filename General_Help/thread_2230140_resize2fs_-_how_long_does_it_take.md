---
title: "resize2fs - how long does it take?"
date: 2014-06-17
forum: General Help
---

### Post by nathandetroit on 2014-06-17
Haven't found this information anywhere else, so I thought I would post it here.

I just finished resizing a RAID1 (using mdadm) volume from 2TB to 3TB as follows:

    sudo resize2fs /dev/md2

This process took about 50 minutes. I also note that it would have been better to use the -p option so I could monitor progress:

    sudo resize2fs -p /dev/md2

As a final note, my online research indicates that resizing a filesystem to make it smaller takes longer than making it larger, although I cannot verify this from personal experience.

---

