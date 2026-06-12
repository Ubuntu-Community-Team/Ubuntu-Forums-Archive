---
title: "Secure wipe on ext3/Reiser/Xfs"
date: 2005-05-04
forum: General Help
---

### Post by nocturn on 2005-05-04
Is there any way of securely wiping files of a journalled fs (apart from deleting the files, tarring everything up, wiping the partition, restoring)?

I know it is hard to do something like this because of the distributed nature of the journal.  Maybe it would be possible to do secure wiping again using the ReiserFSv4 plugin architecture?

---

### Post by nad on 2005-05-04
dd Can be your friend, But as you are doing direct disk writes be forewarned. Move the file to a temp directory and issue zeroes:

   1. dd if=/dev/zero of=/home/tmp
   2. sync
   3. rm /home/tmp
   4. sync

---

