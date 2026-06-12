---
title: "RSYNCH Help"
date: 2007-06-26
forum: General Help
---

### Post by strange_cathect on 2007-06-26
Hello,

I'm using the frontend GRSYNCH to do a backup of some files.  Specifically, I want to backup my /home folder so that I could, if necessary, just transfer the backup back to my /home partition.

1. Can someone tell me what the "verbose" selection means?

2. What do I need to select (in grsynch) when trying to make a perfect copy of these files?

---

### Post by dmonner on 2007-06-26
1. The "verbose" selection just means that, once the file transfer begins, the program will show you more information about its progress and any errors it encounters. Whether it is checked or not should have no effect on the actual transfer process itself.

2. To make exact copies of files, you will want to check all of the following:
Basic Options:
  - Preserve Time
  - Preserve Owner
  - Preserve Permissions
  - Preserve Group
Advanced Options:
  - Preserve Devices
  - Copy Symlinks as Symlinks

The above is all basically equivalent to the commandline: "rsync -a <home directory> <backup directory>"

You may also want Delete on Destination from Basic Options, if you want your backup area to maintain an exact copy of your home directory; if you don't check Delete on Destination, any files you delete from your home directory will continue to exist in your backup.

With the Delete on Destination option checked, the equivalent commandline would be "rsync -a --delete <home directory> <backup directory>".

Hope that helps!

---

