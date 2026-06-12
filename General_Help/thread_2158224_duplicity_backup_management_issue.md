---
title: "duplicity backup management issue"
date: 2013-06-28
forum: General Help
---

### Post by redrumrogue on 2013-06-28
Hi all,

This is my very first post!  (irrelevant information, i know..).

I've been happily using Ubuntu 12.04LTS for quite a while now, and using Deja-Dup for backing up /home/justin to a USB drive.  Over time Deja-Dup has created 1 or two additional full backup sets, and now my backup drive is getting full.

First question:  what happens when the drive gets full?  Will old backups be removed automatically to make way for the latest?

Secondly ... I'm aware that Deja-Dup is just a GUI for Duplicity.  So, I've tried running the command [COLOR=#a52a2a]**duplicity remove-all-but-n-full 1 file:///media/backup**[/COLOR].  This seems to be very quickly filling up my /(root) partition, which is only 10Gb in size (/home is 2Tb total) ... and of course the operation fails.  Thankfully the data written to /root seems to be deleted automatically when the command fails.  Why is this happening?  Can I change Duplicity config in some way to prevent his?  I think this is going to cause issues for me when the backup drive gets full and the system will not be able to remove old backups automatically to make way for the latest and greatest.

Any help would be much appreciated!

---

### Post by TheFu on 2013-06-28
I don't use either of those tools, sorry.  Most of the information you seek is contained in the "man page" for each command. For any lurkers, open a terminal, type:
$ **man duplicity**

It seems you may have read that information already, but might have missed some critical parts, like the **cleanup** section. Seems running *cleanup  --force *could be necessary after failures.

I've found that there are often "best practice" guides written for specific software. Perhaps Deja-dup and/or duplicity have a writeup somewhere? Google didn't find any great, but [https://lists.gnu.org/archive/html/duplicity-talk/2008-03/msg00088.html](https://lists.gnu.org/archive/html/duplicity-talk/2008-03/msg00088.html) might be helpful.  I found this page [http://www.rsync.net/resources/howto/duplicity.html](http://www.rsync.net/resources/howto/duplicity.html) useful in explaining full and incremental backups for this tool.

To understand failures, usually turning up the logging or verbosity of output is needed.  I like to use "tee" to mirror output from commands to log files, if the output errors and warnings are too long to read in the console.  Deja-dup must log things somewhere. What do those lof files show as the errors?

Duplicity seems like an awesome backup tool.  I'll need to consider switching from rdiff-backup (my favorite the last 6 yrs).

Sorry I don't know anything about the programs you are using. Hopefully, someone else will respond with more useful information.

BTW, good choice running 12.04!  I love it!

---

### Post by redrumrogue on 2013-06-28
Thanks for the reply!  I wasn't sure if I'd get one.  I have read through parts of the man pages but it seems a little light on information.  Here is the output from my terminal window ...

justin@IXTREME:~$ duplicity remove-all-but-n-full 1 --force file:///media/Seagate/IXTREME/HOME_backup
Import of duplicity.backends.sshbackend Failed: No module named paramiko
Synchronising remote metadata to local cache...
GnuPG passphrase: 
Copying duplicity-full-signatures.20130609T110852Z.sigtar.gpg to local cache.
[Errno 28] No space left on device
justin@IXTREME:~$

So ... it's "Copying duplicity-full-signatures.20130609T110852Z.sigtar.gpg to local cache", which is obviously on my /root partition.  I have to admit, I don't know where the "local cache" is on the /root partition.  I'd like to find out if there is a way of changing the location to which duplicity copies the data.  I will take you advice and search for a best practice guide.  In the meantime if anybody has some ideas for me - let me know.

Thanks.

---

### Post by redrumrogue on 2013-06-29
looks like data is being written to /tmp ...

---

