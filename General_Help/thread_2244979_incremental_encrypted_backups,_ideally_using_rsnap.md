---
title: "incremental encrypted backups, ideally using rsnapshot?"
date: 2014-09-20
forum: General Help
---

### Post by Martin_Mucha on 2014-09-20
Hi,

in last two month I nearly destroyed all mine data twice by stupid mistake, which forced me to think more about backups.

I tested few gui and command line tools and rsnapshots suits me best, but I have two problems with it:
a) if I want to store data on external nas, then I need co configure rsnapshots to do rsync push and not pull and 
```
snapshot_root   nashome:/mnt/HD/HD_b2/backups/
``` 
does not work. So is this even possible? I can mount remove disc via sshfs, but that won't work either, since creating hardlinks creation is not supported in sshfs.

b) if I want to store it on some more clever server, then I need to setup ecryption (since that server is not solely under my control). Then I can use encfs for example, but than I has to push data to server (otherwise server would have to know passphrase) or I can create encrypted view of mine filesystem, but then in rsnapshots configuration probably has to be encrypted filenames, which isn't great, and also that encrypted view of mine filesystem would have to be mounted all the time for backup server, which seems insane.

any hint how to setup this?

---

