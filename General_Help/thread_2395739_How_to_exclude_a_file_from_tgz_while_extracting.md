---
title: "How to exclude a file from tgz while extracting"
date: 2018-07-06
forum: General Help
---

### Post by scientist21 on 2018-07-06
I have backed up my entire hard disk through this command(1).
I then copied the backup.tgz into root directory of ubuntu and tried to extract it but it took me some time to realize that my whole external hard disk is also backed up which make Backup.tgz file about 80gb. I donot want to extract my /media folder. Can I just delete it without making another backup as I do not have enough time? OR Can I just exclude the directory /media while extracting? I used command (2), (3), (4) to extract files without extracting /media folder but it did not work. Kindly tell me anyway to extract my backup without /media or help me delete /media folder.

(1) = tar cvpzf backup.tgz --exclude=/proc --exclude=/lost+found --exclude=/backup.tgz --exclude=/mnt --exclude=/sys /

(2) = tar xpvfz backup.tgz -C / --exclude "/media"

(3) = tar xpvfz backup.tgz -C / --exclude=/media

(4) = tar xpvfz backup.tgz -C / --exclude='/media'

---

### Post by Holger_Gehrke on 2018-07-06
tar does have an option '--delete' to remove archive-members, but it only works on uncompressed archives. The '--exclude=' option only works when adding files. To exclude files from extraction, you'll have to get the list of archive members and manipulate it.
```

tar -xf Backupt.tgz $(tar -tf Backup.tgz | sed -E '\#/$#d;\#^^/media/#d')

```
The sequence '$( ... )' is a command line substitution. The output of the command(s) inside the parentheses is put into the command line in place of the command. That command gets the list of the contents of the archive and filters it through sed, removing directories (entries ending in '/') and files in '/media'. That list is then passed to tar to extract.

It might be simpler to use a frontend for extracting like file-roller or the 'Midnight Commander' (mc).

Holger

---

### Post by Frogs Hair on 2018-07-06
Closed per OP request .

---

