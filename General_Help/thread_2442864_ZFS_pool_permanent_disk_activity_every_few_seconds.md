---
title: "ZFS pool permanent disk activity every few seconds"
date: 2020-05-08
forum: General Help
---

### Post by izeman on 2020-05-08
I know the topic is a bit cryptic.

I got a 3+1 zfs raid, and I can't find out what causes this permanent disk activity.

I do "zfs mount data" all 4 disks show heavy head movement noise (7k2 server disks) for a second or so. Then it's quiet for a few second and then noise again. And so on and so on.
Once I unmount the pool everything is totally quiet again.

All accessing services like nfs and smb are stopped (otherwise I couldn't unmount anyway).

I did some "lsof /path-to-zfs-mount, but it doesn't show any file activity.

The pool itself is healthy ...

Any idea how i can find out what's going on here? It's and annoying background sound - i have my working table next to the server.

Thanks

---

### Post by izeman on 2020-05-08
I just measured the times if this helps. It's roughly 2s activity, 3s pause.

Maybe something here helps:

```
root@fileserver:~# zfs get all
NAME  PROPERTY              VALUE                  SOURCE
data  type                  filesystem             -
data  creation              Mi Mär 18 13:59 2020  -
data  used                  6,10T                  -
data  available             1,78T                  -
data  referenced            6,10T                  -
data  compressratio         1.00x                  -
data  mounted               yes                    -
data  quota                 none                   default
data  reservation           none                   default
data  recordsize            128K                   default
data  mountpoint            /data                  local
data  sharenfs              off                    default
data  checksum              on                     default
data  compression           off                    default
data  atime                 on                     default
data  devices               on                     default
data  exec                  on                     default
data  setuid                on                     default
data  readonly              off                    default
data  zoned                 off                    default
data  snapdir               hidden                 default
data  aclinherit            restricted             default
data  createtxg             1                      -
data  canmount              on                     default
data  xattr                 on                     default
data  copies                1                      default
data  version               5                      -
data  utf8only              off                    -
data  normalization         none                   -
data  casesensitivity       sensitive              -
data  vscan                 off                    default
data  nbmand                off                    default
data  sharesmb              off                    default
data  refquota              none                   default
data  refreservation        none                   default
data  guid                  9080374912943241696    -
data  primarycache          all                    default
data  secondarycache        all                    default
data  usedbysnapshots       0B                     -
data  usedbydataset         6,10T                  -
data  usedbychildren        19,6M                  -
data  usedbyrefreservation  0B                     -
data  logbias               latency                default
data  dedup                 off                    default
data  mlslabel              none                   default
data  sync                  standard               default
data  dnodesize             legacy                 default
data  refcompressratio      1.00x                  -
data  written               6,10T                  -
data  logicalused           6,10T                  -
data  logicalreferenced     6,10T                  -
data  volmode               default                default
data  filesystem_limit      none                   default
data  snapshot_limit        none                   default
data  filesystem_count      none                   default
data  snapshot_count        none                   default
data  snapdev               hidden                 default
data  acltype               off                    default
data  context               none                   default
data  fscontext             none                   default
data  defcontext            none                   default
data  rootcontext           none                   default
data  relatime              off                    default
data  redundant_metadata    all                    default
data  overlay               off                    default
```

---

### Post by kneutron on 2020-05-29
--This is what I have in my /etc/rc.local:

[COLOR=#34BC26][FONT=Menlo][COLOR=#000000]# 2018.0819 FIX for writing ~150KB/sec to zfs /home[/COLOR][/FONT][/COLOR]
[COLOR=#28FE14][FONT=Menlo][COLOR=#000000]**cd** /sys/module/zfs/parameters && **\**[/COLOR][/FONT][/COLOR]
[COLOR=#28FE14][FONT=Menlo][COLOR=#000000]  tmpv=zfs_txg_timeout;         **[** -e **$tmpv** ] && **echo** 30 > **$tmpv**[/COLOR][/FONT][/COLOR]
[COLOR=#28FE14][FONT=Menlo][COLOR=#000000]
[/COLOR][/FONT][/COLOR]
[COLOR=#34BC26][FONT=Menlo][COLOR=#000000]# 1,073,741,824 *4[/COLOR][/FONT][/COLOR]
[COLOR=#28FE14][FONT=Menlo][COLOR=#000000]  tmpv=zfs_arc_max;             **[** -e **$tmpv** ] && **echo** 4294967296 > **$tmpv** # limit zfs RAM usage[/COLOR][/FONT][/COLOR]
[COLOR=#28FE14][FONT=Menlo][COLOR=#000000]
[/COLOR][/FONT][/COLOR]
[COLOR=#28FE14][FONT=Menlo][COLOR=#000000]  tmpv=zfetch_max_distance;     **[** -e **$tmpv** ] && **echo** 52428800 > **$tmpv** # prefetch 50MB - should speed up reads for VM resumes[/COLOR][/FONT][/COLOR]
[COLOR=#34BC26][FONT=Menlo][COLOR=#000000]# 52,428,800 # prefetch 50MB - should speed up reads for VM resumes[/COLOR][/FONT][/COLOR]
[COLOR=#34BC26][FONT=Menlo][COLOR=#000000]# REF: [https://github.com/openzfs/zfs/wiki/ZFS-on-Linux-Module-Parameters#zfetch_max_distance](https://github.com/openzfs/zfs/wiki/ZFS-on-Linux-Module-Parameters#zfetch_max_distance)[/COLOR][/FONT][/COLOR]
[COLOR=#28FE14][FONT=Menlo][COLOR=#000000]**cd** -

[/COLOR][/FONT][/COLOR]############

--The part that concerns you is the 1st one, it sets the zfs commit time to 30 seconds to delay writes for a bit.  The others may help; the 2nd one limits ZFS RAM usage to 4GB and the 3rd seems to help speed up large reads.
[COLOR=#28FE14][FONT=Menlo]

[/FONT][/COLOR]

---

