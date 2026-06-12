---
title: "Zfs 'replacing' vdev failed after resilver. Cannot detach?"
date: 2013-09-22
forum: General Help
---

### Post by Zfs on 2013-09-22
My one zpool has experienced two successive drive failures. As I was resilvering the first, the second failed and I got two errors, in snapshots. The resilvering finished, and then I used "zpool replace" to resilver the second faulty drive.


The pool is mounted, all data safe and available except for the two files:


pool: gggpool
state: DEGRADED
status: One or more devices has experienced an error resulting in data corruption.
        Applications may be affected.
scan: resilvered 2,35T in 19h29m with 5 errors on Sat Sep 21 03:08:24 2013 


config:


NAME                                             STATE     READ WRITE CKSUM
gggpool                                          DEGRADED     0     0     5
  raidz1-0                                       DEGRADED     0     0    10
    scsi-SATA_ST3000DM001-9YN_Z1F0NJKS           ONLINE       0     0     0
    scsi-SATA_ST3000DM001-9YN_Z1F0RPKE           ONLINE       0     0     0
    scsi-SATA_ST3000DM001-9YN_Z1F0RPZG           ONLINE       0     0     0
    scsi-SATA_ST3000DM001-9YN_Z1F0RQJ2           ONLINE       0     0     0
    scsi-SATA_ST3000DM001-9YN_Z1F0RQSV           ONLINE       0     0     0
    scsi-SATA_ST3000DM001-9YN_Z1F0T6VN           ONLINE       0     0     0
    spare-6                                      DEGRADED     0     0     0
      scsi-SATA_WDC_WD30EZRX-00_WD-WMC1T4095404  UNAVAIL      0     0     0
      scsi-SATA_ST3000DM001-9YN_Z1F118BA         ONLINE       0     0     0
    replacing-7                                  UNAVAIL      0     0     0
      scsi-SATA_ST3000DM001-1CH_Z1F2Z9VC         UNAVAIL      0     0     0
      scsi-SATA_ST3000DM001-1CH_Z1F2Z8SM         ONLINE       0     0     0
spares
  scsi-SATA_ST3000DM001-9YN_Z1F118BA             INUSE     currently in use


The remaining errors probably point to where the faulty files were - I destroyed the relevant snapshots but these error indications remain:


errors: Permanent errors have been detected in the following files:


    <0x218>:<0x7308>
    <0x3a0>:<0x295a6b>
I am not worried about these errors. I am trying to detach the two failed drives, both of which has been replaced, but zpool doesn't do it:


root@ggg:~# zpool detach gggpool scsi-SATA_ST3000DM001-1CH_Z1F2Z9VC
cannot detach scsi-SATA_ST3000DM001-1CH_Z1F2Z9VC: no valid replicas


root@ggg:~# zpool detach gggpool scsi-SATA_WDC_WD30EZRX-00_WD-WMC1T4095404
cannot detach scsi-SATA_WDC_WD30EZRX-00_WD-WMC1T4095404: no valid replicas


The two drives have been physically removed from the array - sent in for warranty replacement - but they live on in the zpool configuration. How do I get rid of them?


When reading data from the pool, I can see the "replacing-7" vdev is not active:


                                                    capacity     operations    bandwidth
pool                                             alloc   free   read  write   read  write
-----------------------------------------------  -----  -----  -----  -----  -----  -----
gggpool                                          19,8T  1,96T    323      0  36,8M      0
  raidz1                                         19,8T  1,96T    323      0  36,8M      0
    scsi-SATA_ST3000DM001-9YN_Z1F0NJKS               -      -    177      0  5,42M      0
    scsi-SATA_ST3000DM001-9YN_Z1F0RPKE               -      -    184      0  5,26M      0
    scsi-SATA_ST3000DM001-9YN_Z1F0RPZG               -      -    183      0  5,55M      0
    scsi-SATA_ST3000DM001-9YN_Z1F0RQJ2               -      -    183      0  5,25M      0
    scsi-SATA_ST3000DM001-9YN_Z1F0RQSV               -      -    180      0  5,39M      0
    scsi-SATA_ST3000DM001-9YN_Z1F0T6VN               -      -    181      0  5,21M      0
    spare                                            -      -    298      0  5,47M      0
      scsi-SATA_WDC_WD30EZRX-00_WD-WMC1T4095404      -      -      0      0      0      0
      scsi-SATA_ST3000DM001-9YN_Z1F118BA             -      -    230      0  5,49M      0    
    replacing                                        -      -      0      0      0      0
      scsi-SATA_ST3000DM001-1CH_Z1F2Z9VC             -      -      0      0      0      0
      scsi-SATA_ST3000DM001-1CH_Z1F2Z8SM             -      -      0      0      0      0
-----------------------------------------------  -----  -----  -----  -----  -----  -----
This is worrying because without this VDEV working, the pool has no redundancy - yet I cannot remove or detach any of its two drives. I am in the process of making a full backup - only a day to go. However, destroying this pool and rebuilding it will cause a LOT of headaches, with many filesystems and smb and afs shared having to be re-set up.


And ideas how I can force this failed replacing-7 vdev to work again?

---

### Post by tgalati4 on 2013-09-22
No idea, but you have demonstrated an issue with ZFS and with RAID pools in general.  Because it takes so long to rebuild them (because they are holding large datasets), any disruption in the rebuild process leaves you in an indeterminate state. RAID10 is supposed to protect against this type of failure, but I don't think ZFS has protection in this failure scenario.  My only ZFS pool is running on a freenas system, which is then backed up to a RAID mirror--for just this scenario.

Out of curiosity, did the two files suffer data corruption (silent bit rot) and then the hard disk failed which triggered the resilvering and then the second drive failed during this resilvering?

Perhaps you can simply "expand" your existing zpool with the new disks and just ignore the disabled devices.  Sometimes you have to let the system win.

[http://jsosic.wordpress.com/2013/01/01/expanding-zfs-zpool-raid/](http://jsosic.wordpress.com/2013/01/01/expanding-zfs-zpool-raid/)

---

### Post by Zfs on 2013-09-23
> **tgalati4 said:**
> No idea, but you have demonstrated an issue with ZFS and with RAID pools in general.  Because it takes so long to rebuild them (because they are holding large datasets), any disruption in the rebuild process leaves you in an indeterminate state. RAID10 is supposed to protect against this type of failure, but I don't think ZFS has protection in this failure scenario.

Zfs did everything it was supposed to. I have 19.8tb in this pool, with only raidz1 protection.  I had two successive drive failures, as explained. If I had raidz2 i would have had no problem. I do have a backup on another server, but going over to the backup is a huge job.  

As it stands, the pool is working but has no redundancy and after two failures this is worrying. I need to get the last vdev working again. Expanding the pool like in your link will not solve the redundancy issue. 

I need to somehow make the pool detach the working but unused drive from "replacing-7", but detach fails.

Update:


I am running a scrub on this pool and hope that the scrub will make the "replacing-7" and "spare-6" vdevs work again.  


      pool: gggpool
     state: DEGRADED
    status: One or more devices has experienced an error resulting in data
	corruption.  Applications may be affected.
    action: Restore the file in question if possible.  Otherwise restore the
	entire pool from backup.
       see: [http://zfsonlinux.org/msg/ZFS-8000-8A](http://zfsonlinux.org/msg/ZFS-8000-8A)
      scan: scrub in progress since Mon Sep 23 09:02:34 2013
        825G scanned out of 19,8T at 403M/s, 13h44m to go
        0 repaired, 4,07% done
    config:
    
    	NAME                                             STATE     READ WRITE CKSUM
    	gggpool                                       DEGRADED     0     0     5
    	  raidz1-0                                       DEGRADED     0     0    10
    	    scsi-SATA_ST3000DM001-9YN_Z1F0NJKS           ONLINE       0     0     0
    	    scsi-SATA_ST3000DM001-9YN_Z1F0RPKE           ONLINE       0     0     0
    	    scsi-SATA_ST3000DM001-9YN_Z1F0RPZG           ONLINE       0     0     0
    	    scsi-SATA_ST3000DM001-9YN_Z1F0RQJ2           ONLINE       0     0     0
    	    scsi-SATA_ST3000DM001-9YN_Z1F0RQSV           ONLINE       0     0     0
    	    scsi-SATA_ST3000DM001-9YN_Z1F0T6VN           ONLINE       0     0     0
    	    spare-6                                      DEGRADED     0     0     0
    	      scsi-SATA_WDC_WD30EZRX-00_WD-WMC1T4095404  UNAVAIL      0     0     0
    	      scsi-SATA_ST3000DM001-9YN_Z1F118BA         ONLINE       0     0     0
    	    replacing-7                                  DEGRADED     0     0     0
    	      scsi-SATA_ST3000DM001-1CH_Z1F2Z9VC         UNAVAIL      0     0     0
    	      scsi-SATA_ST3000DM001-1CH_Z1F2Z8SM         ONLINE       0     0     0
    	spares
    	  scsi-SATA_ST3000DM001-9YN_Z1F118BA             INUSE     currently in use
    
     errors: 2 data errors, use '-v' for a list


Strange thing:  When scrubbing, it is reading and writing to/from the active disk in "replacing-7" (see below), while rsync reading from the same pool reads nothing from "replacing-7" (as shown in the original post above).


    SCRUBBING at 551MB/sec!!!:
    gggpool                                       19,8T  1,96T  4,38K     26   551M  68,7K
      raidz1                                         19,8T  1,96T  4,38K     26   551M  68,7K
        scsi-SATA_ST3000DM001-9YN_Z1F0NJKS               -      -  3,16K      5  83,3M  34,4K
        scsi-SATA_ST3000DM001-9YN_Z1F0RPKE               -      -  3,18K      4  80,3M  30,4K
        scsi-SATA_ST3000DM001-9YN_Z1F0RPZG               -      -  3,09K      5  83,5M  32,8K
        scsi-SATA_ST3000DM001-9YN_Z1F0RQJ2               -      -  3,30K      5  79,8M  29,6K
        scsi-SATA_ST3000DM001-9YN_Z1F0RQSV               -      -  2,59K      5  83,8M  32,8K
        scsi-SATA_ST3000DM001-9YN_Z1F0T6VN               -      -  2,95K      5  80,5M  30,4K
        spare                                            -      -  4,32K      7  81,7M  29,6K
          scsi-SATA_WDC_WD30EZRX-00_WD-WMC1T4095404      -      -      0      0      0      0
          scsi-SATA_ST3000DM001-9YN_Z1F118BA             -      -  2,98K      5  82,8M  32,8K
        replacing                                        -      -  4,32K      7  77,5M  29,6K
          scsi-SATA_ST3000DM001-1CH_Z1F2Z9VC             -      -      0      0      0      0
          scsi-SATA_ST3000DM001-1CH_Z1F2Z8SM             -      -  3,35K      5  79,1M  29,6K
    -----------------------------------------------  -----  -----  -----  -----  -----  -----

---

### Post by tgalati4 on 2013-09-23
I was going to recommend a scrub, but with your pool in an indeterminate state, it may do some damage.

Not your type of pool, but interesting reading regardless:  [https://blogs.oracle.com/partnertech/entry/a_hands_on_introduction_to1](https://blogs.oracle.com/partnertech/entry/a_hands_on_introduction_to1)

Some other zfs resources:  [http://pthree.org/2012/12/11/zfs-administration-part-vi-scrub-and-resilver/](http://pthree.org/2012/12/11/zfs-administration-part-vi-scrub-and-resilver/)

[http://forums.freebsd.org/showthread.php?t=28084](http://forums.freebsd.org/showthread.php?t=28084)

Bottomline:  scrub while you have redundancy.  It doesn't help in your situation, but perhaps the scrub will allow you to detach the "bad" drive.

---

### Post by Zfs on 2013-09-23
[COLOR=#000000][FONT=monospace]scan: scrub in progress since Mon Sep 23 09:02:34 2013[/FONT][/COLOR]
[COLOR=#000000][FONT=monospace]    14,0T scanned out of 19,8T at 437M/s, 3h53m to go[/FONT][/COLOR]
[COLOR=#000000][FONT=monospace]    0 repaired, 70,52% done[/FONT][/COLOR]

---

### Post by Zfs on 2013-09-24
The scrub finished with no change.  Both 'spare-6' and 'replacing-7' were still degraded.  Error count dropped to 1, in another snapshot which I subsequently destroyed.

- still not able to detach the UNAVAIL drives.
- tried something new - try to "online" one of the drives that is listed as "online" in the degraded vdev:

zpool online gggpool [COLOR=#000000][FONT=monospace]scsi-SATA_ST3000DM001-9YN_Z1F118BA[/FONT][/COLOR]

And the pool started resilvering both online drives????

[COLOR=#000000][FONT=monospace]  scan: resilver in progress since Mon Sep 23 23:31:42 2013[/FONT][/COLOR]
[COLOR=#000000][FONT=monospace]    15,2T scanned out of 19,8T at 410M/s, 3h16m to go[/FONT][/COLOR]
[COLOR=#000000][FONT=monospace]    9,31G resilvered, 76,73% done
[/FONT][/COLOR]              ....
[COLOR=#000000][FONT=monospace]            spare-6                                      DEGRADED     0     0     0[/FONT][/COLOR]
[COLOR=#000000][FONT=monospace]              scsi-SATA_WDC_WD30EZRX-00_WD-WMC1T4095404  UNAVAIL      0     0     0[/FONT][/COLOR]
[COLOR=#000000][FONT=monospace]              scsi-SATA_ST3000DM001-9YN_Z1F118BA         ONLINE       0     0     0  (resilvering)[/FONT][/COLOR]
[COLOR=#000000][FONT=monospace]            replacing-7                                  DEGRADED     0     0     0[/FONT][/COLOR]
[COLOR=#000000][FONT=monospace]              scsi-SATA_ST3000DM001-1CH_Z1F2Z9VC         UNAVAIL      0     0     0[/FONT][/COLOR]
[COLOR=#000000][FONT=monospace]              scsi-SATA_ST3000DM001-1CH_Z1F2Z8SM         ONLINE       0     0     0  (resilvering)[/FONT][/COLOR]

---

### Post by tgalati4 on 2013-09-24
All you can do is wait.  ZFS is a giant, mysterious, black box.

---

### Post by Zfs on 2013-09-24
Resilver once again did not online the drives.  Once again I could not detach.  It must be something to do with the remaining errors on the pool.  So I deleted ALL the relevant snapshots where the errors were, and now the same resilver is running again, but it is indicating no errors.  Hopefully it will bring the disks online when done with no errors.

---

### Post by Zfs on 2013-09-25
SOLVED

Steps:
1. **Delete all the snapshots containing the errors**
2. zpool online gggpool [the drive in 'spare' or 'rebuilding' that says online but is not really online]
- this starts a resilver process on all vdevs that needs to resilver.
3. Wait for resilvering to finish
4. Vdevs all indicate "online" in stead of "degraded"
5. zpool detach gggpool [unavailable drive]

All pools healthy.

---

