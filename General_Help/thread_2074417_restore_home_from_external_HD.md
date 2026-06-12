---
title: "restore /home from external HD"
date: 2012-10-21
forum: General Help
---

### Post by aspergerian on 2012-10-21
My Acer-1410 was running Ubuntu 9.04 (64 bit) with /home on a separate partition. I backed up /home to an external HD and wonder how best to restore the external HD's /home folder to the /home folder on the Acer now with a clean install of Xubuntu 12.04.1.

If possible, I would prefer to avoid creating a new user on the Acer. Suggestions appreciated.

---

### Post by CaptainMark on 2012-10-21
If you want to keep all your configuration files and they are intact on the external hdd```
rsync -av /path/to/exthdd/home/ /home/
```If your user has the same name as originally your new install should just assign the newly found home folder to your current user,

---

### Post by aspergerian on 2012-10-23
Solved [couldn't find toggle for solved].

I tried Grsync but couldn't correctly specify source and destination directories. Xubuntu's File Manager enabled me to open source and destination home folders in separate windows. Then, File Manager's copy-all enabled me to copy all /home files from old Thunderbird on external HD to /home on newly installed Xubuntu.

As this occurred, the process renamed {old} .thunderbird to .mozilla-thunderbird {now in new /home} while leaving {new} .thunderbird in the Xubuntu /home directory. See attached images, each with its own ....default identifier.

I then relabeled .thunderbird to .thunderbird-new (thus disabling it) and renamed .mozilla-thunderbird to .thunderbird (thus enabling it). 

When I re-opened TBird, the old emails, folders, and subfolders were restored.

---

