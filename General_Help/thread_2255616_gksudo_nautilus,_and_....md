---
title: "gksudo nautilus, and ..."
date: 2014-12-06
forum: General Help
---

### Post by Leonardo_Ciampa on 2014-12-06
Dear friends,

I booted up from Ubuntu 8, in order to recover files from my Mac PPC OS 10.4.  At first I wasn't allowed to see or copy any of my files.  Then I learned about gksudo nautilus, which saved my life!

HOWEVER, I still am not able to delete any Mac files.  Is there an additional command I can use?  If only I could delete a few Gig, I might actually be able to boot up the Mac!

With many thanks,

L.

---

### Post by steeldriver on 2014-12-06
Hello and welcome to the forums

AFAIK Mac (hfs+) partitions are mounted read-only by default: you will need to take extra steps to enable read-write access

See for example [hfsplus - Official Ubuntu Documentation]("https://help.ubuntu.com/community/hfsplus")

---

### Post by Leonardo_Ciampa on 2014-12-06
I opened a terminal and typed "diskutil list." It said "command not found."  I also tried "sudo diskutil disableJournal volumeName." That was not found, either.

---

### Post by steeldriver on 2014-12-06
diskutil is an OSX command - if you can't boot into OSX at all, then I don't know what to suggest - there have been a few projects to implement the disabling of journalling directly from Linux but I don't know their current status.

---

### Post by Leonardo_Ciampa on 2014-12-06
Ahh. I do find it strange, though, that Ubuntu is letting me read the files and copy them onto flash drives.  It just won't let me delete them.

---

### Post by steeldriver on 2014-12-06
Copying only requires read access whereas deleting requires write access - write access allows the possibility of filesystem corruption, so it's safer to mount "foreign" filesystems as read-only by default

---

