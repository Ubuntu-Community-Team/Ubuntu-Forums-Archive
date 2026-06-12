---
title: "rsync deleted everything on an ntfs partition"
date: 2008-02-28
forum: General Help
---

### Post by Oswald1 on 2008-02-28
Greetings,

To keep it short, this is what happened:

I ran rsync with the command:

```

sudo rsync - a -e ssh /home/ username@backupcomp:/backupdir/ 

```

The backupdir on the backupcomputer is an ntfs drive. As a result the backupdir contains all the directories from the computer i was trying to back up but they are all empty. As an addition there were some other stuff in the backupdir before doing this, but they're all gone too (not even empty dirs)! Ouch. Other dirs in the ntfs drive seem to be OK.

I tried running ntfsundelete on the drive to see if some of the vanished files could be found to no avail. 

The frustrating thing here is that of course I had some files over there waiting to be copied elsewhere after a system upgrade and nowhere else.

Any help would be TRULY appreciated as right now I have quite an uncomfortable feeling in my stomach.


edit: As an addition rsync gave lot's of warnings about not being able to set times on files while doing its business.

---

### Post by Oswald1 on 2008-02-28
OK it seems that I'm just panicking about those lost files and they seem to be in fact in another location. I'm a bit jumpy about these backups...

Still the backup didn't copy any files so if someone can tell me what's wrong there I'd be grateful.

---

### Post by djgrandmarquis on 2008-02-28
I have had very bad experiences trying to use rsync with ntfs. (This is what prompted me to format all my drives as ext3 and ditch Windows altogether.) Perhaps it could be an issue with the way ntfs handles time stamps. However, I have never used rsync remotely with ssh, so there may or may not be a problem there.

---

