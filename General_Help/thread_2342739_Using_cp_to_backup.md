---
title: "Using cp to backup"
date: 2016-11-09
forum: General Help
---

### Post by sccjono on 2016-11-09
Hello all,

I'm really sorry but I'm sure I'm going to infuriate the more experience CLI users here but...

I already use rdiff-backup to periodically backup my home directory to an external drive and it works great. However, I would also like to replicate some of my directories, such as ~/Pictures into my Dropbox folder e.g. ~/Dropbox/Photos. I realise I could use rdiff-backup again but I'd like to avoid the 'rdiff-backup-data' directory etc and so I hoped to be able to use cp. Unfortunately the more I read, the more I'm confusing myself.

Would executing...
```
cp -vRu ~/Pictures/* ~/Dropbox/Photos
```
...Periodically keep my Dropbox matching what's in my Pictures folder?


Thanks,
jono

---

### Post by Bucky Ball on 2016-11-09
*Thread moved to **General Help**.*

... as *New to Ubuntu* is for users who are. :) You could use Luckybackup for this. Easy interface and works fine for incremental backups. Only backs up what's not in the target directory or has been changed in the source directory. Sounds dinky but is powerful. Its in the official repos so you can install from there.

Hope that helps.

---

### Post by TheFu on 2016-11-09
For your specific use, I'd use **rsync**. No need to copy things that haven't changed since the last copy.

```
$ rsync -avz ~/Pictures/* ~/Dropbox/Photos/
```
be careful about trailing slashes - you want this one.

The only downside is that rsync does recursive and you might not want that?

Having a mirror on dropbox or OwnCloud or seafile or any of the other cloud-storage-like options isn't really the purpose for rdiff-backup or other versioned backup tools.  Of course, you still need to have versioned backups for ~/Pictures/ outside dropbox.

---

### Post by Dennis N on 2016-11-09
> **sccjono said:**
> Would executing...
```
cp -vRu ~/Pictures/* ~/Dropbox/Photos
```
...Periodically keep my Dropbox matching what's in my Pictures folder?


Yes, it will copy a file only if the file is not in the destination, or if a source file is newer than the same file on the destination. What it will not do is delete a file in the destination folder when the same file it not in the source folder.

---

### Post by CantankRus on 2016-11-09
You could put your ~/Pictures folder in dropbox, then create  ~/Pictures as a link to the dropbox folder.
You said you already backup $HOME.

---

### Post by oldrocker99 on 2016-11-10
My personal favorite is grsync, which is simply a frontend for rsync, and is, shall we say, easier to use.

---

### Post by sccjono on 2016-11-16
Sorry for the delay in replying but I wanted to say thank you all for the posts. I have settled on the rsync solution and its working great. Thanks again.

jono

---

### Post by Bucky Ball on 2016-11-16
Thanks for getting back to it. Could you please mark the thread as 'solved' to help others. Thread Tools at top right or see the link in my signature for how. Thanks.

---

### Post by SeijiSensei on 2016-11-16
> **Dennis N said:**
> Yes, it will copy a file only if the file is not in the destination, or if a source file is newer than the same file on the destination. What it will not do is delete a file in the destination folder when the same file it not in the source folder.

Rsync will delete files in the destination if you add the --delete option to the command line.  You can also tell it whether to do the deletions before, during, or after the transfer.  Rsync has an enormous array of options; see "[man rsync]("https://linux.die.net/man/1/rsync")."

---

