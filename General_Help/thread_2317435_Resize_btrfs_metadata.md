---
title: "Resize btrfs metadata?"
date: 2016-03-16
forum: General Help
---

### Post by Gijsbert_Wiesenekk on 2016-03-16
Hi,

I am using a 32GB encrypted boot volume that contains a btrfs filesystem with the / and /home subvolumes. I am frequently running out of (metadata) space:

$ sudo btrfs filesystem show /
Label: none  uuid: 3c13ca46-a43b-4d14-9a72-741b5dda3410
    Total devices 1 FS bytes used 9.19GiB
    devid    1 size 29.89GiB used 13.01GiB path /dev/dm-2
$ sudo btrfs filesystem df /
Data, single: total=11.00GiB, used=8.78GiB
System, DUP: total=5.50MiB, used=16.00KiB
Metadata, DUP: total=1.00GiB, used=421.31MiB
unknown, single: total=144.00MiB, used=0.00

1GB has been allocated to metadata with 421 MiB used. I am getting filesystem full errors when metadata size reaches about 550MiB. Rebalancing does not help, I can only recover by deleting snapshots, deleting old kernels and/or deleting files. Is it possible to resize the metadata space to say 2GB?

Gijsbert

---

