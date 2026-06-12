---
title: "Create Multipe Partitions on a RAID Array"
date: 2019-12-31
forum: General Help
---

### Post by Markardi on 2019-12-31
I have created a RAID 1 using mdadm and would now like to make two partitions on that array.
When I go to format a partition, there is no option to choose the size of the partition, only the whole array.
Of the 4TB array, I would like to split it into a 1TB and 3TB partitions.
How do I go about doing that?  

Ubuntu 18.04 Desktop on a separate drive to the array.

Edit:  Had to install GParted to be able to choose partition size when formatting.

---

### Post by SeijiSensei on 2019-12-31
You could install [LVM]("https://wiki.ubuntu.com/Lvm") on top of the array and use that to create virtual partitions.

Otherwise, you can repartition the drives in the array, then create two arrays of 1 TB and 3 TB each. 

I don't believe you can partition an array, but others here might have better information.

---

### Post by Markardi on 2019-12-31
I will look into LVM as I have not used it before.
The end goal of the two partitions is to have them network shared; one for a backup location for windows 10 machines, the other for a plex media server.
Should I have any concerns with samba sharing virtual partitions?

I did have one array with two partitions when the system was running 14.04 and 16.04, but after a bad upgrade to 18.04, I'm redoing everything from scratch.
I don't recall having to do anything special, but it's been a while.

It makes more sense to me to have one mirrored array opposed to an array for each partition, but my understanding of how mdadm operates is limited.

---

### Post by Markardi on 2019-12-31
I remembered what I did!

I did not use the Disks utility that came with Ubuntu, but had to install GParted.
GParted allows you to choose the size while creating a partition.  My two partitions are now created.

I will still look LVM more as it does seem interesting.

Thanks!

---

### Post by TheFu on 2019-12-31
> **Markardi said:**
> I will look into LVM as I have not used it before.
The end goal of the two partitions is to have them network shared; one for a backup location for windows 10 machines, the other for a plex media server.
Should I have any concerns with samba sharing virtual partitions?

I did have one array with two partitions when the system was running 14.04 and 16.04, but after a bad upgrade to 18.04, I'm redoing everything from scratch.
I don't recall having to do anything special, but it's been a while.

It makes more sense to me to have one mirrored array opposed to an array for each partition, but my understanding of how mdadm operates is limited.

LVM is the easiest way.  In fact, I'd have LVM do the RAID1 mirroring too.  Under the covers, it uses the same code as mdadm.  Setup LVM on 1 of the disks ignoring the other completely, create a PV, then VG, then size each LV like you want.  The best practice is to keep the LV only the size you need for the next month or 3, since increasing the size is trivial.  Reducing the size because we made a mistake is a hassle.

Next, tell LVM about the other disk and tell it you want to mirror as RAID1.  Let it churn for a while, though the source disk is available while the mirroring happens.  You'll want to read the **lvcreate** manpage carefully to understand mirroring.  For example:```

              There are two implementations of mirroring which can be used and
              correspond  to  the  "raid1"  and  "mirror"  segment types.  The
              default is "raid1".  See the --type option for more  information
              if  you would like to use the legacy "mirror" segment type.  See
              lvm.conf(5)    settings     global/mirror_segtype_default    and
              global/raid10_segtype_default  to  configure default mirror segâ
              ment type.  The options --mirrorlog and --corelog apply  to  the
              legacy "mirror" segment type only.
``` so a few caveats are important to know.

With LVM, you get some other nice things like the ability to have real snapshots for perfectly quiesced backups.  There must be storage left available to hold the snapshots, so be certain you address that need BEFORE it is too late or too hard.

BTW, there is no good method to move from RAID1 to RAID10.  If you need to expand and want RAID10, that's a complete rebuild, though moving everything in a PV is pretty easy thanks to the **pvmove** command.

---

### Post by Markardi on 2020-01-01
Yes, the more I'm reading about LVM the more I understand the benefit.  Something definitely worth trying out.

Thanks for the tips!

---

