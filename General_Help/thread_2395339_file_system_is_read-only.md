---
title: "file system is read-only"
date: 2018-06-30
forum: General Help
---

### Post by shambakey1 on 2018-06-30
Hi

I'm using ubuntu 18.04, and recently I'm facing a strange problem. All partitions are read-only. I tried "chmod" but it failed. I then tried modifying fstab for each partition as follows:
UUID=36C2C9A9C2C96E25 /f ntfs rw,user,exec,umask=000,gid=46 0 0
but it also failed despite "ls -l" shows that the following:
drwxrwxrwx   1 root plugdev  4096 Jun 29 18:23 f
but still, I cannot create a directory or copy files to the partition because of "Read-only file system"

Please help

Regards

---

### Post by vanadium on 2018-06-30
You can't create files or directories on any linux system except in your own home directory, or wherever else the administrator has granted you permissions.

---

### Post by oldos2er on 2018-06-30
Moved to *General Help*.

---

### Post by SeijiSensei on 2018-06-30
if the Linux filesystem has errors that need to be fixed, it will be mounted read-only.  Usually rebooting will fix this problem since Ubuntu checks to see if the filesystem needs to be repaired at boot.  Have you rebooted?  Still have the problem?

---

### Post by Impavidus on 2018-07-01
You say that all partitions are read-only, then give an example of an ntfs partition. If the ntfs partitions were not cleanly unmounted in Windows, they can only be mounted read-only. Make sure all settings in Windows for hibernation/fast startup are off. Windows may turn them on again as part of its updates.

The root partition of your operating system (and probably your /home partition, if you have one; these are obviously not ntfs partitions) may get mounted read-only if there are errors. When you reboot it should run some checks to fix it

---

