---
title: "Replace Disk In ZFS Mirrored Pool"
date: 2016-02-03
forum: General Help
---

### Post by Brando569 on 2016-02-03
I have a Mirrored ZFS pool and I've been replacing my 3 TB WD Green drives with 4 TB HGST NAS drives. I was using FreeNAS (FreeBSD 9.3) for about a year but just a few days ago decided to switch back to Linux since BSD has been annoying me. I swapped one of the drives out with the FreeNAS GUI, but now I'm trying to figure out how to replace one of the drives from the command line but can't seem to figure it out. I already offlined and detached the last 3 TB disk (still works and still contains data) and tried to replace it with the 4 TB drive (I didn't want to do an in-place replacement since the Pool drives are attached to an Intel HBA and the replacement drive would be on a SATA 1.5 link) but it's not working, probably because I'm not doing it correctly.

```
root@nas:/home/bran# zpool status
  pool: pool
 state: ONLINE
  scan: resilvered 2.10T in 5h0m with 0 errors on Fri Jan 29 00:53:14 2016
config:

        NAME                                          STATE     READ WRITE CKSUM
        pool                                          ONLINE       0     0     0
          mirror-0                                    ONLINE       0     0     0
            ata-WDC_WD10JFCX-68N6GN0_WD-WXN1E74LS79A  ONLINE       0     0     0
            ata-WDC_WD10JFCX-68N6GN0_WD-WXN1E743TFVA  ONLINE       0     0     0
          mirror-1                                    ONLINE       0     0     0
            ata-HGST_HDN724040ALE640_PK2338P4H08E2C   ONLINE       0     0     0
            ata-HGST_HDN724040ALE640_PK2334PCJL6H5B   ONLINE       0     0     0
          mirror-2                                    ONLINE       0     0     0
            ata-HGST_HDN724040ALE640_PK1334PCK32T6S   ONLINE       0     0     0
            ata-HGST_HDN724040ALE640_PK2331PBJ2ZRXT   ONLINE       0     0     0
          ata-HGST_HDN724040ALE640_PK1334PCJBG98S     ONLINE       0     0     0
        logs
          ata-INTEL_SSDSC2BA100G3_BTTV543501W8100FGN  ONLINE       0     0     0
```

** ata-HGST_HDN724040ALE640_PK1334PCJBG98S ** Is the half of the last mirror that I would like to attach the new drive (**ata-HGST_HDN724040ALE640_PK2381PBJEPTHT**) to but I get the following errors and don't want to destroy my data by messing around (Happened before with FreeNAS when I was trying to replace a drive).

```
root@nas:/home/bran# zpool attach pool /dev/disk/by-id/ata-HGST_HDN724040ALE640_PK2381PBJEPTHTmissing <new_device> specification
usage:
        attach [-f] [-o property=value] <pool> <device> <new-device>


root@nas:/home/bran# zpool attach pool /dev/disk/by-id/ata-HGST_HDN724040ALE640_PK2381PBJEPTHT /dev/disk/by-id/ata-HGST_HDN724040ALE640_PK1334PCJBG98S
the kernel failed to rescan the partition table: 16
cannot label 'sdf': try using parted(8) and then provide a specific slice: -1
```

These are all of my HGST disks, something interesting here is that the first device **sdf** doesn't have partitions and the new disk **sdc** does

```
root@nas:/home/bran# ls -lh /dev/disk/by-id/|grep -i hgst
lrwxrwxrwx 1 root root  9 Feb  3 17:45 ata-HGST_HDN724040ALE640_PK1334PCJBG98S -> ../../sdf

lrwxrwxrwx 1 root root  9 Feb  3 17:45 ata-HGST_HDN724040ALE640_PK1334PCK32T6S -> ../../sdg
lrwxrwxrwx 1 root root 10 Feb  3 16:11 ata-HGST_HDN724040ALE640_PK1334PCK32T6S-part1 -> ../../sdg1
lrwxrwxrwx 1 root root 10 Feb  3 16:11 ata-HGST_HDN724040ALE640_PK1334PCK32T6S-part2 -> ../../sdg2

lrwxrwxrwx 1 root root  9 Feb  3 16:11 ata-HGST_HDN724040ALE640_PK2331PBJ2ZRXT -> ../../sdh
lrwxrwxrwx 1 root root 10 Feb  3 16:11 ata-HGST_HDN724040ALE640_PK2331PBJ2ZRXT-part1 -> ../../sdh1
lrwxrwxrwx 1 root root 10 Feb  3 16:11 ata-HGST_HDN724040ALE640_PK2331PBJ2ZRXT-part2 -> ../../sdh2

lrwxrwxrwx 1 root root  9 Feb  3 17:45 ata-HGST_HDN724040ALE640_PK2334PCJL6H5B -> ../../sdd
lrwxrwxrwx 1 root root 10 Feb  3 16:11 ata-HGST_HDN724040ALE640_PK2334PCJL6H5B-part1 -> ../../sdd1

lrwxrwxrwx 1 root root  9 Feb  3 17:45 ata-HGST_HDN724040ALE640_PK2338P4H08E2C -> ../../sde
lrwxrwxrwx 1 root root 10 Feb  3 16:11 ata-HGST_HDN724040ALE640_PK2338P4H08E2C-part1 -> ../../sde1

lrwxrwxrwx 1 root root  9 Feb  3 17:45 ata-HGST_HDN724040ALE640_PK2381PBJEPTHT -> ../../sdc
lrwxrwxrwx 1 root root 10 Feb  3 17:11 ata-HGST_HDN724040ALE640_PK2381PBJEPTHT-part1 -> ../../sdc1
lrwxrwxrwx 1 root root 10 Feb  3 17:11 ata-HGST_HDN724040ALE640_PK2381PBJEPTHT-part9 -> ../../sdc9
```

---

### Post by lukeiamyourfather on 2016-02-09
It looks like ata-HGST_HDN724040ALE640_PK1334PCJBG98S was added to the pool as a stand alone drive VDEV with no redundancy. I'd backup the pool and create it again because if that lone drive fails then the pool will be lost.

In the future use the replace command to replace a drive, see the example below assuming the pool is called tank. Also if you want the capacity of the pool to increase (like if you're replacing all of the drives one by one) then enable auto expansion before you begin which is disabled by default and can't be enabled after the fact.

```
sudo zpool set autoexpand=on tank
sudo zpool replace tank ata-WDC_old_and_busted ata-HGST_new_hotness
```

With that many drives you might consider moving to RAID Z2 if you create the pool again.

---

### Post by Brando569 on 2016-02-10
Hey thanks for the reply, sadly everything was lost. I had rebooted my NAS and after that it wouldnt mount the pool, after talking to the guys in #ZFSonLinux for about an hour or so we came to the conclusion that it was FUBAR. I wish I would have know about the autoexpand option earlier since I have already recreated the pool.

---

### Post by lukeiamyourfather on 2016-02-11
Just to clarify, the auto expansion option can be enabled at anytime before upgrading one of the drives. So if you just created a new pool, I'd enable it now. There's no reason not to.

---

### Post by Brando569 on 2016-02-11
Ah cool, thanks for the info!

---

