---
title: "tar: Error exit delayed from previous errors"
date: 2007-09-22
forum: General Help
---

### Post by zkab on 2007-09-22
I followed the guidelines in Howto: Backup and restore your system! ([http://ubuntuforums.org/showthread.php?t=35087](http://ubuntuforums.org/showthread.php?t=35087)) and here are my commands:

Backup:

cd /
sudo tar cvpzf backup.tgz --exclude=/proc --exclude=/lost+found --exclude=/backup.tgz --exclude=/backup.log --exclude=/backup.error --exclude=/backup.cron --exclude=/backup.cp --exclude=/mnt --exclude=/media --exclude=/sys --exclude=/home/zkab/.Trash > backup.log 2>backup.error / 

Restore:

cd /
sudo tar xvpfz backup.tgz -C /

but at the end of the restore I get following error msg:

    tar: Error exit delayed from previous errors

What is wrong ... can I trust the backup :confused:

Another question ... should I add exclude=/tmp in the backup command ?

---

### Post by harmlessdrudge on 2008-04-23
+1

I found this when searching for a solution the same problem.

---

### Post by chrismyers on 2008-06-22
I encountered this problem. This is how I fixed it.

This was my original backup command:

tar cvpzf ~/backup.tgz ~ --exclude=backup.tgz --exclude=Trash --exclude=Cache

It errored with the with the same as you.

I added this to the end of my tar command:

--exclude=backup.log > ~/backup.log

I ran it again & checked the newly created backup.log

I found that it had a permission denied on a folder, so I excluded it.

It then worked fine. Hope this helps.

---

### Post by lolwhites on 2008-07-21
I'm getting the same error message when I create the backup in the first place. I tries excluding the folders where the problems seemed to be occurring, but when I tried backing up just the home folder, the same thing happened, in spite of the fact that it had happily gone through the home folder on previous occasions.

It seems that the message appears once it's finished creating the tar file. Will it still be usable?

---

