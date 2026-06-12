---
title: "Permission for copied files from external hdd"
date: 2013-10-09
forum: General Help
---

### Post by denywinarto on 2013-10-09
Hi, I have a data server which is shared to a number of clients. I use external hdd to update the content of this server. Problem is, nautilus doesnt give correct permission to the newly added files, so i have to change the permission to 755 whenever i update the server, or else the client wont be able to access it.
Is there anyway to fix this? Thanks

---

### Post by nerdtron on 2013-10-10
What is the file system of the external hard drive? If it is NTFS, there nothing much you can do. The files in the drive will always have 777 permissions

---

### Post by mcduck on 2013-10-10
If you need to transfer files over FAT or NTFS filesystems, and wish for them to maintain their correct Linux permissions, you can compress them into a .tar.gz (for example) before copying to the non-Linux filsesystem. And then when you extract the archive on the server the permissions will be intact.

---

