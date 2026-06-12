---
title: "cannot find name for group ID 126"
date: 2008-02-27
forum: General Help
---

### Post by jaspergreen on 2008-02-27
I am trying to chroot the directory /opt/ltsp/i386/
 and am getting the message:
cannot find name for group ID 126

The group ID 126 belongs to the group fuse.

Anytbody have any ideas?

---

### Post by jeffus_il on 2008-02-27
Is the groupid defined in two group files, one in the system and one in the chroot system? Are both defined?

---

### Post by superedgaryo on 2008-05-16
> **jeffus_il said:**
> Is the groupid defined in two group files, one in the system and one in the chroot system? Are both defined?

 How I can know if groupid is defined in boot systems?

---

