---
title: "mount CIFS - bad UNC"
date: 2015-04-27
forum: General Help
---

### Post by cbrun on 2015-04-27
I recently migrated from ubuntu 12 to 14 and seem to have lost the ability to mount my Windows file share (drive S: ) I'm getting a bad UNC error.  Tried both command line and fstab (original from when I ran 12.04).  

root@nm:/# mount -t cifs dpm-2.xxxxx.org:S /mnt/dpm2 -o username=xxxxx,password=xxxxxmount.cifs: bad UNC (dpm-2.xxxxx.org:S)

I know it resolves so DNS is OK:
root@nm:/# ping dpm-2.xxxxx.org
PING dpm-2.xxxxx.org (101.216.211.42) 56(84) bytes of data.
64 bytes from dpm-2.xxxxx.org (101.216.211.42): icmp_seq=1 ttl=128 time=0.449 ms

Here is the original fstab entry:
dpm-2.xxxxx.org:S /mnt/dpm2 cifs usernam=xxxxx,password=xxxxx  0  0
root@nm:/# mount -a
mount.cifs: bad UNC (dpm-2.xxxxx.org:S)

Am I misformatting the UNC?

---

### Post by cbrun on 2015-04-29
Format of the mount command:
mount -t cifs dpm-2.xxxxx.org:S 

should have read:
mount -t cifs dpm-2.xxxxx.org/S

---

