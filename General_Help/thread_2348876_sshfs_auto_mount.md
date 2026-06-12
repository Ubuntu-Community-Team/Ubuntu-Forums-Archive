---
title: "sshfs auto mount"
date: 2017-01-08
forum: General Help
---

### Post by marchello_lippi2 on 2017-01-08
Hi all, 

My need is to auto mount remote ssh directory. This is how I do it manually: 

```

sudo sshfs -o allow_other user1@host1:/home/user1 /mnt/directory1

```

Please advise the best way to automate it. 
Thanks ahead.

---

### Post by TheFu on 2017-01-08
No need for sudo.  ssh is a FUSE connection, not a system connection.

1) chown /mnt/directory1 # to your useid on this machine.
2) Create a script that runs every time you login to the machine
3) That script should check for the existence of the mount - if it doesn't exist, the mount it.

Or  use autofs - [https://help.ubuntu.com/community/Autofs](https://help.ubuntu.com/community/Autofs)
[https://help.ubuntu.com/community/Autofs#FUSE_based_file_systems](https://help.ubuntu.com/community/Autofs#FUSE_based_file_systems)

BTW, thanks for asking this question. I'll be setting up the autofs version for my laptop to a server here that isn't already running NFS.

So - just spend the last 15 min trying to setup autofs following 3 different guides. It isn't working.  I use sshfs all-the-time and have been using autofs for CIFS and NFS for about 20 yrs.  Maybe I'm just tired. Fresh eyes needed. This stuff isn't very complicated.

---

### Post by marchello_lippi2 on 2017-02-26
Just spent few minutes trying to follow this guide [http://www.tjansson.dk/2008/01/autofs-and-sshfs-the-perfect-couple/](http://www.tjansson.dk/2008/01/autofs-and-sshfs-the-perfect-couple/) 

Yes, it does creates additional subfolder in my /mnt/sshfs folder when I open it, but when I try to enter the subfolder, it says that directory does not exist. 

Got errors in syslog: 

sudo less /var/log/syslog
> 
Feb 26 18:33:49 MyPC automount[19538]: state.c:622: assertion failed: ap->state == ST_READY || ap->state == ST_EXPIRE
Feb 26 18:33:49 MyPC automount[19538]: nextstate:85: write failed Bad file descriptor
Feb 26 18:33:54 MyPC kernel: [18338.012914] init: autofs main process (19538) killed by **KILL** signal
Feb 26 18:34:10 MyPC automount[20898]: key ".directory" not found in map source(s).


(just BTW, I did not kill anything). 

> 
# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.
# Parameters can be specified after the module name.

lp
fuse
/etc/modules (END)


> 
#
# Sample auto.master file
# This is an automounter map and it has the following format
# key [ -mount-options-separated-by-comma ] location
# For details of the format look at autofs(5).
#
#/misc  /etc/auto.misc
#
# NOTE: mounts done from a hosts map will be mounted with the
#       "nosuid" and "nodev" options unless the "suid" and "dev"
#       options are explicitly given.
#
#/net   -hosts
#
# Include /etc/auto.master.d/*.autofs
#
+dir:/etc/auto.master.d
#
# Include central master map if it can be found using
# nsswitch sources.
#
# Note that if there are entries for /net or /misc (as
# above) in the included master map any keys that are the
# same will not be seen as the first read key seen takes
# precedence.
#
+auto.master
/mnt/sshfs /etc/auto.sshfs uid=1000,gid=1000,--timeout=30,--ghost
/etc/auto.master (END)


> 
nout -fstype=fuse,rw,nodev,nonempty,noatime,allow other,max read=65536 :sshfs\#user1@host1\:
osmc -fstype=fuse,rw,nodev,nonempty,noatime,allow other,max read=65536 :sshfs\#user2@host2\:
/etc/auto.sshfs (END)


Please advise.

---

