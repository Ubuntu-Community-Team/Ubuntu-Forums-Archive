---
title: "SFTP chroot uploaded file permissions"
date: 2013-10-22
forum: General Help
---

### Post by thuizt on 2013-10-22
Hello experts,

We have a SFTP and Samba server running on Ubuntu 12.04.
Everything works great but the file permissions on uploaded files.
We have multiple SFTP users who can up/download files from SFTP
Through Samba office users can modify the files in the users home directories.
The SFTP user is owner and the Samba users have access through a group.

However when a SFTP users uploads a file it gets Read-Only permissions for the group so Samba users cannot modify the uploaded files.

How can we arrange that uploaded files get Read-Write for the owner and the group ??

Any help greatly appreciated.

---

