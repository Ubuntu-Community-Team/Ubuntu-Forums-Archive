---
title: "tar backup stops after backup file is exactly 25Gb"
date: 2019-08-05
forum: General Help
---

### Post by robertcull1 on 2019-08-05
I am doing backups with a command like this:

```
tar -czvf backup.tar.gz /home/robert
```

Actually I am doing it in a really long script and this is the actual command.

```
/usr/bin/time -o $SCHEDULEFILE -a -f "%E real,%U user,%S sys" tar --exclude='/home/robert/.Xauthority' --exclude='/home/robert/.cache/dconf' -czvf $BACKUPTIME"_backup.tar.gz" /home/robert >> $BACKUPTIME"_stdout.txt" 2> $BACKUPTIME"_stderr.txt"
```

But I don't see how that should make any difference.

It always stops when the tar file gets to be 25.0Gb. I am backing it up into a USB drive. I can't see what I am doing wrong.

Can someone help?

---

### Post by HermanAB on 2019-08-06
Your machine may be running out of RAM causing tar to fail, but some searching showed that older versions of tar do have a maximum file size limit and GNU tar is recommended to avoid that.

You should try rsync with differential backups instead.  It will save oodles of disk space in the long run:
[https://www.nongnu.org/rdiff-backup/](https://www.nongnu.org/rdiff-backup/)
[http://www.mikerubel.org/computers/rsync_snapshots/](http://www.mikerubel.org/computers/rsync_snapshots/)

The original article by Mike Rubel describes how to keep three backups for the price of one, using a combination of hard links and rsync. That idea then spawned the rsnapshot (pull) and rdiff-backup (push) scripts.

FWIIW, I have a little NUC with a 2TB disk that has all my music, movies and backups.

On my MacBook, my backup script is directly based on Mike's and looks like this:
#! /bin/bash
# Rsync to Muzak 192.168.1.250 and keep 3 old hard linked copies.
# Assumes the public key is installed in /home/herman/.ssh
ssh herman@muzak "mv ~/Backups/Herman.3 ~/Backups/Herman.tmp"
ssh herman@muzak "mv ~/Backups/Herman.2 ~/Backups/Herman.3"
ssh herman@muzak "mv ~/Backups/Herman.1 ~/Backups/Herman.2"
ssh herman@muzak "mv ~/Backups/Herman.0 ~/Backups/Herman.1"
ssh herman@muzak "mv ~/Backups/Herman.tmp ~/Backups/Herman.0"
ssh herman@muzak "cp -al ~/Backups/Herman.1/. ~/Backups/Herman.0"
rsync -avze ssh --progress --delete --max-size=20M --exclude "*Trash*" --exclude "*bak" \
--exclude "*old" --exclude "*cache*" --exclude "*Cache*" --exclude "*iso" ~/ herman@muzak:~/Backups/Herman.0/

I simply run this little script whenever I feel like it.

---

### Post by robertcull1 on 2019-08-06
All my research on tar says that gnu tar is exactly the same as tar. I can't find anything on the internet that says tar has a 25Gb limit.

---

### Post by HermanAB on 2019-08-06
Many moons ago, there was a 2 GB limit and then an 8 GB limit.  Now, it may be 25 GB bug, not a deliberate limit.

Anyhoo, using tar with such big files is horrible, since it is a very slow process to retrieve anything from it.

---

### Post by Holger_Gehrke on 2019-08-06
The 't' in tar is for Tape. The program makes assumptions that are true for tape drives (blocks and sequential access, mainly) which are not true for other backup media. So unless you're writing to tape **any** other backup tool is superior to tar.

Holger

---

### Post by TheFu on 2019-08-06
Using tar for anything more than about 500MB is tar-abuse in my book.  It still has some really great uses, just for smaller needs.

duplicity, rdiff-backup, rsnapshot, back-in-time, are some of the most popular tools.  Some require that the target disk have a Linux file system. but one or two of them will work with NTFS.

---

### Post by andrew.46 on 2019-08-06
Interestingly enough 'officially' there should be no file size limit at all. The table at the base of [this page]("https://www.gnu.org/software/tar/manual/html_node/Formats.html") shows some of the historical versions of tar and the limits. Unlimited size for all modern versions of tar...

Might be worth testing a different compression application rather than gzip, perhaps try:

```

tar -c**[COLOR="#FF0000"]a[/COLOR]**vf backup.tar.**[COLOR="#FF0000"]xz[/COLOR]** /home/robert

```

And see if the limitation is coming from compression, not archiving...

---

### Post by Skaperen on 2019-08-07
my vote is for [FONT=courier new]**rsync**[/FONT].  what media are you doing backups to?  tape? memory stick? external hard drive?  how much total space will your backup need?  external hard drive that work on USB-3 are available up to 4 TB (internal SATA up to 14TB)

---

