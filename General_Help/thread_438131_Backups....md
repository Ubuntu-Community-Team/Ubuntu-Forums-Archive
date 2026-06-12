---
title: "Backups..."
date: 2007-05-09
forum: General Help
---

### Post by Yaffle on 2007-05-09
Hello,
I have a root partition "/" and a sperate home partition "/home" I have made a hole backup all my data. excluding "/home" and obvious files and folders. Now if my system became un-bootable and I pop the live cd into my computer. What would be the command to restore the backup which is in my "/" folder. without over writing my home partition?

Thanks!  :guitar:

**Edit:** My backup files is called backup.tar.gz.

---

### Post by rdoolen on 2007-05-09
It would be something like, tar -xvpzf /backup.tgz -C /. From live CD, you will have to mount your root partion and replace the / with that mounted parrtiton. Also, you will have to use the correct name and location of your backup file. Remeber, from live CD, you will have to mount those locations and the paths will be different.

---

