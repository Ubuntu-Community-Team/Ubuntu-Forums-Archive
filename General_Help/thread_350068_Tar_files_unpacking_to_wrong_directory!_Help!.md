---
title: "Tar files unpacking to wrong directory! Help!"
date: 2007-01-31
forum: General Help
---

### Post by Gen2ly on 2007-01-31
I recently used [Heliodes excellent Restore and Backup Howto]("http://ubuntuforums.org/showthread.php?t=35087&highlight=howto+backup") and it looks like it works decent, but I can't get the files to unpack in the right directory.  The command to backup the systems is:
> tar cvpzf backup.tgz ... /
 "..." represents some information that I left out so not to bore you all.  This original command saves the tar file at root.  I in all my grace and bravado said I don't want it there so my command
> tar cvpzf backup.tgz ... /home/user/backups
Well, now i have troubles.  When I tried my restore attempt:
>  tar xvpfz backup.tgz -C /
the whole system was :confused: in /home/user/backups and not at root.
Is there a way to have tar not use /home/user/backups ???

thx

---

### Post by daemonoid on 2007-01-31
The problem is that the tar file itself has the path saved. I'm not sure how to do it from cmd line but most archive gui progs can do it (try file roller).

Otherwise, why not simply do:

```
mv /home/usr/backups / -r
```

On the untarred file?

---

### Post by WW on 2007-01-31
As far as I can tell, your second tar command does not create an archive of your root directory.  Instead, it creates an archive of the directory /home/user/backups, and I don't think that is what you intended.  If I understand what you were trying to do, the command should have been
```
tar cvpzf /home/user/backups/backup.tgz ... /
```
That will create an archive of your root directory, and store the result in /home/user/backups/backup.tgz.

To see the files in a tar archive without extracting them, you can use the "t" option.  For example,
```
tar tzf backups.tgz | less
```
will list the names of the files in backups.tgz (and pass them to the "less" command for convenient viewing).  Use this to see if the archive contains what you think it should contain.

---

### Post by gwpritch on 2007-01-31
I'm not familiar with the app you're using but it seems to me if you are trying to write the backup to the root directory you are going to need root privilages

```
sudo tar xvpfz backup.tgz -C / 
```

---

### Post by Gen2ly on 2007-01-31
yes true, gwpritch, I do sudo ;) and, yes WW,  I forgot the mention that it was at root I tarred at.

I did as you recommended daemonoid and it seems to work, though things feel a tad bit sluggish. 
> mv /home/usr/backups / -r
I thought there would be a tar command I could use, as I don't want have my backups stored at /.

---

