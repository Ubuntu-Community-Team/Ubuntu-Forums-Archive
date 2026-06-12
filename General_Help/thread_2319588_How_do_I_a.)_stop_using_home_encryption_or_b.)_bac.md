---
title: "How do I a.) stop using /home encryption or b.) back it up to an external USB drive?"
date: 2016-04-05
forum: General Help
---

### Post by pei-ollllo on 2016-04-05
In a recent reinstall of 15.10 I decided (for no particular reason) to turn on encryption for Home folders.  Coincidentally, my LuckyBackup task (RSync) for /home stopped working right thereafter.  I am guessing it is related to trying to backup encrypted files to a FAT, external USB drive.

- I don't need encryption.  Can it be turned off?  In this forum and via Google I found several articles but the latest is from 2012 so I would prefer more recent instructions or assurances it is the same process still.  

- If I reformat the external USB drive to ext4, will rsync between the encrypted /home folder and the USB drive be successful?

- another answer?

Thanks all.

---

### Post by mastablasta on 2016-04-06
as I understand, the files are not encrypted when you are working on them (e.g. are logged in). so the issue might be elsewhere.

If all you are backing up is data files then I would suggest to use NTFS (if you have any windows computers at home), otherwise ext4 would be a better option.

---

### Post by pei-ollllo on 2016-04-10
Thank you for the reply, mastablasta.  Especially, since no one else did.

Upon closer study of the logs, the errors were occurring only for the files in ~/.Private .   Since this appears to be the encrypted mirror of the home folder, backing it up seems redundant any-ways.  I am now excluding it from my backups.  However, I could not see how to exclude a subfolder in Luckybackup so I have gone back to a scripted Rsync command for the home backup.

---

