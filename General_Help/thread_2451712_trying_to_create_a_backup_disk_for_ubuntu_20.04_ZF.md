---
title: "trying to create a backup disk for ubuntu 20.04 ZFS"
date: 2020-10-09
forum: General Help
---

### Post by darksidedude on 2020-10-09
Hello all,

I heard about a cool ZFS tool called Send/Recieve,

it got me thinking (which in most cases gets me into trouble :rolleyes:  )

ZFS rollback with zsys works well but what if the whole drive goes poof? I would like to replicate the bpool/rpool onto a usb drive

I created a new pool with 
```
sudo zfs create new-backup /dev/sdf 
```
next I mounted the pool
```
# zfs set mountpoint=/mnt/zfs new-backup 
```

and then verified the status that I didn't break/make a mistake 
```
  # zpool list
NAME         SIZE  ALLOC   FREE  CKPOINT  EXPANDSZ   FRAG    CAP  DEDUP    HEALTH  ALTROOT
bpool       1.88G   539M  1.35G        -         -     1%    28%  1.00x    ONLINE  -
new-backup   696G   552K   696G        -         -     0%     0%  1.00x    ONLINE  -
rpool        440G   329G   111G        -         -    25%    74%  1.00x    ONLINE  -
root@ubuntu-desktop:/mnt# zpool status
  pool: bpool
 state: ONLINE
  scan: none requested
config:

	NAME                                    STATE     READ WRITE CKSUM
	bpool                                   ONLINE       0     0     0
	  8c34816e-5ec4-5448-ade1-94f4c11491c4  ONLINE       0     0     0

errors: No known data errors

  pool: new-backup
 state: ONLINE
  scan: none requested
config:

	NAME        STATE     READ WRITE CKSUM
	new-backup  ONLINE       0     0     0
	  sde       ONLINE       0     0     0

errors: No known data errors

  pool: rpool
 state: ONLINE
  scan: none requested
config:

	NAME                                    STATE     READ WRITE CKSUM
	rpool                                   ONLINE       0     0     0
	  cb1e7a65-821f-654a-8dbb-413b523766d2  ONLINE       0     0     0

errors: No known data errors
           
```

then I started to look for how to do zfs send/recieve to create the backup....

and I started to see a bit of info pertaining to Solaris and other OS's but not about Ubuntu, at this point I stopped because I don't want to break anything :lolflag:

if anyone has advice I would appreciate it. or should I just use Timeshift Rsync backup? 

thanks again,

---

### Post by Tadaen_Sylvermane on 2020-10-09
Any backup method will do. 

You do realize that a single drive with zfs has zero redundancy. Other than cow and deduplication it's no different than any other single drive system.

---

### Post by darksidedude on 2020-10-11
I was hoping for guidance on how to use ZFS Send/Recieve to make a hot spare backup,

---

### Post by darksidedude on 2020-10-12
So i did further research on my day off from work and discovered the ZFS attach command as featured here:

[HTML] https://docs.oracle.com/cd/E19253-01/819-5461/6n7ht6qvl/index.html[/HTML]

the attach command allows for a non redundant ZFS pool to become a mirrored pair.

this is now my zpool status 

```
    linux4life@ubuntu-desktop:~$ zpool status
  pool: bpool
 state: ONLINE
  scan: resilvered 543M in 0 days 00:00:17 with 0 errors on Mon Oct 12 02:39:34 2020
config:

	NAME                                      STATE     READ WRITE CKSUM
	bpool                                     ONLINE       0     0     0
	  mirror-0                                ONLINE       0     0     0
	    8c34816e-5ec4-5448-ade1-94f4c11491c4  ONLINE       0     0     0
	    sde1                                  ONLINE       0     0     0

errors: No known data errors

  pool: rpool
 state: ONLINE
  scan: resilvered 335G in 0 days 03:42:10 with 0 errors on Mon Oct 12 06:23:26 2020
config:

	NAME                                      STATE     READ WRITE CKSUM
	rpool                                     ONLINE       0     0     0
	  mirror-0                                ONLINE       0     0     0
	    cb1e7a65-821f-654a-8dbb-413b523766d2  ONLINE       0     0     0
	    sde2                                  ONLINE       0     0     0

errors: No known data errors
          
```

I tested to make sure it does boot from the resilvered backup disk and it does. so I hope this might happen to help someone in the future who doesn't exactly trust their main boot drive, 

cheers.

---

### Post by dad+sithlord on 2020-12-29
> I was hoping for guidance on how to use ZFS Send/Recieve to make a hot spare backup,

The oracle documents on ZFS should work with Ubuntu - as far as ZFS goes:
[https://docs.oracle.com/cd/E18752_01/html/819-5461/gbchx.html](https://docs.oracle.com/cd/E18752_01/html/819-5461/gbchx.html)

To send a snapshot from one pool to another on the same system (from above link):
 [B]zfs send tank/data@snap1 | zfs recv spool/ds01

[/B]To send a snapshot from one pool to another on a different system:

[B][B]zfs send tank/dana@snap1 | ssh host2 zfs recv newtank/dana

[/B][/B]To send an **incremental** snapshot from one pool to another on a different system:[B][B]

**zfs send -i tank/dana@snap1 tank/dana@snap2 | ssh host2 zfs recv newtank/dana**

You can also just compress the data stream into a really big file(s) and restore that later.


[/B][/B]

---

