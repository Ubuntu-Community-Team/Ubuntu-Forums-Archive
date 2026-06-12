---
title: "Recovery of a zfs volume on an OLD (2010/2011) linux box"
date: 2020-04-25
forum: General Help
---

### Post by jaco-tech on 2020-04-25
I am posting this in the hope it can help someone else, in the unlikely case they come across the same problem. I  have broke my head over it for a long time to find this solution.

In 2010/2011 i used this linux box as a fileserver, some years later it moved to the attic to gather dust.
Recently i took it down and wanted to get it up in search of some file i think were on it and were not on my backups.

So the system is pretty outdated:

```
root@egor:~# uname -a
Linux egor 2.6.32-32-generic #62-Ubuntu SMP Wed Apr 20 21:52:38 UTC 2011 x86_64 GNU/Linux
root@egor:~# cat /etc/issue
Ubuntu 10.04.2 LTS

```
It has a small ssd system disk and 4 sata disks. sdb, sdc, sdd, sde
sde seems to have failed over its time in the attic

```

[ 2497.967294] ata4.00: status: { DRDY ERR }
[ 2497.967296] ata4.00: error: { UNC }
[ 2498.380602] ata4.00: configured for UDMA/133
[ 2498.380613] sd 3:0:0:0: [sde] Unhandled sense code
[ 2498.380615] sd 3:0:0:0: [sde] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 2498.380619] sd 3:0:0:0: [sde] Sense Key : Medium Error [current] [descriptor]
[ 2498.380623] Descriptor sense data with sense descriptors (in hex):
[ 2498.380625]         72 03 11 04 00 00 00 0c 00 0a 80 00 00 00 00 00
[ 2498.380634]         00 00 00 00
[ 2498.380638] sd 3:0:0:0: [sde] Add. Sense: Unrecovered read error - auto reallocate failed
[ 2498.380642] sd 3:0:0:0: [sde] CDB: Read(10): 28 00 00 00 00 00 00 00 08 00
[ 2498.380650] end_request: I/O error, dev sde, sector 0
[ 2498.380654] Buffer I/O error on device sde, logical block 0
[ 2498.380666] ata4: EH complete
[ 2501.123454] ata4.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[ 2501.123457] ata4.00: BMDMA stat 0x24
[ 2501.123460] ata4.00: failed command: READ DMA
[ 2501.123466] ata4.00: cmd c8/00:08:00:00:00/00:00:00:00:00/e0 tag 0 dma 4096 in
[ 2501.123467]          res 51/40:00:00:00:00/00:00:00:00:00/e0 Emask 0x9 (media error)

```

The other ones i can open

```
root@egor:~# cryptsetup luksOpen /dev/sdb xpoolb
Enter passphrase for /dev/sdb:
Key slot 0 unlocked.
root@egor:~# cryptsetup luksOpen /dev/sdc xpoolc
Enter passphrase for /dev/sdc:
Key slot 0 unlocked.
root@egor:~# cryptsetup luksOpen /dev/sdd xpoold
Enter passphrase for /dev/sdd:
Key slot 0 unlocked.
root@egor:~# ls -ahl /dev/mapper/
total 0
drwxr-xr-x  2 root root     120 2020-04-25 11:53 .
drwxr-xr-x 18 root root    4.3K 2020-04-25 11:53 ..
crw-rw----  1 root root  10, 59 2020-04-25 11:41 control
brw-rw----  1 root disk 252,  0 2020-04-25 11:53 xpoolb
brw-rw----  1 root disk 252,  1 2020-04-25 11:53 xpoolc
brw-rw----  1 root disk 252,  2 2020-04-25 11:53 xpoold

```
ZFS on linux during that time was quite experimental

Starting the ZFS deamon ...
```
root@egor:~# zfs-fuse
root@egor:~#

```

And checking the pool status
```
root@egor:~# zpool status
  pool: vault
 state: UNAVAIL
status: One or more devices could not be opened.  There are insufficient
        replicas for the pool to continue functioning.
action: Attach the missing device and online it using 'zpool online'.
   see: http://www.sun.com/msg/ZFS-8000-3C
 scrub: none requested
config:


        NAME               STATE     READ WRITE CKSUM
        vault              UNAVAIL      0     0     0  insufficient replicas
          raidz1-0         UNAVAIL      0     0     0  insufficient replicas
            mapper/xpoolb  UNAVAIL      0     0     0  cannot open
            mapper/xpoolc  UNAVAIL      0     0     0  cannot open
            mapper/xpoold  UNAVAIL      0     0     0  cannot open
            mapper/xpoole  UNAVAIL      0     0     0  cannot open

```

I do not know why all devices are in the state unavailable. While only the xpoole (sde) is not mounted.

I tried some things but no luck.
```
root@egor:~# zpool online vault mapper/xpoolb
cannot open 'vault': pool is unavailable
root@egor:~# zpool import vault
cannot import 'vault': a pool with that name already exists
use the form 'zpool import <pool | id> <newpool>' to give it a new name
root@egor:~# zpool offline vault /dev/mapper/xpoolb /dev/mapper/xpoolc /dev/mapper/xpoold /dev/mapper/xpoole
cannot open 'vault': pool is unavailable


```

The solution was to first _**export**_ and then import again:

```
root@egor:~# zpool export vault
root@egor:~# zpool import vault
You have new mail in /var/mail/root
root@egor:~# zpool status
  pool: vault
 state: DEGRADED
status: One or more devices has experienced an error resulting in data
        corruption.  Applications may be affected.
action: Restore the file in question if possible.  Otherwise restore the
        entire pool from backup.
   see: http://www.sun.com/msg/ZFS-8000-8A
 scrub: none requested
config:


        NAME                           STATE     READ WRITE CKSUM
        vault                          DEGRADED     0     0     0
          raidz1-0                     DEGRADED     0     0     0
            disk/by-id/dm-name-xpoolb  ONLINE       0     0     0
            disk/by-id/dm-name-xpoolc  ONLINE       0     0     0
            disk/by-id/dm-name-xpoold  ONLINE       0     0     0
            2978311589468590032        UNAVAIL      0     0     0  was /dev/mapper/xpoole


errors: 6 data errors, use '-v' for a list
root@egor:~# cat /var/spool/mail/root
From root@egor  Sun May  5 11:33:47 2019
Return-Path: <root@egor>
X-Original-To: root
Delivered-To: root@egor
Received: by egor (Postfix, from userid 0)
        id 1E69025BE6; Sun,  5 May 2019 11:33:47 +0200 (CEST)
To: root@egor
Subject: vdev mapper/xpoole  is failing for pool vault
Message-Id: <20190505093347.1E69025BE6@egor>
Date: Sun,  5 May 2019 11:33:47 +0200 (CEST)
From: root@egor (root)


automatic mail generated by zfs_pool_alert

```

Degraded but i could recover my files !

---

### Post by CelticWarrior on 2020-04-25
Welcome.

Your system is missing **5 years** of security updates. No support should be given, other than tell you the obvious: Upgrade to a supported release.

---

### Post by DuckHook on 2020-04-25
> **CelticWarrior said:**
> Welcome.

Your system is missing **5 years** of security updates. No support should be given, other than tell you the obvious: Upgrade to a supported release.
My reading of the OP's thread is that s/he knows that his/her server is years past EoL. S/he is not advocating for operation of EoL releases. Rather, the thread was contributed as a possibly useful how-to that illustrates method for data recovery under such circumstances.

---

### Post by jaco-tech on 2020-04-25
> **DuckHook said:**
> My reading of the OP's thread is that s/he knows that his/her server is years past EoL. S/he is not advocating for operation of EoL releases. Rather, the thread was contributed as a possibly useful how-to that illustrates method for data recovery under such circumstances.

That was exactly what i intended. Perhaps someone will stumble upon it when searching.

Now that i have secured all data on the zfs volume, i have wiped and installed an up to date OS version.

Trying to upgrade before the recovery would have been a bigger risk. The box was behind NAT so no vulnerable services were directly accessible from the internet.

---

### Post by DuckHook on 2020-04-25
Thanks for your contribution jaco-tech. Hope to continue seeing you around the forums.

Good Luck and Happy Ubuntu-ing!

---

