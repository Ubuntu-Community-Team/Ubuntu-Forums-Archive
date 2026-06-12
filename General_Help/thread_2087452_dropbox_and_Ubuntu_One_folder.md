---
title: "dropbox and Ubuntu One folder"
date: 2012-11-23
forum: General Help
---

### Post by Ubunteras on 2012-11-23
Hi all,

I want to have the folders of dropbox and Ubuntu One in a NTFS partition. In both apps are other folders than home greyed out. I thought it has to do with fstab, so I ve modified the file to mount on boot the NTFS partition. But the problem persists. So, it possible at all to have these 2 folders in a folder other than home and how? How should fstab be configured?


thanks in advance

---

### Post by forestG on 2012-12-07
I think your problem is with read and write rights. The only folder that a user has certainly read and write rights is the user's home folder. Give the folder that the partition is mounted on read and write rights. A package that might help is the ntfs-config. You can install the package using the command "sudo apt-get install ntfs-config"

---

