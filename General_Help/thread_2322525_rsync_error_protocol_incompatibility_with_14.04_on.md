---
title: "rsync error: protocol incompatibility with 14.04 on both local and remote servers"
date: 2016-04-28
forum: General Help
---

### Post by mike4ubuntu on 2016-04-28
after some update, I'm an now getting this error between a local and remote server
```

protocol version mismatch -- is your shell clean?
(see the rsync man page for an explanation)
rsync error: protocol incompatibility (code 2) at compat.c(174) [sender=3.1.0]

```
the strange thing is that both servers have the same version of Ubuntu and same version of rsync.  An even stranger thing is when I have the local server rsync to a 15.10 remote server, it's ok.  Bash shells and logins are configured the same way on all servers.  It used to work until just recently.
local:
```

lic1:/share/logs/rsync$ uname -a
Linux lic1 3.13.0-66-generic #108-Ubuntu SMP Wed Oct 7 15:20:27 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux

lic1:/share/logs/rsync$ version
Linux lic1 3.13.0-66-generic #108-Ubuntu SMP Wed Oct 7 15:20:27 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux
No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu 14.04.4 LTS
Release:	14.04
Codename:	trusty

lic1:/share/logs/rsync$ rsync --version
rsync  version 3.1.0  protocol version 31
Copyright (C) 1996-2013 by Andrew Tridgell, Wayne Davison, and others.
Web site: http://rsync.samba.org/
Capabilities:
    64-bit files, 64-bit inums, 64-bit timestamps, 64-bit long ints,
    socketpairs, hardlinks, symlinks, IPv6, batchfiles, inplace,
    append, ACLs, xattrs, iconv, symtimes, prealloc

rsync comes with ABSOLUTELY NO WARRANTY.  This is free software, and you
are welcome to redistribute it under certain conditions.  See the GNU
General Public Licence for details.


```
remote:
```

lic2:/share/logs/rsync$ uname -a
Linux lic2 3.13.0-85-generic #129-Ubuntu SMP Thu Mar 17 20:50:15 UTC 2016 x86_64 x86_64 x86_64 GNU/Linux

lic2:/share/logs/rsync$ version
Linux lic2 3.13.0-85-generic #129-Ubuntu SMP Thu Mar 17 20:50:15 UTC 2016 x86_64 x86_64 x86_64 GNU/Linux
No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu 14.04.4 LTS
Release:	14.04
Codename:	trusty

lic2:/share/logs/rsync$ rsync --version
rsync  version 3.1.0  protocol version 31
Copyright (C) 1996-2013 by Andrew Tridgell, Wayne Davison, and others.
Web site: http://rsync.samba.org/
Capabilities:
    64-bit files, 64-bit inums, 64-bit timestamps, 64-bit long ints,
    socketpairs, hardlinks, symlinks, IPv6, batchfiles, inplace,
    append, ACLs, xattrs, iconv, symtimes, prealloc

rsync comes with ABSOLUTELY NO WARRANTY.  This is free software, and you
are welcome to redistribute it under certain conditions.  See the GNU
General Public Licence for details.
lic2:/share/logs/rsync$ 

```

I notice only a slight version difference in the 2 kernels and I'm not sure how that happened and how to fix it.  I have installed all updates reported.

any ideas?

---

### Post by mike4ubuntu on 2016-04-29
I solved it by seeing these posts:

[http://www.faqoverflow.com/serverfault/267154.html]("http://www.faqoverflow.com/serverfault/267154.html")
[http://serverfault.com/questions/267154/protocol-version-mismatch-is-your-shell-clean]("http://serverfault.com/questions/267154/protocol-version-mismatch-is-your-shell-clean")

I had a ssh command in sshd_config:
```
ForceCommand /usr/bin/ssh-alert.sh
```
that I must have modified somewhere along the line which had an extra text output on the remote server that was not working with rsync.  I took out that echo ",,," and it works fine now.

---

