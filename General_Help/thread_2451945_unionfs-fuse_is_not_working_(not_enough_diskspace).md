---
title: "unionfs-fuse is not working (not enough diskspace)"
date: 2020-10-13
forum: General Help
---

### Post by xconnect on 2020-10-13
Hi there, 

I have just added a new diskarray and mount it with: 
```
#unionfs-fuse -o allow_other /sixteenstore/media/f=rw:/atastorage/media/f=rw:/twelvestore/media/f=rw:/storage/media/f=rw /mnt/virtualf
```

When I copy a file from a disk outside the fuse mount, I get "no diskspace" errors. There is plenty of space on the zfs diskarrays.

```
NAME           SIZE  ALLOC   FREE  CKPOINT  EXPANDSZ   FRAG    CAP  DEDUP    HEALTH  ALTROOT
atastorage     109T   106T  3.57T        -         -     1%    96%  1.00x    ONLINE  -
rpool          222G  5.41G   217G        -         -     2%     2%  1.00x    ONLINE  -
sixteenstore  87.3T  84.6T  2.73T        -         -     0%    96%  1.00x    ONLINE  -
storage       54.6T  51.1T  3.46T        -         -     2%    93%  1.00x    ONLINE  -
twelvestore   65.5T  2.68M  65.5T        -         -     0%     0%  1.00x    ONLINE  -
```

More exactly, when I run: [B]# cp -r "Naturemixscene298673.ts"/ /mnt/virtualf 

[/B]```
cp: cannot create regular file '/mnt/virtualf/Naturemixscene298673.ts': No space left on device
```

What am I doing wrong?


P.S.
I just found something conflicting: 

**# df**
```
Filesystem                              1K-blocks         Used   Available Use% Mounted on
udev                                    263473892            0   263473892   0% /dev
tmpfs                                    52699708        18892    52680816   1% /run
rpool/ROOT/pve-1                        224003072      4170240   219832832   2% /
tmpfs                                   263498536        56160   263442376   1% /dev/shm
tmpfs                                        5120            0        5120   0% /run/lock
tmpfs                                   263498536            0   263498536   0% /sys/fs/cgroup
/dev/nvme0n1p1                         1967952148    768749412  1099166472  42% /mnt/pve/scratch
rpool                                   219832960          128   219832832   1% /rpool
sixteenstore                             29565952         1024    29564928   1% /sixteenstore
sixteenstore/media                    60488117248  60458552320    29564928 100% /sixteenstore/media
rpool/data                              219832960          128   219832832   1% /rpool/data
rpool/ROOT                              219832960          128   219832832   1% /rpool/ROOT
rpool/data/subvol-100-disk-0             73400320      1501440    71898880   3% /rpool/data/subvol-100-disk-0
twelvestore                           45355508736         1024 45355507712   1% /twelvestore
twelvestore/media                     45355508736         1024 45355507712   1% /twelvestore/media
atastorage                              117700736          256   117700480   1% /atastorage
storage                                1257177856          128  1257177728   1% /storage
atastorage/media                      71723496448  71605795968   117700480 100% /atastorage/media
atastorage/backup                      3992710016   3875009536   117700480  98% /atastorage/backup
atastorage/share                        118285568       585088   117700480   1% /atastorage/share
atastorage/data                         117700736          256   117700480   1% /atastorage/data
storage/media                         37774341376  36517163648  1257177728  97% /storage/media
storage/share                          1257177856          128  1257177728   1% /storage/share
storage/containers                     1257177856          128  1257177728   1% /storage/containers
storage/data                           1257177856          128  1257177728   1% /storage/data
storage/backup                         1257207168        29440  1257177728   1% /storage/backup
storage/containers/subvol-101-disk-1    524288000     25308928   498979072   5% /storage/containers/subvol-101-disk-1
/dev/fuse                                   30720           24       30696   1% /etc/pve
tmpfs                                    52699704            0    52699704   0% /run/user/0
unionfs-fuse                         154853346304 108122961920 46730384384  70% /mnt/virtualtv
unionfs-fuse                         154853346304 108122961920 46730384384  70% /mnt/virtualb
unionfs-fuse                         154853346304 108122961920 46730384384  70% /mnt/virtualhv
unionfs-fuse                         154853346304 108122961920 46730384384  70% /mnt/virtuald
unionfs-fuse                         154853346304 108122961920 46730384384  70% /mnt/virtualm
unionfs-fuse                         154853346304 108122961920 46730384384  70% /mnt/virtualstv
unionfs-fuse                         154853346304 108122961920 46730384384  70% /mnt/virtualp
unionfs-fuse                         215341463552 168581514240 46759949312  79% /mnt/virtualf
```

Still very strange!

---

