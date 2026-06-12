---
title: "Problem sharing home directory with nfs"
date: 2013-11-21
forum: General Help
---

### Post by xeddog on 2013-11-21
I have a small collection of linux machines in a home network, mostly running Ubuntu.  On my "main" machine (Stealth running Ubuntu 12.04.3) I have relocated my home directory to a second hard drive (sdb1) in the machine.  I set up all machines to export their root filesystems, and that is all working fine with one exception.  The other machines all mount Stealth's root file system just fine, but if I navigate to /home/userid I get the home directory on sda1, which is essentially empty, instead of the one I want on sdb1.

The /etc/exports initially looked like this:
```
# /etc/exports: the access control list for filesystems which may be exported
#		to NFS clients.  See exports(5).
#
# Example for NFSv2 and NFSv3:
# /srv/homes       hostname1(rw,sync,no_subtree_check) hostname2(ro,sync,no_subtree_check)
#
# Example for NFSv4:
# /srv/nfs4        gss/krb5i(rw,sync,fsid=0,crossmnt,no_subtree_check)
# /srv/nfs4/homes  gss/krb5i(rw,sync,no_subtree_check)
#
#
/	Intrepid(rw,sync,no_root_squash,no_subtree_check,fsid=0) G-Man(rw,sync,no_root_squash,no_subtree_check,fsid=0)
#
```

I have tried several things in /etc/exports to get it working properly, including this which is the last thing I have tried:
```
/home/twoblues	10.1.1.0/24(rw,sync,no_root_squash,no_subtree_check,fsid=901a81bd-f7a3-4a64-9377-bd855dfcd603,crossmnt)
```
where the uuid specified is sdb1, but even with this I still get the wrong home directory.

I either restart nfs-kernel-server and autofs, or reboot between each modification.

Any ideas how I can get the correct home directory to mount???


Thanks,

X

---

