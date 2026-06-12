---
title: "Deja Dup Issue"
date: 2024-04-23
forum: General Help
---

### Post by speartip on 2024-04-23
New install of 24.04.
Tried running Deja Dup to my external drive with about 500GB free space. The Backup is about 280GB in size, but the backup stalls with the message I need at least 576GB of space to backup.
Any ideas on the issue please?

---

### Post by TheFu on 2024-04-24
Did you check that the target storage is over 576GB in size?

---

### Post by deadflowr on 2024-04-24
Check preferences > folders and see what is set to be backed up and what is set to be ignored for backup.
Also check mounts to see if anything is mounted somewhere that is part of the backup setting in the preferences.

---

### Post by dragonfly41 on 2024-04-24
Try LuckyBackup in "dry run" mode to inspect any errors encountered during "dry run".

---

### Post by donald187 on 2024-04-25
Any chance that Deja Dup is going to make a second full backup (used to be in three months time) and it wants room to do that?

---

### Post by speartip on 2024-04-25
> **TheFu said:**
> Did you check that the target storage is over 576GB in size?
The Target has 500GB free space, but the backup size was only 280GB so it shouldn't have been an issue.

---

### Post by speartip on 2024-04-25
> **deadflowr said:**
> Check preferences > folders and see what is set to be backed up and what is set to be ignored for backup.
Also check mounts to see if anything is mounted somewhere that is part of the backup setting in the preferences.
The total size of the folder being backed up was 417.2GB with 133GB of that set to be ignored.

---

### Post by speartip on 2024-04-25
> **donald187 said:**
> Any chance that Deja Dup is going to make a second full backup (used to be in three months time) and it wants room to do that?
This was a first full Backup.

---

### Post by speartip on 2024-04-25
Does anyone know where Deja Dup keeps its config files? I'll try deleting everything and start with a clean config.

---

### Post by speartip on 2024-04-25
Just another strange thing about this. I calculated exactly the size of the backup, which is 287.4 GB. And the error message is "Backup location does not have enough free space. Try using a location with at least 574.8 GB.
Exactly double the backup size. I'm stumped.

---

### Post by TheFu on 2024-04-25
> **speartip said:**
> Just another strange thing about this. I calculated exactly the size of the backup, which is 287.4 GB. And the error message is "Backup location does not have enough free space. Try using a location with at least 574.8 GB.
Exactly double the backup size. I'm stumped.

Out of inodes, perhaps?  This is unlikely on a disk that size with ext4 as the file system, but stranger things have happened.
**df -i** and **df -Th** are your friends here.

---

### Post by donald187 on 2024-04-25
> **speartip said:**
> This was a first full Backup.

I assumed so.  As I'm sure you know Deja Dup (Duplicity) can't just make incremental backups for forever.  It has to do a second full backup at some point.  But it won't have enough space.  I'm just suggesting that Deja Dup knows this and is preemptively saying that there's not (won't be) enough room.  But who knows.  It might be interesting to see if it will back up something with size less than half the size of your backup disk (less several GB to be safe).

---

### Post by donald187 on 2024-04-25
> **speartip said:**
> Does anyone know where Deja Dup keeps its config files? I'll try deleting everything and start with a clean config.

Duplicity keeps some files in .cache in the duplicity folder.  Namely the manifest and signature files.  When I want to start over in Duplicity I delete the appropriate sub-folder.   Deja Dup also has settings--I have used the dconf-editor to reset settings back to their defaults.  I don't know if there are other default settings somewhere.  Under org.gnome.deja-dup I believe.  Not sure about punctuation there.

---

### Post by dragonfly41 on 2024-04-25
In synaptic I installed
dconf-cli
dconf-editor
Opening dconf-editor (with warnings) shows deja-dup settings.

---

### Post by speartip on 2024-04-26
> **donald187 said:**
> I assumed so.  As I'm sure you know Deja Dup (Duplicity) can't just make incremental backups for forever.  It has to do a second full backup at some point.  But it won't have enough space.  I'm just suggesting that Deja Dup knows this and is preemptively saying that there's not (won't be) enough room.  But who knows.  It might be interesting to see if it will back up something with size less than half the size of your backup disk (less several GB to be safe).

After Googling around, apparerently this is the issue. In all the years I've used Deja Dup I've not come across this before, but apparently it does indeed need double the size of the backup otherwise it will stall.
That's space that I do not have. I never appeared to have this issue in 22.04, so it must be something new in the 24.04 version of DejaDup.
For now I'm trying rdiff-backup instead.

---

