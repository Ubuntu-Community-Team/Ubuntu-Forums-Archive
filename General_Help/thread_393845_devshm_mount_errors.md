---
title: "/dev/shm mount errors"
date: 2007-03-26
forum: General Help
---

### Post by unixpaul on 2007-03-26
Hello,

I've got a new VPS install of Dapper  but when it boots, I get the following errors
related to /dev/shm

mount: wrong fs type, bad option, bad superblock on /dev/shm/var.run,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

mount: wrong fs type, bad option, bad superblock on /dev/shm/var.lock,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

I do not have any /etc/fstab entries for these filesystems. 
Where are these being mounted from, and what is the problem?

The system seems to work OK, and after logging in a mount shows they are mounted.

udev                  128M   40K  128M   1% /dev
devshm                128M     0  128M   0% /dev/shm

Any ideas whats causing these errors?

Paul

---

