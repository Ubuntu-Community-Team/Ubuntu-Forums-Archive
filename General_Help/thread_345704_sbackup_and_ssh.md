---
title: "sbackup and ssh"
date: 2007-01-24
forum: General Help
---

### Post by chipyoung on 2007-01-24
I am running ubuntu version 6.06.  I am trying to do a backup of my PC using sbackup.  I am trying to use the ssh option to backup to my web server which is also ubuntu.  I cannot get it to backup to my other server.  I have no problem ssh'ing into that server.  In fact I use scp all the time to trasfer files from my local to my server.  I am using the custom backup settings and specifying my remote server with the proper userid and password.  When I run the sbackup with these settings it backs up to my local hard drive even though I have specfied the ssh option.  My version of sbackup is .9-1.

I get the following error message when I run from the command prompt (sudo simple-backup-config)

Traceback (most recent call last):
  File "/usr/sbin/simple-backup-config", line 609, in on_dest_remotetest_clicked
    if tinfo and tinfo.type == 2 and (tinfo.permissions / (8*8) )-(tinfo.permiss ions/(8*8*8)*8)  == 7:
ValueError: type field has no valid value


Any help would be greatly appreciated.

Thanks in advance,
Chip

---

