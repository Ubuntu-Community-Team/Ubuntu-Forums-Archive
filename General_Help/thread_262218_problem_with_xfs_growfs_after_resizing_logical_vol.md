---
title: "problem with xfs_growfs after resizing logical volume"
date: 2006-09-21
forum: General Help
---

### Post by elektronaut on 2006-09-21
Hi,

I'm using a logical volume which is exclusively used by VMWare. While running a virtual machine, VMWare complained about not having enough disk space. I first ignored this, then Windows in the virtual machine crashed. I couldn't stop VMWare afterwards, it said the virtual machine would still be running. So I killed the process. Then I extended the logical volume using lvextend, and tried to also extend the file system using xfs_growfs. But this gave me the error that there wouldn't be any memory left on the partition. What can I do?

---

### Post by elektronaut on 2006-09-22
Problem is solved. I simply copied the data to an external disk, removed and recreated the logical partition and copied the backup back.

---

