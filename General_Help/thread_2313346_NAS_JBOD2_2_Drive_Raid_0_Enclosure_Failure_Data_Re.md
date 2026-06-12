---
title: "NAS JBOD2 2 Drive Raid 0 Enclosure Failure Data Recovery"
date: 2016-02-11
forum: General Help
---

### Post by trinsic1 on 2016-02-11
I have a Caldigit Enclosure that had 2 2TB Sata Hard Drives in the unit. The Enclosure seems to have failed during a data recovery operation where the partition was lost during a power failure.  I am now at the point of trying to recover this data by other means, I was wondering if there was a way to mount these two drives on a ubuntu platform using the sata interface so I can either try to restore the partition or recover the data. The information on the drive characteristics is below:        

```
*-disk:0
       description: SCSI Disk
       physical id: 0.0.0
       bus info: scsi@8:0.0.0
       logical name: /dev/sdg
       size: 1863GiB (2TB)
       capabilities: partitioned partitioned:dos
       configuration: sectorsize=512
  *-disk:1
       description: SCSI Disk
       physical id: 0.0.1
       bus info: scsi@8:0.0.1
       logical name: /dev/sdh
       size: 1863GiB (2TB)
       configuration: sectorsize=512
root@bench:/home/trinsic# 
root@bench:/home/trinsic# mdadm --misc --examine /dev/sdh
mdadm: No md superblock detected on /dev/sdh.
root@bench:/home/trinsic# mdadm --misc --examine /dev/sdg
/dev/sdg:
   MBR Magic : aa55
Partition[0] :   4294967295 sectors at            1 (type ee)
```

---

### Post by trinsic1 on 2016-02-12
just trying to get a response on this, have a failed to include further information?

---

### Post by trinsic1 on 2016-02-13
Im back to try to get another response on this. There has got to be a way to assemble this array.

---

