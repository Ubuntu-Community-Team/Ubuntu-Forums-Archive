---
title: "Changing Owner/Permissions"
date: 2007-11-08
forum: General Help
---

### Post by lyxerd on 2007-11-08
This may seem like a repeat question, but I have been going through these forums and google for hours and nothing seems to work.  I have four external hard drives from my mac that I need access to, one FAT, one NTFS, one HFS+, and one ext2.  The FAT one has me as the owner and i have write permissions.  The others all have root listed as the owner and there seems to be nothing i can do to change this,

I've tried sudo chown <myname> /media/TWO, i've tried sudo chown 777 /media/FOUR, i've logged in as root and tried these; Nothing ever changes! Am I missing something completely obvious?

---

### Post by bettlebrox on 2007-11-08
You have to change the mount options in /etc/fstab to affect the ownership of files on a non-Linux filesystem (make a backup of the file before you do any changes as can hose your system).

Luck
Mick

---

### Post by lyxerd on 2007-11-08
Thanks, that worked for the ext and ntfs drives but the hfs+ drive is still unwriteable.  Is there anything special I need to download to write to hfs+ drives? I remember on macosx I had to download a third party package to write to ntfs drives.

---

### Post by Maestro23 on 2007-11-08
> **lyxerd said:**
> Thanks, that worked for the ext and ntfs drives but the hfs+ drive is still unwriteable.  Is there anything special I need to download to write to hfs+ drives? I remember on macosx I had to download a third party package to write to ntfs drives.

Don't have a MAC, but saw your post and did a quick google (comes in handy sometimes :smile:). Found the following article:
[http://fosswire.com/2007/09/12/dealing-with-mac-formatted-drives-on-linux/](http://fosswire.com/2007/09/12/dealing-with-mac-formatted-drives-on-linux/)

Which led me to search the Repositories.  There are 2 packages in Ubuntu that might help you.

hfsutils - Tools for reading and writing Macintosh volumes
hfsutils-tcltk - Tcl/Tk interfaces for reading and writing Macintosh volumes

Search for them in Synpatic.

Good luck.

---

