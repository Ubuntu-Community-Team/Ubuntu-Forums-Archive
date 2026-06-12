---
title: "updatedb errors"
date: 2008-04-27
forum: General Help
---

### Post by jjberry on 2008-04-27
when using $ locate I get this error:

locate: can not open `/var/lib/mlocate/mlocate.db': No such file or directory

when I try $ sudo updatedb I get this:

updatedb:/etc/updatedb.conf:4: unknown variable `FINDOPTIONS'
updatedb:/etc/updatedb.conf:5: unknown variable `export'
updatedb:/etc/updatedb.conf:8: unknown variable `export'
updatedb:/etc/updatedb.conf:11: unknown variable `export'
updatedb:/etc/updatedb.conf:13: unknown variable `NETPATHS'
updatedb:/etc/updatedb.conf:14: unknown variable `export'
updatedb:/etc/updatedb.conf:16: unknown variable `LOCALUSER'
updatedb:/etc/updatedb.conf:17: unknown variable `export'
updatedb:/etc/updatedb.conf:20: unknown variable `NICE'
updatedb:/etc/updatedb.conf:21: unknown variable `export'
updatedb:/etc/updatedb.conf:24: unknown variable `IONICE_CLASS'
updatedb:/etc/updatedb.conf:25: unknown variable `export'
updatedb:/etc/updatedb.conf:27: unknown variable `IONICE_PRIORITY'
updatedb:/etc/updatedb.conf:28: unknown variable `export'

The same error occurs for $ sudo /etc/cron.daily/mlocate

my updatedb.conf looks like this:

# This file sets environment variables which are used by updatedb

# Global options for invocations of find(1)
FINDOPTIONS='-ignore_readdir_race'
export FINDOPTIONS
# filesystems which are pruned from updatedb database
PRUNEFS="NFS nfs nfs4 afs binfmt_misc proc smbfs autofs iso9660 ncpfs coda devpts ftpfs devfs mfs shfs sysfs cifs lustre_lite tmpfs usbfs udf vmhgfs"
export PRUNEFS
# paths which are pruned from updatedb database
PRUNEPATHS="/tmp /usr/tmp /var/tmp /afs /amd /alex /var/spool /sfs /media"
export PRUNEPATHS
# netpaths which are added
NETPATHS=""
export NETPATHS
# run find as this user
LOCALUSER="nobody"
export LOCALUSER
# cron.daily/find: run at this priority -- higher number means lower priority
# (this is relative to the default which cron sets, which is usually +5)
NICE=10
export NICE
# cron.daily: I/O priority
# 1 for real time, 2 for best-effort (3 for idle is only allowed for root!)
IONICE_CLASS=2
export IONICE_CLASS
# 0-7 (for IONICE_CLASS 1 and 2 only), 0=highest, 7=lowest 
IONICE_PRIORITY=7
export IONICE_PRIORITY


I'm running Hardy on vmware-fusion

Any ideas?

---

### Post by mykmelez on 2008-06-07
This problem is caused by the mlocate package not installing its /etc/updatedb.conf file.  Instead, it leaves the previous implementation of locate's /etc/updatedb.conf file in place, but it doesn't understand the configuration in that file, so it spews those errors you see when you try to run updatedb, and then it dies without building the database.

I have filed [bug 238062]("https://bugs.launchpad.net/ubuntu/+source/mlocate/+bug/238062") on the problem.  While waiting for the bug to be fixed, you can work around it by downloading the package manually from packages.ubuntu.com <[http://packages.ubuntu.com/hardy/mlocate]("http://packages.ubuntu.com/hardy/mlocate")>, extracting the file (f.e. using file-roller), which is in mlocate_0.18-2ubuntu1_i386.deb / data.tar.gz / etc / updatedb.conf, and copying it to /etc/updatedb.conf:

```
sudo cp /etc/updatedb.conf /etc/updatedb.conf.bak
sudo cp extracted-file /etc/updatedb.conf

```
At the moment, with version 0.18-2ubuntu1 of mlocate, the file looks like this:

```
PRUNE_BIND_MOUNTS="yes"
PRUNEPATHS="/tmp /var/spool /media"
PRUNEFS="NFS nfs nfs4 afs binfmt_misc proc smbfs autofs iso9660 ncpfs coda devpts ftpfs devfs mfs shfs sysfs cifs lustre_lite tmpfs usbfs udf rpc_pipefs"

```
So you could just create the file and copy that text into it.  But that's a less robust solution, since the file could change in the future.

Note: if you are running Ubuntu in a VM using VMWare Fusion, you'll want to add "vmhgfs" to the list of PRUNEFS, i.e. the text should be:

```
PRUNE_BIND_MOUNTS="yes"
PRUNEPATHS="/tmp /var/spool /media"
PRUNEFS="NFS nfs nfs4 afs binfmt_misc proc smbfs autofs iso9660 ncpfs coda devpts ftpfs devfs mfs shfs sysfs cifs lustre_lite tmpfs usbfs udf rpc_pipefs vmhgfs"

```

Or rerun vmware-config-tools, and it should make that change for you.

---

### Post by mykmelez on 2008-06-07
Note: I reinstalled VMWare tools after fixing the problem, and the problem then reappeared, because vmware-config-tools.pl overwrote /etc/updatedb.conf with /etc/updatedb.conf.BeforeVMwareToolsInstall, which contained an older version of the file.

So I deleted that file, copied updatedb.conf from the mlocate package to /etc/updatedb.conf once again, and reran vmware-config-tools.pl, whereupon it copied the new version to /etc/updatedb.conf.BeforeVMwareToolsInstall and then updated /etc/updatedb.conf to include vmhgfs in the PRUNEFS list.

---

