---
title: "Folder missing after failing to unmount"
date: 2016-11-29
forum: General Help
---

### Post by samuelsson.joel on 2016-11-29
Hi,

I recently updated to Ubuntu 16.04 on one of my partitions (wiped the partition and reinstalled Ubuntu). Before doing so, I made a tar-ball of the entire partition onto another partition. Yesterday, I wanted to get some files from my tar-ball so I extracted the tar-ball partly only to realise my home directory had been encrypted so all my files were in /home/.ecrypt/joel/.Private/ in encrypted form. Following this guide:
[http://www.kaijanmaki.net/2009/10/26/recovering-files-from-ecryptfs-encrypted-home/](http://www.kaijanmaki.net/2009/10/26/recovering-files-from-ecryptfs-encrypted-home/)

I managed to mount the directory and access my files. I copied some of them and today I needed some more of them. However, the directory can no longer be found (neither tar-ball nor my encrypted files, which were all in the same directory). I am certain I didn't do any rm -rf nonsense. Any idea why the folder might be gone and how I can recover it?

Worth mentioning:
- The partition on which I put the backup has an ntfs filesystem and is shared through dual boot with a Windows install. The folder can't be seen from the Windows OS either.
- Running df -h shows 437Gb used on /dev/sda3 even though du -h counts only ~250Gb of files in the folder where that partition is mounted (the difference is reasonable in size for my missing files).
- I did not unmount the ecrypt folder before turning off my computer yesterday.
- I used the Windows install (for other purposes) between turning off Ubuntu yesterday and turning it on today.

---

### Post by yancek on 2016-11-29
I'm not familiar with encryption and potential problems in this case so this is just a guess.  If you re-booted into windows and then into Ubuntu, the ntfs partition might not mount if you left windows hibernated which is the default if you have windows 8 or newer (??)  Of course, you should still have been able to see the partition from windows so...

---

### Post by samuelsson.joel on 2016-11-29
The partition mounts fine. It's the particular folder that is gone. Structure was like this:

backup/
backup/backup.tar
backup/backup/home/.ecryptfs/joel/.Private/
otherFolder1/
otherFolder2/
.....

The entire "backup" folder is gone (including tar file) but other folders are still there. 



I just ran this:
```
joel@joel-laptop:~$ sudo ntfsundelete -m "backup.tar" /dev/sda3 
Inode    Flags  %age     Date    Time       Size  Filename
-----------------------------------------------------------------------
199396   F..!     0%  1970-01-01 01:00         0  backup.tar


Files with potentially recoverable content: 0
```

That doesn't look too promising. I don't understand how the folder can just be gone :/

---

### Post by Keith_Helms on 2016-11-29
No idea, but as part of the hunt try these:
* If there is one, check the Trash folder.
* Do an ls -a to see if something got renamed or moved to a dot file.
* When in the terminal, hit the up-arrow repeatedly to review the commands you previously issued.  Maybe you accidentally did something you didn't mean to or don't recall.

---

