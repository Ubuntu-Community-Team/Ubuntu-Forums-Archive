---
title: "Mount ISO, Permissions"
date: 2008-02-28
forum: General Help
---

### Post by picopir8 on 2008-02-28
I created an ISO of a directory as follows:

cd [directory that will be made into an iso]
mkisofs -r -V "$IMAGE_NAME" -cache-inodes -J -l -o myiso.iso .

However, when I mount the ISO using 

mkdir /mnt/mountpt
mount -o loop myiso.iso /mnt/mountpt

All of the the permissions for files/directories within the ISO were not preserved.  I understand that no files/directories within the ISO will have write privileges.  However, prior to creating the ISO some files/directories that had privileges of 500 or 550.  Yet when I mounted the ISO, the permissions were set to 555.  I do not know if they were manipulated in the process of creating the ISO or in the way in which I mounted the ISO.

I do not want "others" to have access to those files when the ISO is mounted.  Is there a way of mounting the ISO to preserve the privileges that I originally specified?

---

### Post by pointone on 2008-02-28
It's not possible to store file permissions on an ISO image, as far as I know; the filesystem doesn't support it. You can, however, easily change the permissions of the mount point to restrict access.

Another option would be to use the UDF filesystem when creating the image.

---

