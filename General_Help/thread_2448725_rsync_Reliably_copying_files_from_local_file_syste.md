---
title: "rsync: Reliably copying files from local file system to NAS"
date: 2020-08-12
forum: General Help
---

### Post by Helveticus on 2020-08-12
I run a virtual machine with Red Hat. On the virtual machine a node.js server is running and the data uploaded to the server is stored locally on the machine at /local/data.

From time to time (e.g. once a week) I would like to move the data to a NAS. The NAS is mounted on the virtual machine. That means I would like to move the data from /local/data to /import/myNas/data

/local/data contains folders, files and sqlite database files. The structure is as follows:

```
/local/data/folder1
         exception1.exception
         exception2.exception
         info.txt
         otherFile.txt
         /database
             session1.db
             session2.db
             ....
             session1000.db
    
/local/data/folder2
         exception1.exception
         info.txt
         otherFile.txt
         /database
             /session_198
                     session_198.00000034.db.tmp
                     session_198.00000035.db.tmp
                     ...
                     upload_fff344dbf979363020d1b874a8ee7bef.db
             session1.db
             session2.db
             ....
             session987.db
```

I would like to copy all data to /import/myNas/data except for the folders in /database. So for example, /local/data/folder2/database/session_198 and all of its files should not be copied.

How can I copy all these data to the NAS and when copying finished delete it from local storage? Very important is that the data is only deleted when the data is successfully copied (or moved), that means no corrupted or lost data. I don't know which the most reliable solution is (Python script, shell script, etc.)

---

### Post by HermanAB on 2020-08-13
Something like this:
rsync  --exclude="*database*" --delete --max-delete=50 /local/data/ /import/myNas/data/

The max-delete is intended to prevent a total catastrophe.

Please see this also:
[https://www.aeronetworks.ca/2019/08/differential-backups-made-simple.html](https://www.aeronetworks.ca/2019/08/differential-backups-made-simple.html)

---

### Post by The Cog on 2020-08-13
The --delete in rsync deletes files on the destination that don't have matching files in the source. This may not be what you are looking for.
I think that to delete the source after a successful rsync would need a separate command. Something like this **untested** perhaps:
```
#!/bin/bash
# tell the script to stop if any command fails - won't remove source files if rsync fails
set -e 
# copy the files
rsync --exclude="*database*" --delete --max-delete=50 /local/data/ /import/myNas/data/
# remove the source files
rm -rf /local/data
```

---

### Post by HermanAB on 2020-08-13
Good one: 'set -e'
That can save a whole lot of error checking in a script.

---

### Post by Helveticus on 2020-08-13
[COLOR=#1A1A1B][COLOR=#1A1A1B]Thank you very much to all of you. [/COLOR]

Does the set command get shipped with rsync or do I have to install some package?

database  should not be excluded but all folders inside [/COLOR][COLOR=#1A1A1B][COLOR=#1A1A1B]database[/COLOR]. How can I do  this? The folders inside database start with "session", so for example database/session_234 or database/session_1234. But inside database there are also files starting with "session", such as database/session_234.db or database/session_1234.db. These files should not be excluded.

Is it perhaps better to use --delete-source-files? 
[/COLOR][COLOR=#1A1A1B]  [/COLOR]

---

### Post by SeijiSensei on 2020-08-13
I much prefer to put includes and excludes in separate plain-text files and use 
```
rsync -av --files-from=/usr/local/etc/rsync-includes --exclude-from=/usr/local/etc/rsync-excludes [etc.]
```
You could then try populating rsync-includes with
```

[other filespecs you want to back up]
database/session_*.db

```
and rsync-excludes with
```

[other filespecs you want to exclude]
database/session*

```
You'll probably have to play around with these to get exactly the results you want.

I don't know what kind of databases these are.  I use PostgreSQL and MySQL.  For both I run the "dump" command before running rsync, e.g., for PostgreSQL,
```
/usr/bin/pg_dumpall -U username > mypgdump
```
That produces a plain-text file that can be used to reconstruct the databases if they go south. I use rsync to copy these files, not the databases themselves. I don't know if the database software you're using has an equivalent command.

---

### Post by Helveticus on 2020-08-13
Thank you SeijiSensei. This helped me a lot. My script now looks as follows:

```
#!/bin/bash
# chmod +x copy.sh
# Execute script in root
# tell the script to stop if any command fails - won't remove source files if rsync fails
set -e
# copy the files
rsync --info=progress2 -r --include='database/session_*.db' --exclude  'database/session*' --remove-source-files /local/data/  /import/myNas/data
```

This works perfectly. But I have just two questions:

I found that --remove-source-files also removes not yet copied files when rsync stops. That means  when I terminate rsync in-between copying files or when rsync stops due  to a failure. How can I prevent this so that only files are delete in source which are successfully copied?

Second, is it likely to  get corrupted files from rsync? If a file is successfully copied but  corrupted and gets removed by --remove-source-files, that would be very  bad. Is there a way to guarantee that only non-corrupted files are  deleted in the source directory?

---

### Post by SeijiSensei on 2020-08-13
I've never used --remove-source-files.  If I want to delete files on the source, I use a script on that machine. Most of the time I just leave the source files alone.

As for file checking, see [https://www.oreilly.com/library/view/linux-security-cookbook/0596003919/ch01s16.html](https://www.oreilly.com/library/view/linux-security-cookbook/0596003919/ch01s16.html)

Basically it suggests running rsync twice, once to transfer the files, and again with the "-n" or "--dry-run" switch after the initial transfer is complete.

---

### Post by Helveticus on 2020-08-13
Thanks for the link. That makes sense, I will give it a try.

My script now looks as follows:

```
#!/bin/bash
# chmod +x copy.sh
# Execute script in root
# tell the script to stop if any command fails - won't remove source files if rsync fails
set -e
# copy the files
rsync --info=progress2 -r --include='database/session_*.db' --exclude 'database/session*' /local/data/ /import/myNas/data
rsync --info=progress2 -r --include='database/session_*.db' --exclude 'database/session*' --checksum --remove-source-files /local/data/ /import/myNas/data
```

The problem now is that while rsync is running new files are written to /local/data. I would like that rsync takes a snapshots of the list of files when it runs the first time and then only copies these files. In the second run rsync should then also only run on these files from the snapshot. Is this possible?

---

### Post by SeijiSensei on 2020-08-13
What if you reverse the comparison in the second step comparing the files on the NAS to their origins?

---

### Post by Helveticus on 2020-08-13
That could be an option. Another option could be to use find to put a list of all the files in a temporary file and then using --include-from=/tmp/filenames to copy just those files.

How can I create such a temporary file with find so that database/session_*.db are included but database/session* are excluded?

---

### Post by HermanAB on 2020-08-14
You can run rsync multiple times and first copy the important ones:
rsync -a "/whatever/session_*.db" /wherever/

Followed by the rest with a blanket exclude:
rsync -a --exclude="*session*" /whatever/ /wherever/

---

