---
title: "Chgrp incompatible with NTFS/smbfs?"
date: 2006-10-16
forum: General Help
---

### Post by W. Irving on 2006-10-16
Quick question.

I've set up my Ubuntu laptop to make backups to my desktop (running Win XP) using rsync via samba. Additionally, rsync is running in archive mode so that permissions, group, owner, times and other metadata is preserved. But for every file that rsync copies, it says this:

> rsync: chgrp "<DESTINATION FILE>" failed: Operation not permitted (1)


Is this a limitation with samba or NTFS?


Yes - I'm fully aware that the idea to back up your Linux machine to a Windows one is a little unorthodox and defies all logic, but that's the way it has to be for me until SHIII runs on Ubuntu :)

---

### Post by bettlebrox on 2006-10-16
The group probably doesn't exist on the NTFS system, plus it's a differnt OS so it's filesystem doesn't quite correspond to how Linux (and Unixes) work. 

U could try using tar in incremental mode instead:

[http://chxo.com/be2/tar_backup_to_ntfs.html]("http://chxo.com/be2/tar_backup_to_ntfs.html")

---

