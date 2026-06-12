---
title: "Duplicity tries to restore rather than back up"
date: 2013-11-29
forum: General Help
---

### Post by Sageth on 2013-11-29
I'm using the duplicity command line (not deja-dup) and am looking to make a backup of a remote server (my VPS) and copy it locally.  For some reason, no matter what options I put, duplicity thinks that I want to restore rather than back up.  I think it's because I have the URL first (scp://root...) which is the syntax for restore, but I can't seem to force it to do a backup.  I've even tried "duplicity full..." and it says that you can't use full on a restore.

I've put a very excerpted debug log that I believe illustrates what I'm saying.  Any thoughts as to if I can accomplish this in the way that I'm thinking?  The man page for duplicity doesn't explicitly say that I can't (from what I can tell) and if I don't have to install duplicity on my VPS, that would be ideal.  Any thoughts?



```
sageth@sageth-desktop:~$ /usr/bin/duplicity --verbosity 9 --ssh-options="-oIdentityFile=~/.ssh/vps" --no-encryption scp://root@vps/etc /backup
**Main action: restore**
================================================================================
duplicity 0.6.21 (January 23, 2013)
Args: /usr/bin/duplicity --verbosity 9 --ssh-options=-oIdentityFile=~/.ssh/vps --no-encryption scp://root@vps/etc /backup
================================================================================
CollectionsError: No backup chains found

```

---

