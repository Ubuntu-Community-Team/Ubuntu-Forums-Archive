---
title: "Low disk space, but I should have at least 16 gigs."
date: 2014-01-09
forum: General Help
---

### Post by MasterShadow on 2014-01-09
I'm using ubuntu 12.04, and a warning always comes up saying I only have very little disk space left. I used bleach bit, tweak, some commands throught the terminal, but nothing works. 

When I put the commant df -h, it'll give:

/dev/sda2        26G   11G   16G  41% /host

When I use disk usage analyzer it says 10.5 GB are used under disks. Then 1.9 GB under usr.

---

### Post by Bashing-om on 2014-01-09
MasterShadow; Hi !

The df command does not lie, but may not tell the whole story.
Post back to us the complete output of terminal commands:
```

df -h
df -i

```
Which will indicate where to look for the space constraint.

[INDENT][INDENT]my bit to try and help
[/INDENT][/INDENT]

---

### Post by Mark Phelps on 2014-01-09
> /dev/sda2 26G 11G 16G 41% /host

See that "/host"?  That means you installed using Wubi  -- in which the installer created a single file (root.disk) INSIDE a Windows partition and runs from there.  From what I recall, 16GB is the maximum size limit of a Wubi install.

---

### Post by MasterShadow on 2014-01-09
> **Bashing-om said:**
> MasterShadow; Hi !

The df command does not lie, but may not tell the whole story.
Post back to us the complete output of terminal commands:
```

df -h
df -i

```
Which will indicate where to look for the space constraint.[INDENT][INDENT]my bit to try and help
[/INDENT]
[/INDENT]


Here's df -h

```
df: `/root/.gvfs': Permission denied
Filesystem      Size  Used Avail Use% Mounted on
/dev/loop0      9.3G  8.8G  3.7M 100% /
udev            742M  4.0K  742M   1% /dev
tmpfs           301M  876K  300M   1% /run
none            5.0M     0  5.0M   0% /run/lock
none            751M  156K  750M   1% /run/shm
/dev/sda2        26G   11G   16G  41% /host
/dev/sdb1        15G   68M   15G   1% /media/43845E1D0505BFD7
```

Then df -i 

```
df: `/root/.gvfs': Permission denied
Filesystem       Inodes  IUsed    IFree IUse% Mounted on
/dev/loop0       624624 148059   476565   24% /
udev             189938    531   189407    1% /dev
tmpfs            192002    465   191537    1% /run
none             192002      3   191999    1% /run/lock
none             192002      7   191995    1% /run/shm
/dev/sda2      16272416     54 16272362    1% /host
/dev/sdb1      15417792     23 15417769    1% /media/43845E1D0505BFD7
```

---

### Post by MasterShadow on 2014-01-09
> **Mark Phelps said:**
> See that "/host"?  That means you installed using Wubi  -- in which the installer created a single file (root.disk) INSIDE a Windows partition and runs from there.  From what I recall, 16GB is the maximum size limit of a Wubi install.

So, what does that mean?

---

### Post by MasterShadow on 2014-01-09
Wait, if I remove windows, will it remove ubuntu too?

---

### Post by Impavidus on 2014-01-09
Your Ubuntu is installed on a virtual Linux partition of 9GB on a Windows partition of 26GB. This Windows partition is what you see under /host. There is still 16GB free on /host, that is on the Windows partition, but this space is only available for files stored in the /host directory. And indeed, if you remove Windows, Ubuntu will be gone too.

It is possible to resize a wubi installation: [https://help.ubuntu.com/community/ResizeandDuplicateWubiDisk](https://help.ubuntu.com/community/ResizeandDuplicateWubiDisk). I think the maximum is 30GB.

Wubi is being fased out and no longer supported for the latest releases. It was intended as a longer term trial mode, without a need for repartitioning and with easy uninstall. You may consider moving to a true dual boot ([https://help.ubuntu.com/community/MigrateWubi](https://help.ubuntu.com/community/MigrateWubi)), but another option has to be considered too.

For you it may be best to increase the size of your wubi installation with a few GB and then wait for the new LTS release, which is planned come in April. Instead of migrating to a dual boot and then upgrading you can then just do a clean install.

---

