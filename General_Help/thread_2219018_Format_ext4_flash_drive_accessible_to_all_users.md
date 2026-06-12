---
title: "Format ext4 flash drive accessible to all users"
date: 2014-04-22
forum: General Help
---

### Post by lou6 on 2014-04-22
I've formatted a flash drive to ext4 (for rsync use) but the other user on the system can't access it. We don't have this problem with ntfs flash drives - they are automatically usable by all. Some responses say to modify etc/fstab but 14.04 does not seem to have these entries.

Can some wise person help? TIA

---

### Post by lou6 on 2014-04-22
Never mind - I solved the problem by taking ownership with chown and changing permissions in Nautilus.

---

