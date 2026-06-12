---
title: "Rsync: why different number of files in destination vs. source?"
date: 2021-03-28
forum: General Help
---

### Post by Brent_Santin on 2021-03-28
Hi, I used rsync to backup my home directory to an external USB hard drive. Both drives are ext4 filesystem.

The command I used was:
** rsync -a --progress /home/brent /media/brent/Elements/Lubuntu20^04_backups/Home_rsync_bkp**

When I examined both the source and destination folders to compare them (using PCManFM's "properties" fuction) there was a slight difference in the number of files and and space occupied by the source and copy:

SOURCE:
Contains: 69,533 files

DESTINATION: 
Contains: 69,525 files

I've attached screenshots below. Click to enlarge them.
Just wondering why this is the case? Thanks.

[ATTACH=CONFIG]288194[/ATTACH]     [ATTACH=CONFIG]288195[/ATTACH]

NOTE: While rsync was copying the files, I did open and edit a document in a text editor (FeatherPad), but I didn't save the file. I'm wondering if that could have caused some log files or something to have been created by Featherpad that would have been written to the source and explain the discrepancy.

---

### Post by TheFu on 2021-03-28
rsync doesn't delete files in the target, unless that is specifically requested.

GUI programs, and almost all editors, commonly create temporary files in the same directory as the file being edited.

To backup files for a real backup, it is almost always best to use a backup tool that includes versioning.
[LIST]
[*][https://popey.com/blog/2020/12/straightforward-linux-backups-with-rsnapshot/](https://popey.com/blog/2020/12/straightforward-linux-backups-with-rsnapshot/)
[*][https://www.cyberciti.biz/faq/linux-unix-apple-osx-bsd-rsync-copy-hard-links/](https://www.cyberciti.biz/faq/linux-unix-apple-osx-bsd-rsync-copy-hard-links/)
[/LIST]
rsnapshot is in the ubuntu repos and has been well-tested for 20+ yrs. It is based on rsync.
The target storage needs to support normal Unix features, so don't use NTFS or anything with "FAT" in the name for the file system.

If you want to ensure something like what you are doing cannot happen, that's where LVM or ZFS with snapshots comes in. A quiesced file system ensures no corruption for files which may have been "open()" during the copy time.  LVM snapshots + something like rdiff-backup are really excellent for efficient, fast, versioned, backups, but you can use LVM snapshots + rsync to get 1 clean copy too, if you prefer.  Versioned backups aren't a 1-for-1 storage thing.  Here's what rdiff-backup does with 90 days of daily, versioned, backups:
[https://ubuntuforums.org/showthread.php?t=2436798&p=13932882#post13932882](https://ubuntuforums.org/showthread.php?t=2436798&p=13932882#post13932882)
Basically, 9G of files in the backup used 10.1G for 90days of backups. About 10% more storage for all those versions? Seems like a no-brainer.

---

### Post by Doug S on 2021-03-28
Try having another look with rsync, to see if it can provide any insight.

For example, and for this reply, I did a backup of my local directory to another disk, albeit on the same computer. For number of files, I get:

```
doug@s19:/media/sdb/backup/s19$ find . -type f | wc -l
313253
doug@s19:/media/sdb/backup/s19$ find /home/doug -type f | wc -l
313255
```Oh, the number of files differs by 2. I wonder why? Well, maybe rsync can tell me (note the use of --dry-run, as I don't actually want to do it again):

```
doug@s19:/media/sdb/backup/s19$ rsync --delete --archive --verbose --dry-run /home/doug ./
sending incremental file list
doug/.bash_history
doug/vm/desk-ff.img
doug/vm/serv-xx.img

sent 9,847,891 bytes  received 71,198 bytes  3,967,635.60 bytes/sec
total size is 203,185,919,579  speedup is 20,484.33 (DRY RUN)
``` Well, of course my bash_history changed, as I had typed new commands. And oh ya, those two virtual machine image files are root owned:


```
doug@s19:/media/sdb/backup/s19$ ls -l /home/doug/vm
total 25690068
-rw------- 1 root root 53695545344 Nov 21 13:06 desk-ff.img
-rw------- 1 root root 53695545344 Mar  5 14:23 serv-xx.img
```

EDIT: I guess I was off doing this reply when TheFu replied. And yes, I had it backwards that your destination had more files than the source. Notice that I used the --delete option.

---

### Post by Brent_Santin on 2021-03-28
Okay, sounds like the text editor use probably caused the change in file numbers.

> rsync doesn't delete files in the target, unless that is specifically requested.

This was from a source to a totally blank drive, so I don't think the --delete parameter would have helped in this case.

---

### Post by Doug S on 2021-03-28
> **Brent_Santin said:**
> Okay, sounds like the text editor use probably caused the change in file numbers.So, verify that assumption. Example, where I deleted 4 files and did it again:

```
doug@s19:/media/sdb/backup/s19$ rsync --delete --archive --verbose --dry-run /home/doug ./
sending incremental file list
[COLOR="#FF0000"]deleting doug/turbostatfx2[/COLOR]
[COLOR="#FF0000"]deleting doug/turbostatfx1[/COLOR]
[COLOR="#FF0000"]deleting doug/turbostatdq[/COLOR]
[COLOR="#FF0000"]deleting doug/turbostatd[/COLOR]
doug/
doug/.bash_history
doug/vm/desk-ff.img
doug/vm/serv-xx.img

sent 9,847,782 bytes  received 71,286 bytes  3,967,627.20 bytes/sec
total size is 203,185,362,788  speedup is 20,484.32 (DRY RUN)
```

---

### Post by HermanAB on 2021-03-28
You could use *ls* to make a list of each directory, then compare the two lists with *diff*.  Then you will know exactly what is different.

---

### Post by TheFu on 2021-03-28
> **HermanAB said:**
> You could use *ls* to make a list of each directory, then compare the two lists with *diff*.  Then you will know exactly what is different.

Or use **diff**/**sdiff** to compare the directory "files" - or **meld** or **dircmp**.  This takes advantage of the "everything is a file in Unix" fundamental view.  It turns out that directories are just files too. ;)
[https://unix.stackexchange.com/questions/231530/comparing-directories-using-diff](https://unix.stackexchange.com/questions/231530/comparing-directories-using-diff)

---

