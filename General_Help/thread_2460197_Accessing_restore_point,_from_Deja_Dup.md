---
title: "Accessing restore point, from Deja Dup"
date: 2021-04-04
forum: General Help
---

### Post by christine4 on 2021-04-04
Using Ubuntu 20.04 I wanted to restore to an earlier point (as far back as 2019). Whenever I change anything, I always do a new back-up, in case anything goes wrong. Which I did yesterday. Restoring back to 2019 was successful. Unfortunately it didn't fix what I needed. So I went to restore to the most recent save (yesterday) again. Only Files Manager identified restore points from 2018 and 2019 - when I know the recent backups, were from 2020-2021. I'm assuming the back-up from yesterday, is still located on my actual hard-drive, but Files Manager has been restored to an earlier point, that doesn't recognise it.

Is there a way to see my newest restore point from yesterday, on my external hard-drive? If so, how do I go about restoring it?

Cheers to anyone who can steer me in the right direction.=d>

---

### Post by deadflowr on 2021-04-05
My understanding is that if any part of a backup is corrupted then none of the backup is available.
You can use duplicity commands to check.
Something like the collection-status command may help.
typically runs like
```
duplicity collection-status file:///path/to/backup/location
```
cleaner example
```
duplicity collection-status file:///media/username/BackupsDriveName/BackupFolderName
```

You can also look at this: [https://wiki.gnome.org/Apps/DejaDup/Help/Restore/WorstCase]("https://wiki.gnome.org/Apps/DejaDup/Help/Restore/WorstCase")

also, more on duplicity here: [http://duplicity.nongnu.org/vers8/duplicity.1.html]("http://duplicity.nongnu.org/vers8/duplicity.1.html")

---

### Post by christine4 on 2021-04-06
I appreciate the time you took to supply some options. I've tried both codes, and it returns:

 > Giving up after 1 attempts. FileNotFoundError: No such file or directory

Which is consistent with File Manager, not finding the files either. Corruption may be an issue, but I also wonder if there's a problem with how the home folders were restored?

I've always experienced problems upgrading directly from Software Updater, as it cancels part way through.  Any upgrades have always been done manually.

---

