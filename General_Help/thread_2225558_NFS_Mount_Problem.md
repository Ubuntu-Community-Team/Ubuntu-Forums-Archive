---
title: "NFS Mount Problem"
date: 2014-05-22
forum: General Help
---

### Post by pravinxyz on 2014-05-22
I am using netapp cmode storage. The problem seems to be only with version Ubuntu VERSION="14.04, Trusty Tahr" where i am unable to mount the volume 

root@block:~# mount -t nfs4 10.238.229.43:/open_test /pra/
mount.nfs4: access denied by server while mounting 10.238.229.43:/open_test

able to mount the root volume for netapp on this box
root@block:~# mount -t nfs4 10.238.229.43:/ /pra/
root@block:~# cd /pra/
root@block:/pra# ls
open_test

root@block:/pra# cd /pra/open_test/
bash: cd: /pra/open_test/: Permission denied




I have tried change changing the values and nothing helped.

# If you do not set values for the NEED_ options, they will be attempted
# autodetected; this should be sufficient for most people. Valid alternatives
# for the NEED_ options are "yes" and "no".

# Do you want to start the statd daemon? It is not needed for NFSv4.
NEED_STATD=yes

# Options for rpc.statd.
#   Should rpc.statd listen on a specific port? This is especially useful
#   when you have a port-based firewall. To use a fixed port, set this
#   this variable to a statd argument like: "--port 4000 --outgoing-port 4001".
#   For more information, see rpc.statd(8) or [http://wiki.debian.org/SecuringNFS](http://wiki.debian.org/SecuringNFS)
STATDOPTS=

# Do you want to start the gssd daemon? It is required for Kerberos mounts.
NEED_GSSD=no



This is on other machine which the mount work fine
[root@nbmonitor tmp]# mount
10.238.229.43:/open_test on /mnt/tmp type nfs (rw,addr=10.238.229.43)

---

