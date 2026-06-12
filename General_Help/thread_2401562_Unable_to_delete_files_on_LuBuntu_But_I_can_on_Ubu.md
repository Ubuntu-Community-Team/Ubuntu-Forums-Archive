---
title: "Unable to delete files on LuBuntu But I can on Ubuntu?"
date: 2018-09-19
forum: General Help
---

### Post by neuman1812 on 2018-09-19
I have a shared directory on a nas drive for media files.  On my Ubuntu 18.04 computer I can delete files via the Desktop file manager without issue. 

I have a secondary laptop running Lubuntu 17.04 that Im unable to delete files with using the file manager,  but I can delete files using the terminal.

When i try an delete I get the error :

    Unable to find or create trash directory for /media/plex.....(directory path)

Both machines mount the drive with fstab with the exact same line. 

    192.168.1.103:/nfs/Media /media/plex nfs auto,_netdev,noatime,nolock,bg,intr,tcp,actimeo=1800 0 0

---

### Post by jdeiros on 2018-09-19
Permissions issue??

---

### Post by neuman1812 on 2018-09-19
Not sure.  The nas drive is setup with full read/write.  The Fstab line is the same on both machines,  but its only via the lubuntu filemanager that I can't delete.

I can delete if I navigate to the directory using the terminal on lubuntu.  So I dont think its a permissions issue.

---

### Post by geofftf on 2018-09-19
The error message suggests that PCManFM cannot find the Rubbish Bin. Does the Rubbish Bin have the same path in both Ubuntu and Lubuntu?  It would appear not:

[https://unix.stackexchange.com/questions/8790/where-is-the-trash-directory-for-pcmanfm-and-xfe](https://unix.stackexchange.com/questions/8790/where-is-the-trash-directory-for-pcmanfm-and-xfe)

[https://www.carnaghan.com/knowledge-base/where-is-the-trash-folder-located-in-ubuntu-16-04-lts/](https://www.carnaghan.com/knowledge-base/where-is-the-trash-folder-located-in-ubuntu-16-04-lts/)

That is probably the cause of the problem. The file manager for Ubuntu 18.04 is Nautilus 3.26. You could install that on Lubuntu, but the version in Software may have been customized for Lubuntu. That might cast some light on the problem.

---

### Post by oldos2er on 2018-09-22
Moved to General Help; Lubuntu is an officially supported "flavor" in addition to Ubuntu.

---

