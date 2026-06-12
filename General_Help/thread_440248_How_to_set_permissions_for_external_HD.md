---
title: "How to set permissions for external HD?"
date: 2007-05-11
forum: General Help
---

### Post by nacnud on 2007-05-11
Hi all,

I have an external hard drive that contains all my music files (formatted as vfat).  It mounts fine, and I have read/write access.  (Unmounting/ejecting is a problem, but that's a separate issue.)

However, I need to change the permissions so that my music server software (slimserver) can access the music on the external drive.  Right now, it can't.  I've tried using nautilus as root to right click on the drive and alter the permissions, but each time I do so permissions immediately revert to what they were.

Should I create an entry for the drive in /etc/fstab?  If so, could someone guide me as to how to do that so that it has the correct permissions?  Or is there something else I should try?

Thanks for any help.

---

### Post by stchman on 2007-05-11
> **nacnud said:**
> Hi all,

I have an external hard drive that contains all my music files (formatted as vfat).  It mounts fine, and I have read/write access.  (Unmounting/ejecting is a problem, but that's a separate issue.)

However, I need to change the permissions so that my music server software (slimserver) can access the music on the external drive.  Right now, it can't.  I've tried using nautilus as root to right click on the drive and alter the permissions, but each time I do so permissions immediately revert to what they were.

Should I create an entry for the drive in /etc/fstab?  If so, could someone guide me as to how to do that so that it has the correct permissions?  Or is there something else I should try?

Thanks for any help.

I believe (and the other members here can correct me if I am wrong) that only EXT3 can have the permissions that you want.  FAT16/32 does not.

---

### Post by rich.bradshaw on 2007-05-11
Yep, FAT doesn't have permissions. NTFS doesn't have Unix/Linux permissions.

---

### Post by nacnud on 2007-05-11
Thanks.  So, if I understand correctly, I can make files on the drive read/write but not executable?

---

