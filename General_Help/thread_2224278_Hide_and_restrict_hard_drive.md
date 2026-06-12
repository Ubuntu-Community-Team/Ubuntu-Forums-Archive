---
title: "Hide and restrict hard drive"
date: 2014-05-15
forum: General Help
---

### Post by declan.marks on 2014-05-15
Is it possible to hide and restrict access to the hard drive. If it is how do I do it? I only want the user to access their own home folder. I do want the administrator to have access

---

### Post by Impavidus on 2014-05-15
You can limit access of users to partition on the hard drive. Arrange that the partitions are mentioned in /etc/fstab. Set the mount options such that the partitions doesn't automout at boot and only root has permission to mount it, or automount it but use mount options or Linux permissions (in case it's a Linux file system) to restrict access. You can separately limit read, write and execute access. So what's your situation exactly?

Users only need write access in their home directories and usually only have it there, but they also need read or execute access in many system directories.

---

### Post by HiImTye on 2014-05-15
here's a good place to start
[https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)

---

