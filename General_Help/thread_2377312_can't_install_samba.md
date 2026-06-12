---
title: "can't install samba"
date: 2017-11-11
forum: General Help
---

### Post by MZ250Supa5 on 2017-11-11
I'm getting a ```
E: Sub-process /usr/bin/dpkg returned an error code (1)
``` message related to installing samba, and it's being a real pain. I checked out this thread, [https://ubuntuforums.org/showthread.php?t=2348602](https://ubuntuforums.org/showthread.php?t=2348602) as it seems to be the most recent, but none of what is there applies in my case, as all that has been done there to solve the issue has already been done in my case, probably as part of an upgrade. When I try to install samba, I get this output

```
insserv: exiting now without changing boot order!
update-rc.d: error: insserv rejected the script header
dpkg: error processing package samba (--configure):
 subprocess installed post-installation script returned error exit status 1
Setting up attr (1:2.4.47-2) ...
Setting up libaio1:amd64 (0.3.110-2) ...
Setting up samba-dsdb-modules (2:4.3.11+dfsg-0ubuntu0.16.04.11) ...
Setting up samba-vfs-modules (2:4.3.11+dfsg-0ubuntu0.16.04.11) ...
Processing triggers for libc-bin (2.23-0ubuntu9) ...
Processing triggers for systemd (229-4ubuntu21) ...
Processing triggers for ureadahead (0.100.0-19) ...
Processing triggers for ufw (0.35-0ubuntu2) ...
Errors were encountered while processing:
 samba
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

It'd be great to know how to solve this, as it's currently doing my head in a bit!

---

