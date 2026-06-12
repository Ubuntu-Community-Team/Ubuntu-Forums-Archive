---
title: "rsync'ing folder causes filesystem to fill up."
date: 2014-10-06
forum: General Help
---

### Post by lynwode on 2014-10-06
Ok - its been a long day and my head hurts !

I have rebuilt a server and all was well until I ran a backup script which basically rsyncs a 6GB folder to a staging folder prior to being copied to the backup server.

The problem is that as soon as the rsync kicks off it chews up all the available space on the disk and then bombs with a no space left on device. 
I am confused as how this is possible.

setup:
14.04 virtual machine with 100GB volume of which 82GB is free.

command:
rsync -avHK --delete --backup --backup-dir=$BACKUPDIR /opt/app/ $DESTLOCAL/app

Any ideas?

Cheers,
Tim

---

### Post by nerdtron on 2014-10-06
Have you tried other options on the rsync command? Why use H and K? Are you using hard links? You could have loops in there.

Try the following rsync to see the files and progress of transfer, notice if there are any duplicates when you copy.
```
rsync -avrh --progress 
```

---

### Post by Habitual on 2014-10-06
What's the value of "$DESTLOCAL" ?

---

### Post by lynwode on 2014-10-24
Thanks for the reply and apologies for the delay in responding.
I tried your suggestion but the same thing happens just fills up the filesystem.

Its a zimbra install I am backing up following the procedure here [http://wiki.zimbra.com/wiki/Open_Source_Edition_Backup_Procedure#A_Simple_Shell_Script_Method](http://wiki.zimbra.com/wiki/Open_Source_Edition_Backup_Procedure#A_Simple_Shell_Script_Method)

Stumped as this worked on an old instance utilising the same script! 

It seemd to grow massively when it hits data/ldap/mdb/db/data.mdb..... ahhh an 80GB file.... googling finds that zimbra has changed something.... [http://blog.datacenterfromhell.net/2013/03/the-zimbra-8-ldap-database-mystery.html](http://blog.datacenterfromhell.net/2013/03/the-zimbra-8-ldap-database-mystery.html)

Right back to the drawing board...

Cheers,
Tim.

---

### Post by lynwode on 2014-10-28
Solved - using the -S for sparse files :)

---

