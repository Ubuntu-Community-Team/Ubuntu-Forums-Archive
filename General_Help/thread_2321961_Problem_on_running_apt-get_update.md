---
title: "Problem on running apt-get update"
date: 2016-04-25
forum: General Help
---

### Post by satimis on 2016-04-25
Hi all,

Ubuntu 14.04 desktop

$ sudo apt-get update```

.....
.....
W: Failed to fetch http://hk.archive.ubuntu.com/ubuntu/dists/trusty-updates/main/binary-amd64/Packages  Hash Sum mismatch

W: Failed to fetch http://hk.archive.ubuntu.com/ubuntu/dists/trusty-updates/main/binary-i386/Packages  Hash Sum mismatch

E: Some index files failed to download. They have been ignored, or old ones used instead.

```

Neither;
sudo rm /var/lib/apt/lists/* -vf

nor;
sudo apt-get clean

can solve the problem.  Please help.  Thanks

Regards
satimis

---

### Post by Bashing-om on 2016-04-25
satimis; Hello;

Maybe nothing more than your mirror awaiting updating/syncing up with mother . Wait a few hours and try again .. 
Else, one can change the mirror site and see what results.

[INDENT][INDENT]it is a process
[/INDENT][/INDENT]

---

