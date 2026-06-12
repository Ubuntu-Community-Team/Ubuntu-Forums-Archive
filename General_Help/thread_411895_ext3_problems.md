---
title: "ext3 problems"
date: 2007-04-17
forum: General Help
---

### Post by Kilbasar on 2007-04-17
I've recently started having a problem with one of my ext3 partitions. I can mount it, but when I try going into it and running ls, I get a segmentation fault. Nothing seems to be able to access the files there. However, if I mount the partition as ext2 instead of ext3, everything is fine, and I can access everything. This leads me to believe there's a problem with the ext3 journal. Is there any way to rebuild the journal? Or maybe I'm completely wrong. Any help would be appreciated.

- Jason

---

### Post by psusi on 2007-04-17
I'd say unmount it and run fsck on it.

---

### Post by anaconda on 2007-04-17
yep.. and the command is:
fsck -f /dev/hda1
just change the "hda1" to point to the partition you want to check.. could be eg. sdaX

---

### Post by Kilbasar on 2007-04-17
Thanks a lot! Worked like a charm. I forgot that hard drive errors are what fsck is there for...

- Jason

---

