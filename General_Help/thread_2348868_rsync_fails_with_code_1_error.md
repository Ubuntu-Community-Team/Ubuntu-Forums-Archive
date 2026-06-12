---
title: "rsync fails with code 1 error"
date: 2017-01-08
forum: General Help
---

### Post by pdcooper on 2017-01-08
my backup arrangements have recently failed.  - due to stupidity on my part and a typo in the (long) rsync command 




```

~$ rsync -az --backup --backup-dir="backupdir"  --progress -e "ssh blah blah blah ....................
sending incremental file list
rsync error: syntax or usage error (code 1) at main.c(873) [Receiver=3.1.1]
:~$ 
:~$ ssh  offsitebackup  rsync | see
Unescaped left brace in regex is deprecated, passed through in regex; marked by <-- HERE in m/%{ <-- HERE (.*?)}/ at /usr/bin/see line 528.
rsync  version 3.1.1  protocol version 31
Copyright (C) 1996-2014 by Andrew Tridgell, Wayne Davison, and others.
Web site: http://rsync.samba.org/
Capabilities:
    64-bit files, 64-bit inums, 32-bit timestamps, 64-bit long ints,
    socketpairs, hardlinks, symlinks, IPv6, batchfiles, inplace,
    append, ACLs, xattrs, iconv, symtimes, prealloc

```


remote server 
```
:~$ uname -a 
Linux remoteserver 4.2.0-16-generic #19-Ubuntu SMP Thu Oct 8 14:46:51 UTC 2015 i686 i686 i686 GNU/Linux
~$ rsync --version
rsync  version 3.1.1  protocol version 31

```


local client 
```
~$ rsync --version
rsync  version 3.1.1  protocol version 31
$ uname -a
Linux mars 4.4.0-57-generic #78-Ubuntu SMP Fri Dec 9 23:50:32 UTC 2016 x86_64 x8



```

i think this is the same thing 

[https://bbs.archlinux.org/viewtopic.php?id=183921](https://bbs.archlinux.org/viewtopic.php?id=183921)

so how do i get the updated version referred to , for my ubuntu machines ?

---

