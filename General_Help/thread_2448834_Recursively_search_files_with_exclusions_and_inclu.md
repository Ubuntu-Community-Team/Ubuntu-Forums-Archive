---
title: "Recursively search files with exclusions and inclusions"
date: 2020-08-14
forum: General Help
---

### Post by Helveticus on 2020-08-14
Hello everybody

I would like to use find to recursively search files and print them to a file. I imagine a command like this:

```
    find /local/data/ --exclude 'database/session*' --include='database/session_*.db' > temp.txt
```

This command does not work. How can I use exclusion and inclusion that work? database/session* and database/session_*.db appear as part of a path, i.e. /local/data/.../database/session..../... and /local/data/database/session_*.db.

---

### Post by TheFu on 2020-08-14
**find** is one of those commands where seeing a few examples is crazy helpful.  Also, don't be afraid to pipeline.
```
 find /local/data/ -type f -name session_\*db -print | egrep -v 'some-regex-to-exclude'
```
If you show examples of the files to be excluded and included, perhaps a regex can be crafted.  Don't forget that other file properties can be used like the create time, owner, and permissions.

---

### Post by Helveticus on 2020-08-14
Thank you so much. Here is the directory structure:

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
```

I would like to find all files except for the files in /database/session_*. Is there a regex for that?

---

### Post by TheFu on 2020-08-14
```
find /local/data/ -type f -name 'session[0-9]+*db' -print
```
Appears to be what you want, but not what is being described.

---

