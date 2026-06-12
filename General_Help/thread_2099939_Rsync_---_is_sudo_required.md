---
title: "Rsync --- is sudo required?"
date: 2012-12-31
forum: General Help
---

### Post by vasa1 on 2012-12-31
Local Backup
```

sudo rsync -azvv /home/path/folder1/ /home/path/folder2
```
Backup Over Network
```
sudo rsync --dry-run --delete -azvv -e ssh /home/path/folder1/ remoteuser@remotehost.remotedomain:/home/path/folder2
```

^^^
This is quoted from: [https://help.ubuntu.com/community/rsync](https://help.ubuntu.com/community/rsync)

I know sudo isn't needed for a local backup but I don't know about "backup over network".

---

### Post by fdrake on 2012-12-31
can't say it for sure but the man says no!
> 
[B]DESCRIPTION
       Rsync is a fast and extraordinarily versatile file copying  tool.   It
       can  copy  locally,  to/from  another  host  over any remote shell, or
       to/from a remote rsync daemon.  It offers a large  number  of  options
       that  control  every  aspect  of its behavior and permit very flexible
       specification of the set of files to be copied.  It is famous for  its
       delta-transfer  algorithm,  which reduces the amount of data sent over
       the network by sending only the differences between the  source  files
       and  the  existing files in the destination.  Rsync is widely used for
       backups and mirroring and as an improved  copy  command  for  everyday
       use.

       Rsync  finds  files  that need to be transferred using a "quick check"
       algorithm (by default) that looks for files that have changed in  size
       or  in  last-modified  time.   Any  changes  in  the  other  preserved
       attributes (as requested by options) are made on the destination  file
       directly  when the quick check indicates that the file’s data does not
       need to be updated.

       Some of the additional features of rsync are:

       o      support for copying links, devices, owners, groups, and permis&#8208;
              sions

       o      exclude and exclude-from options similar to GNU tar

       o      a  CVS  exclude mode for ignoring the same files that CVS would
              ignore

       o      can use any transparent remote shell, including ssh or rsh

      [SIZE="4"][COLOR="Red"]_** o      does not require super-user privileges**_[/COLOR][/SIZE]

       o      pipelining of file transfers to minimize latency costs

       o      support for anonymous or authenticated rsync daemons (ideal for
              mirroring)
[/B]



---

### Post by The Cog on 2012-12-31
Sudo is only required for two reasons:
1: to gain read/write access to files/directories it would not otherwise have access to, and
2: to be able to set the correct owner/group on files it writes.

When doing a backup for multiple users, then clearly you need both of these abilities. When syncing for a single user, then neither is required. In fact, because you are giving a username for the remote login, running rsync under sudo at your local end won't help with reading/writing remote files anyway.

---

