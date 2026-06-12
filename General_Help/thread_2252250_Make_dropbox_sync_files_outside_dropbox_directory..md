---
title: "Make dropbox sync files outside dropbox directory."
date: 2014-11-10
forum: General Help
---

### Post by blazzer12 on 2014-11-10
I installed Dropbox. And everything is file until I realize I can only sync what's in the dropbox directory. 

The thing is I have a NTFS drive and I need them to be synced. While the symbolic link trick might work for ext3/4 file systems, there is no luck with NTFS drives.

It might be mainly due to NTFS not honoring Linux file system permissions and Dropbox thinking the files are outside it's privileges.

So is there a work around?

TL;DR : How to sync directories in NTFS partition to DROPBOX?

---

### Post by nerdtron on 2014-11-10
Haven't tried it for NTFS drives, but cant you change your local dropbox location?
I don't think creating symbolic link inside dropbox folder even with ext4 drives will be honored if they are outside dropbox folder.

---

