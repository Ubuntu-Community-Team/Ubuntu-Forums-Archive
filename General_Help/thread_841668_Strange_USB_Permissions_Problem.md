---
title: "Strange USB Permissions Problem"
date: 2008-06-26
forum: General Help
---

### Post by strange_cathect on 2008-06-26
Hello all,

Weird problem. I have a FAT USB drive that mounts perfectly to the desktop when I plug it in. I can drag files there, delete, the whole ballgame.

However, I thought I'd start using GRSYNC to synchronize a folder on the USB and my Desktop since I often work on another computer away from home.

When I try this, I run into permission problem errors. Why is rsync having problems when I can do this manually through drag-and-drop?

:confused:

---

### Post by chrisccoulson on 2008-06-26
You need to be a bit more specific. The output from Grsync is quite verbose. Could you please copy and paste the messages here.

Thanks

---

### Post by strange_cathect on 2008-06-26
> **chrisccoulson said:**
> You need to be a bit more specific. The output from Grsync is quite verbose. Could you please copy and paste the messages here.

Thanks

My bad:

All I get is "failed: Operation not permitted" and the string concludes with:

> rsync error: some files could not be transferred (code 23) at main.c(977) [sender=2.6.9]

Thanks for the reply!

---

### Post by chrisccoulson on 2008-06-26
What are your source and destination locations? What are the permissions on those folders? Is there any more output from Grsync? There is normally quite a lot more output from it, with the failed folders highlighted in red.

---

### Post by chrisccoulson on 2008-06-26
Also, it might be useful if you save a Grsync session using the settings that are causing this error and then post your ~/.grsync/grsync.ini file. You can do this in Grsync by setting it up in the configuration that causes this error, and then pressing the 'Add' button

---

### Post by strange_cathect on 2008-06-26
rsync: chgrp "/media/John Barley/Dissertation/." failed: Operation not permitted (1)
rsync: chgrp "/media/John Barley/Dissertation/Backups" failed: Operation not permitted (1)
rsync: chgrp "/media/John Barley/Dissertation/Manuscript" failed: Operation not permitted (1)
rsync: chgrp "/media/John Barley/Dissertation/Manuscript/Chapter Four-- Tracks" failed: Operation not permitted (1)
rsync: chgrp "/media/John Barley/Dissertation/Manuscript/Chapter Four-- Tracks/Archive" failed: Operation not permitted (1)
rsync: chgrp "/media/John Barley/Dissertation/Manuscript/Chapter One Brown" failed: Operation not permitted (1)
rsync: chgrp "/media/John Barley/Dissertation/Manuscript/Chapter One Brown/Archive" failed: Operation not permitted (1)
rsync: chgrp "/media/John Barley/Dissertation/Manuscript/Chapter One Brown/Chapter" failed: Operation not permitted (1)
rsync: chgrp "/media/John Barley/Dissertation/Manuscript/Chapter One Brown/Images" failed: Operation not permitted (1)
rsync: chgrp "/media/John Barley/Dissertation/Manuscript/Chapter One Brown/Images/Carey Seven Ranges Plat 1811" failed: Operation not permitted (1)
rsync: chgrp "/media/John Barley/Dissertation/Manuscript/Chapter One Brown/Images/Jaque Bellin Philadelphia 1764" failed: Operation not permitted (1)
rsync: chgrp "/media/John Barley/Dissertation/Manuscript/Chapter One Brown/Images/Scull and Heap" failed: Operation not permitted (1)
rsync: chgrp "/media/John Barley/Dissertation/Manuscript/Chapter One Brown/Maps Research Images" failed: Operation not permitted (1)
rsync: chgrp "/media/John Barley/Dissertation/Manuscript/Chapter One Brown/Research" failed: Operation not permitted (1)
rsync: chgrp "/media/John Barley/Dissertation/Manuscript/Chapter Three -- Squatter" failed: Operation not permitted (1)
rsync: chgrp "/media/John Barley/Dissertation/Manuscript/Chapter Three -- Squatter/Archive" failed: Operation not permitted (1)
rsync: chgrp "/media/John Barley/Dissertation/Manuscript/Chapter Two--Cooper" failed: Operation not permitted (1)
rsync: chgrp "/media/John Barley/Dissertation/Manuscript/Chapter Two--Cooper/Archive" failed: Operation not permitted (1)
rsync: chgrp "/media/John Barley/Dissertation/Manuscript/Introduction" failed: Operation not permitted (1)
rsync: chgrp "/media/John Barley/Dissertation/Manuscript/Introduction/Archive" failed: Operation not permitted (1)
rsync: chgrp "/media/John Barley/Dissertation/Manuscript/NorthwestTerritory" failed: Operation not permitted (1)
rsync: chgrp "/media/John Barley/Dissertation/Tertiary" failed: Operation not permitted (1)
rsync: chgrp "/media/John Barley/Dissertation/Tertiary/Backup" failed: Operation not permitted (1)
rsync: chgrp "/media/John Barley/Dissertation/Tertiary/Bibliography" failed: Operation not permitted (1)
rsync: chgrp "/media/John Barley/Dissertation/Tertiary/Grants" failed: Operation not permitted (1)
rsync: chgrp "/media/John Barley/Dissertation/Tertiary/Ideas" failed: Operation not permitted (1)
rsync: chgrp "/media/John Barley/Dissertation/Tertiary/Images" failed: Operation not permitted (1)
rsync: chgrp "/media/John Barley/Dissertation/Tertiary/Images/US Territorial Growth" failed: Operation not permitted (1)
rsync: chgrp "/media/John Barley/Dissertation/Tertiary/Print Me" failed: Operation not permitted (1)
rsync: chgrp "/media/John Barley/Dissertation/Tertiary/Print Me/Johnson v. M'Intosh_files" failed: Operation not permitted (1)
rsync: chgrp "/media/John Barley/Dissertation/Tertiary/Prospectus" failed: Operation not permitted (1)
rsync: chgrp "/media/John Barley/Dissertation/Tertiary/Prospectus/Backup" failed: Operation not permitted (1)
rsync: chgrp "/media/John Barley/Dissertation/Tertiary/Prospectus/Work Zone" failed: Operation not permitted (1)
rsync: chgrp "/media/John Barley/Dissertation/Tertiary/Related Documents" failed: Operation not permitted (1)
rsync: chgrp "/media/John Barley/Dissertation/Tertiary/Related Documents/Orals" failed: Operation not permitted (1)
rsync: chgrp "/media/John Barley/Dissertation/Tertiary/Related Documents/Orals/Buell" failed: Operation not permitted (1)
rsync: chgrp "/media/John Barley/Dissertation/Tertiary/Related Documents/Orals/Documents" failed: Operation not permitted (1)
rsync: chgrp "/media/John Barley/Dissertation/Tertiary/Related Documents/Orals/Documents/E-Texts" failed: Operation not permitted (1)
rsync: chgrp "/media/John Barley/Dissertation/Tertiary/Related Documents/Orals/Example Lists" failed: Operation not permitted (1)
rsync: chgrp "/media/John Barley/Dissertation/Tertiary/Related Documents/Orals/Images" failed: Operation not permitted (1)
rsync: chgrp "/media/John Barley/Dissertation/Tertiary/Related Documents/Orals/Note System" failed: Operation not permitted (1)
rsync: chgrp "/media/John Barley/Dissertation/Tertiary/Related Documents/Orals/Oral Papers" failed: Operation not permitted (1)
rsync: chgrp "/media/John Barley/Dissertation/Tertiary/Related Documents/Orals/Reading List" failed: Operation not permitted (1)
rsync: chgrp "/media/John Barley/Dissertation/Tertiary/Related Documents/Orals/Squatter and Ramona" failed: Operation not permitted (1)
rsync: chgrp "/media/John Barley/Dissertation/Tertiary/Related Documents/Related Stuff" failed: Operation not permitted (1)
rsync: chgrp "/media/John Barley/Dissertation/Tertiary/Related Documents/Republicanism" failed: Operation not permitted (1)
rsync: chgrp "/media/John Barley/Dissertation/Tertiary/Research Notes" failed: Operation not permitted (1)
rsync: chgrp "/media/John Barley/Dissertation/Working Folder" failed: Operation not permitted (1)
rsync: chgrp "/media/John Barley/Dissertation/Working Folder/Things to Read" failed: Operation not permitted (1)
rsync: chgrp "/media/John Barley/Dissertation/." failed: Operation not permitted (1)
rsync: chgrp "/media/John Barley/Dissertation/Backups" failed: Operation not permitted (1)
rsync: chgrp "/media/John Barley/Dissertation/Manuscript" failed: Operation not permitted (1)
rsync: chgrp "/media/John Barley/Dissertation/Manuscript/Chapter Four-- Tracks" failed: Operation not permitted (1)
rsync: chgrp "/media/John Barley/Dissertation/Manuscript/Chapter Four-- Tracks/Archive" failed: Operation not permitted (1)
rsync: chgrp "/media/John Barley/Dissertation/Manuscript/Chapter One Brown" failed: Operation not permitted (1)
rsync: chgrp "/media/John Barley/Dissertation/Manuscript/Chapter One Brown/Archive" failed: Operation not permitted (1)
rsync: chgrp "/media/John Barley/Dissertation/Manuscript/Chapter One Brown/Chapter" failed: Operation not permitted (1)
rsync: chgrp "/media/John Barley/Dissertation/Manuscript/Chapter One Brown/Images" failed: Operation not permitted (1)
rsync: chgrp "/media/John Barley/Dissertation/Manuscript/Chapter One Brown/Images/Carey Seven Ranges Plat 1811" failed: Operation not permitted (1)
rsync: chgrp "/media/John Barley/Dissertation/Manuscript/Chapter One Brown/Images/Jaque Bellin Philadelphia 1764" failed: Operation not permitted (1)
rsync: chgrp "/media/John Barley/Dissertation/Manuscript/Chapter One Brown/Images/Scull and Heap" failed: Operation not permitted (1)
rsync: chgrp "/media/John Barley/Dissertation/Manuscript/Chapter One Brown/Maps Research Images" failed: Operation not permitted (1)
rsync: chgrp "/media/John Barley/Dissertation/Manuscript/Chapter One Brown/Research" failed: Operation not permitted (1)
rsync: chgrp "/media/John Barley/Dissertation/Manuscript/Chapter Three -- Squatter" failed: Operation not permitted (1)
rsync: chgrp "/media/John Barley/Dissertation/Manuscript/Chapter Three -- Squatter/Archive" failed: Operation not permitted (1)
rsync: chgrp "/media/John Barley/Dissertation/Manuscript/Chapter Two--Cooper" failed: Operation not permitted (1)
rsync: chgrp "/media/John Barley/Dissertation/Manuscript/Chapter Two--Cooper/Archive" failed: Operation not permitted (1)
rsync: chgrp "/media/John Barley/Dissertation/Manuscript/Introduction" failed: Operation not permitted (1)
rsync: chgrp "/media/John Barley/Dissertation/Manuscript/Introduction/Archive" failed: Operation not permitted (1)
rsync: chgrp "/media/John Barley/Dissertation/Manuscript/NorthwestTerritory" failed: Operation not permitted (1)
rsync: chgrp "/media/John Barley/Dissertation/Tertiary" failed: Operation not permitted (1)
rsync: chgrp "/media/John Barley/Dissertation/Tertiary/Backup" failed: Operation not permitted (1)
rsync: chgrp "/media/John Barley/Dissertation/Tertiary/Bibliography" failed: Operation not permitted (1)
rsync: chgrp "/media/John Barley/Dissertation/Tertiary/Grants" failed: Operation not permitted (1)
rsync: chgrp "/media/John Barley/Dissertation/Tertiary/Ideas" failed: Operation not permitted (1)
rsync: chgrp "/media/John Barley/Dissertation/Tertiary/Images" failed: Operation not permitted (1)
rsync: chgrp "/media/John Barley/Dissertation/Tertiary/Images/US Territorial Growth" failed: Operation not permitted (1)
rsync: chgrp "/media/John Barley/Dissertation/Tertiary/Print Me" failed: Operation not permitted (1)
rsync: chgrp "/media/John Barley/Dissertation/Tertiary/Print Me/Johnson v. M'Intosh_files" failed: Operation not permitted (1)
rsync: chgrp "/media/John Barley/Dissertation/Tertiary/Prospectus" failed: Operation not permitted (1)
rsync: chgrp "/media/John Barley/Dissertation/Tertiary/Prospectus/Backup" failed: Operation not permitted (1)
rsync: chgrp "/media/John Barley/Dissertation/Tertiary/Prospectus/Work Zone" failed: Operation not permitted (1)
rsync: chgrp "/media/John Barley/Dissertation/Tertiary/Related Documents" failed: Operation not permitted (1)
rsync: chgrp "/media/John Barley/Dissertation/Tertiary/Related Documents/Orals" failed: Operation not permitted (1)
rsync: chgrp "/media/John Barley/Dissertation/Tertiary/Related Documents/Orals/Buell" failed: Operation not permitted (1)
rsync: chgrp "/media/John Barley/Dissertation/Tertiary/Related Documents/Orals/Documents" failed: Operation not permitted (1)
rsync: chgrp "/media/John Barley/Dissertation/Tertiary/Related Documents/Orals/Documents/E-Texts" failed: Operation not permitted (1)
rsync: chgrp "/media/John Barley/Dissertation/Tertiary/Related Documents/Orals/Example Lists" failed: Operation not permitted (1)
rsync: chgrp "/media/John Barley/Dissertation/Tertiary/Related Documents/Orals/Images" failed: Operation not permitted (1)
rsync: chgrp "/media/John Barley/Dissertation/Tertiary/Related Documents/Orals/Note System" failed: Operation not permitted (1)
rsync: chgrp "/media/John Barley/Dissertation/Tertiary/Related Documents/Orals/Oral Papers" failed: Operation not permitted (1)
rsync: chgrp "/media/John Barley/Dissertation/Tertiary/Related Documents/Orals/Reading List" failed: Operation not permitted (1)
rsync: chgrp "/media/John Barley/Dissertation/Tertiary/Related Documents/Orals/Squatter and Ramona" failed: Operation not permitted (1)
rsync: chgrp "/media/John Barley/Dissertation/Tertiary/Related Documents/Related Stuff" failed: Operation not permitted (1)
rsync: chgrp "/media/John Barley/Dissertation/Tertiary/Related Documents/Republicanism" failed: Operation not permitted (1)
rsync: chgrp "/media/John Barley/Dissertation/Tertiary/Research Notes" failed: Operation not permitted (1)
rsync: chgrp "/media/John Barley/Dissertation/Working Folder" failed: Operation not permitted (1)
rsync: chgrp "/media/John Barley/Dissertation/Working Folder/Things to Read" failed: Operation not permitted (1)
rsync error: some files could not be transferred (code 23) at main.c(977) [sender=2.6.9]

---

### Post by chrisccoulson on 2008-06-26
Is the destination a FAT partition? If it is, then my guess is that you have checked 'Preserve group' in Grsync, and it is failing because the FAT partition doesn't support Linux file permissions and ownership

---

### Post by strange_cathect on 2008-06-26
Thank you, Bender! I mean Chris. Works like a charm now.

---

### Post by chrisccoulson on 2008-06-26
No probs;)

---

