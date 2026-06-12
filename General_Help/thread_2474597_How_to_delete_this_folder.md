---
title: "How to delete this folder"
date: 2022-05-03
forum: General Help
---

### Post by jmichaels29 on 2022-05-03
How to delete this folder (lost+found folder) that is password protected?  I know my password.

attached screenshot

---

### Post by #&amp;thj^% on 2022-05-03
The Purpose of the lost+found Directory

The lost&found directory contains files that have been deleted or lost in a disk operation. The files inside this directory have an inode, but they&#8217;re missing the corresponding filename that normally enables us to access files on the system. However, we can still access or restore a file&#8217;s data if its integrity is intact

The files inside this directory would have been regular files once with an inode and a filename. However, in rare cases, when a process opens a file for an operation, and somehow another process deletes the file when it&#8217;s still being used by the old process, it becomes just a data fragment. So, when there&#8217;s an improper shutdown or a kernel panic while the data is being used by the process, the data becomes obsolete.

Since the references to the file no longer exist and the file is no longer accessible normally, fsck turns the data back into a new file and deposits it in the lost+found directory.

Moral of the TL;DR you can remove it but not recommended.

---

### Post by grahammechanical on 2022-05-03
If you manage to delete the lost+found folder then the next time that fsck is run the fsck utility will create another lost+found folder. Do you know why Linux file systems have a lost+found folder?

[https://www.baeldung.com/linux/lost-found-directory](https://www.baeldung.com/linux/lost-found-directory)

[https://askubuntu.com/questions/165614/is-it-safe-to-delete-a-lostfound-folder](https://askubuntu.com/questions/165614/is-it-safe-to-delete-a-lostfound-folder)

A folder that is not empty cannot be deleted. We can delete files in the lost+found if we are happy to lose the data in those files.

Regards

---

