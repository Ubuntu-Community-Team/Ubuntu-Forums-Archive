---
title: "How would I go about stoping automatic backup I started in su"
date: 2008-02-11
forum: General Help
---

### Post by Lord Xeb on 2008-02-11
I started a backup a while ago and currently the file I have the backups saving to is almost a gig. Is there anyway to stop the this backup and how do I delete these files.... because they are owned by root.

---

### Post by x1a4 on 2008-02-13
Open a terminal and get yourself root priviledges:
```
sudo -s
```

What is the name of the app you're using for backup?  Assuming it's **sbackup**: 
Get the backup app's process number: ```
ps -A | grep sbackup
``` will give you something like this: 
```
31: **4391** ps/1     00:05:46 sbackup
```
The value in **bold** is the process number which you will use to kill it like so: 
```
/bin/kill -TERM 4391
```
Confirm it's killed: ```
ps -A | grep sbackup
```
If kill -TERM didn't work use ```
/bin/kill -s 9 4391
```
Use the -s 9 switch ONLY if -TERM does not work. 

Now remove the backup file: ```
rm /path/to/backup/file
```

Or, to recursively delete an entire directory: ```
rm -r /path/to/backup
```

---

