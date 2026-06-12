---
title: "File recovery from drives out of RAID1 Buffalo NAS"
date: 2014-08-13
forum: General Help
---

### Post by JugeHuge on 2014-08-13
Hi there,

My Buffalo NAS failed drives. Both drivers work somehow and i have hooked those on my Ubuntu linux PC.
I found couple threads on same issue but those were closed and there were no actual answer on those.

I have found out that MDADM can be used to enable mounting those drives.
I runned mdadm --assemble --scan when i had only one drive connected and now when i connect the second drive that command doesn't found the another drive.
I can access data from the first drive but it's damaged so that when it tries to read bad sector it just hangs so i'm hoping that another drive is bit more lively.

So what would be the correct way to use mdadm to make both md devices and then mount them.
I just want to be sure that i won't kill those drives and lost the data as it's accessible and i have partially saved some from the other.

Thanks.

**edit1:**
this is what i get when running examine command. 

sudo mdadm --examine /dev/sda
/dev/sda:
   MBR Magic : aa55
Partition[0] :      2008062 sectors at           63 (type 83)
Partition[1] :     10008495 sectors at      2008125 (type 83)
Partition[3] :   2918255445 sectors at     12016620 (type 05)

sudo mdadm --examine /dev/sdb
mdadm: No md superblock detected on /dev/sdb.

i just would need to get sdb partition3 mounted to get files out from there.

**edit2:** examining sda6 gives following informaton

sudo mdadm --examine /dev/sda6

```

/dev/sda6:
          Magic : a92b4efc
        Version : 0.90.00
           UUID : bb0c81ff:e86a8053:534c82c6:5ebaf3ec
  Creation Time : Sat Apr  3 12:37:09 2010
     Raid Level : raid1
  Used Dev Size : 1457039168 (1389.54 GiB 1492.01 GB)
     Array Size : 1457039168 (1389.54 GiB 1492.01 GB)
   Raid Devices : 2
  Total Devices : 2
Preferred Minor : 127

    Update Time : Wed Aug 13 17:32:33 2014
          State : clean
 Active Devices : 1
Working Devices : 1
 Failed Devices : 0
  Spare Devices : 0
       Checksum : f66d8887 - correct
         Events : 10766947


      Number   Major   Minor   RaidDevice State
this     1       8        6        1      active sync   /dev/sda6

   0     0       0        0        0      removed
   1     1       8        6        1      active sync   /dev/sda6

```

---

### Post by JugeHuge on 2014-08-15
Ok, I managed to copy almost all files from the working disk. There is some files which the harddrive can not read and after that hd goes on vegetative state.

My question is that as my drives were in RAID1 so can i copy somehow /dev/sda6 superblock to /dev/sdb6?? so i could mount it and check those missing files??

There is also guide to re-create array which should leave files intact but there is always risk for loosing them.

---

### Post by JugeHuge on 2014-08-18
Okey, as no help is coming i went re-create array path.
Problem is sync. Is it possible to create array so that it doesn't start syncing them?? 
As one of the disk is so nicely damaged that when it hit that damaged part of the disk. It will kill itself and only way to recover is power off.

---

### Post by JugeHuge on 2014-08-19
So re-create array was a mistake as disk from which it tried to sync was damaged so it left another disk in partially state.
Now my final question is that is there any application which could possibly look data from that one partition or did the sync removed partition information totally so nothing can be removed??

---

