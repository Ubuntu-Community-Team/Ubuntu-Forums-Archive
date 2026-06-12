---
title: "a mount command works on one computer but not another."
date: 2013-04-05
forum: General Help
---

### Post by BrentPinkston on 2013-04-05
I have a Seagate GoFlex Home NAS drive.  My primary desktop is running Ubuntu 12.10 and so is my laptop.  The following mount statement works on my desktop, but not the laptop. 

```
sudo mount -t cifs -orw,soft,rsize=8192,wsize=8192,username=myuser,password=mysecretpassword "//192.168.100.21/goflex home backup" /home/bpinkston/backup
```

Here is the error this code generates:

```
mount: wrong fs type, bad option, bad superblock on //192.168.82.21/GoFlex Home Backup,       missing codepage or helper program, or other error
       (for several filesystems (e.g. nfs, cifs) you might
       need a /sbin/mount.<type> helper program)
       In some cases useful info is found in syslog - try
       dmesg | tail  or so



```

Here is the dmesg report for the mount requirement

```
 
[ 3865.446063] CIFS VFS: Connecting to DFS root not implemented yet[ 3865.446132] CIFS VFS: cifs_mount failed w/return code = -22



```

---

### Post by BrentPinkston on 2013-04-05
Never Mind.  I Installed cifs-utils and the script worked fine.

```
sudo apt-get install cifs-utils
```

---

