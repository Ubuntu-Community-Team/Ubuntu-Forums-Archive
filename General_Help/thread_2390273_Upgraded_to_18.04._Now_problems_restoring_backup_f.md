---
title: "Upgraded to 18.04. Now problems restoring backup files"
date: 2018-04-27
forum: General Help
---

### Post by sanreader on 2018-04-27
Before upgrading from 16.04, I made a backup of my data files to external hard drive. Now trying to restore these but the restore option in Backup isn't finding any backup files. I have entered the correct location and correct folder for the backup location.
Any helpful advice welcomed.

---

### Post by rbmorse on 2018-04-27
Is your username the same for the two versions?

---

### Post by sanreader on 2018-04-28
Yes, I'm using the same user name.

---

### Post by sevendogsbsd on 2018-04-28
Never used the back up tool so can't speak to it. Are the backups just a copy of the files or is it some sort of special "archive"? Assuming the back up device is mounted?

I would also check the permissions on your back up drive and compare them to your current user permissions:

```

ls -la <backup drive device goes here>

```

Look at the permissions, specifically what UID is being used (name or a number)

```

ls -la </home/your user here>

```

And compare. You may have to change ownership of your back up drive files for this to work.

EDIT - I am running a back up test to see how this back up tool works, will post back once I see what it does. So, backup complete. The permissions on the backup files, which appear to be some sort of tar gzips....are read-write for my user so that's good. I noticed the back up tool is capable of encrypting backups, did you do this when you made the backup?

---

