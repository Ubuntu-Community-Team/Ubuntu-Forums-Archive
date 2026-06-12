---
title: "Making backups w/ Unison"
date: 2007-06-15
forum: General Help
---

### Post by drmbogo on 2007-06-15
SOLVED!!!


Hi all!
I'm having a bit of a problem using Unison to create backups. I can synchronize between two folders just fine, and the backup preference seems to work, IF I use the default backup location i.e.: ~/.unison/backup.
The problem occurs when I try to use the backupdir preference to change the directory where backups are stored.
Here's my profile for Unison:
```

root = /home/redrock/RedFiles
root = /media/sdb1/redfilebak



backupdir = Path {baktest}
backup = Name {production.xls}
maxbackups = 4

```

I've tried this with and without the curly brackets  (adding an ignore rule via the GUI gave me the idea to use them, as well as the format of the line)
Without the backupdir line, the backups work, and are placed in the ~/.unison/backup directory.
With that line, no back up takes place, though synchronization still proceeds normally.

If I try to add an absolute path to the backupdir pref, I get this error:
```

Fatal error

Cannot find canonical name of Path media/sdb1/redfilebak/baktest: unable to cd either to it

(Path media/sdb1/redfilebak/baktest: No such file or directory)
or to its parent Path media/sdb1/redfilebak
(Path media/sdb1/redfilebak: No such file or directory)

```

Anyone have any ideas? I have several other files that I'd like to keep multiple copies of, but I'd rather not have to keep them in ~/.unison/backup, if possible.

Thanks in advance!
dB

---

### Post by drmbogo on 2007-06-15
Ok, in the interest of full disclosure, here's how I goofed:

Apparently you don't need the 'Path' identifier in the backupdir pref.
I changed this line:
```

backupdir = Path {baktest}

```
to this:
```

backupdir = /media/sdb1/baktest

```
and... voila, success!

Incidentally, for the newb, the manual isn't very clear on this point. In fact, in the section on Path specification, it talks of three possible forms; Regexp, Path, and Name. The Path form should look like Path path. Now, I recall reading somewhere in the manual that paths were relative (relative to the root of the replica), and I was attempting to use an absolute path.
I discovered this when looking thru my home folder; I found several folders all beginning with 'Path ...'. i.e. 'Path baktest', and 'Path {baktest}' and, not surprisingly, there were my backup files!
So, problem solved, and I'm the wiser for it ;) Hope this can help someone else.
Cheers
Edit: the fatal error happened because, of course, unison went looking for /home/dave/media/sdb1/redfilebak/baktest, rather than /media/sdb1/redfilebak/baktest, which, naturally it didn't find!

---

### Post by Cato2 on 2007-11-19
Unison is very nice for 2-way syncing, but it really isn't a backup tool - I tried using it for backups but found it quite unwieldy.  Using rsync or something based on it (e.g. duplicity or BackupPC) is probably a better approach, and can provide a key feature of backup tools: the ability to easily go back to a previous version of a set of files, including deleted files.  While Unison can just about do this, it's quite hard to make it work for backups.

---

