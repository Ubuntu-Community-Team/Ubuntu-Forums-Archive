---
title: "warning from rdiff-backup"
date: 2006-07-30
forum: General Help
---

### Post by jordilin on 2006-07-30
When performing backups with the rdiff-backup tool it shows me the following message:
> ACLs not supported by filesystem at 
> Extended attributes not supported by filesystem 
Although the backup is done flawlessly, what does it mean? The backups are done in an ext3 filesystem.

---

### Post by fabiand on 2006-07-30
Hey,

nomrally this happens, when your target filesystem doesn't support all "features" your source filesystem does. So, rdiff-backup wasn't able to set all the provided attributes.

In a home-environment, this shouldn't matter to much.

---

### Post by jordilin on 2006-07-31
the source and destination filesystems are both ext3 filesystems. I don't know why rdiff-backup warns. In any case, thanks, and as it performs my backups perfectly I will not care too much.

---

