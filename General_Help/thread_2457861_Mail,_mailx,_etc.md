---
title: "Mail, mailx, etc"
date: 2021-02-11
forum: General Help
---

### Post by hornetster on 2021-02-11
Anyone clued up on mail, mailx or whatever?
Dual boot machine, generally boot to opensuse leap 15.2, but now also playing with Ubuntu 20.04.
In opensuse, have a number of scripts to do various backups, and report, and using mailx to do the mailing. Trying to get the same scripts to work in Ubuntu, and would appear that it is a 'different' mailx - many of the arguments used in the opensuse version, don't exist in the ubuntu one. Particularly the saving of config using -A - which saves your remote server info.) Frustrating, to say the least!
mailx in Ubuntu apparently belongs to: "s-nail, 14.9.15-1" whereas 
mailx in opensuse belongs to : "mailx, 12.5-lp152.3.7"

Thanks.

---

### Post by norobro on 2021-02-11
I don't know anything about s-nail, I use gnu mailutils, but according to the man page it has the "-A" option.> -A name, --account=..
               Executes an account command for the given user email account
               name after program startup is complete (all resource files are
               loaded, any -S setting is being established, but -X commands
               have not been evaluated yet)... 
Is mailx pointed at s-nail?```
$ update-alternatives --config mailx
There are 2 choices for the alternative mailx (providing /usr/bin/mailx).


  Selection    Path                     Priority   Status
------------------------------------------------------------
* 0            /usr/bin/mail.mailutils   30        auto mode
  1            /usr/bin/mail.mailutils   30        manual mode
  2            /usr/bin/s-nail           30        manual mode
```

---

