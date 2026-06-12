---
title: "Synaptic and update manager will not start"
date: 2013-10-14
forum: General Help
---

### Post by CEB2nd on 2013-10-14
Hi,

Started having this problem a few days ago.  Any time I try to run synaptic or update manager I get this error:

E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/dpkg/status
E: The package lists or status file could not be parsed or opened.
E: _cache->open() failed, please report.

W: Encountered status field in a non-version description

Ubuntu software center doesn't work either.  Also, they cannot be started from terminal.

Lucid 10.04

Thanks for any help.

---

### Post by bapoumba on 2013-10-14
Probably the solution here : [http://ubuntuforums.org/showthread.php?t=863742](http://ubuntuforums.org/showthread.php?t=863742)
```
udo rm /var/lib/apt/lists/* -vf
sudo apt-get update
```

---

### Post by CEB2nd on 2013-10-14
I found what was causing the problem.  In var/lib/dpkg there were two status files, status and status-old.  I
changed the the name of status to status-new and started using the old file, problem solved.  Interesting
thing is both files were created on the same date.

Hope this helps someone else.

---

### Post by bapoumba on 2013-10-15
Thanks for posting a follow up :)

---

