---
title: "Running out of disk space on root drive..how to resolve?"
date: 2007-07-28
forum: General Help
---

### Post by padmanabh on 2007-07-28
I am running out of disk space on root partition which basically has all the dirs mounted on it except home dirs of all users.

As far as i know all the system software and downloaded upgrade files will add to this partition which is running out of space. I have 2 other ext3 partitions which have lot of space on them.

How do i use these partitions for system files and stuff so that I don't run out of space on the root partition?

I cannot resize the root partition because the drive(out of the 2 i have) which contains the partition already contains 4 primary partitions. So I cannot (rather i prefer not to) edit any partitions there.

Any suggestions?

---

### Post by rillip on 2007-07-28
You might check out something like kdirstat and see where the space is at.  You could just have a lot of logs or such that you can clear.  Try checking /var/log and /var/cache in particular.  Other than this, what do you have in your home dir?  Mounting that to a new partition is typically trvial, but I do not know how you would get anything to install to a different partition.  You should be able to mount your var folder somewhere else too, if it has enough space to make it useful to do so.

Kind of need to know where the bulk of the space is to make suggestions worth while

---

### Post by padmanabh on 2007-07-29
this is what fdisk gives me:

```
   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63    40965749    20482843+   7  HPFS/NTFS
/dev/sda2        40965750   128937689    43985970    f  W95 Ext'd (LBA)
/dev/sda3       128937690   156296384    13679347+  a5  FreeBSD
/dev/sda4       156296385   488392064   166047840   83  Linux
/dev/sda5   *    40965813    77834924    18434556    7  HPFS/NTFS
/dev/sda6   *    77834988   116744354    19454683+   7  HPFS/NTFS
/dev/sda7   *   116744418   118704284      979933+  82  Linux swap / Solaris
/dev/sda8   *   118704348   128937689     5116671   83  Linux
```

the last partition.../dev/sda8 is the one which has / mounted on it....which is causing problems.
the largest partition /dev/sda4 has the /home mounted on it.

gaprted is still showing only 95% disk usage for / partition and says 250 MB is still left unused.

Apart from this i also have another Drive which has one more 40 Gb Linux partition on it.

Now...what do i do?

---

### Post by padmanabh on 2007-07-29
basically i need to know where the installation files are stored...so that i can mount that to a drive that has more space...

---

### Post by dando80 on 2007-07-30
What is the current usage on your /usr and /var directories and what is the size of the new partition you want to utilize?

---

### Post by padmanabh on 2007-08-04
aargh..now it seems i've hit the absoulte low....i cannot even login to the system...it says cannot write to some log file...and drops back to the GDM login screen....NOW what r my options?

---

### Post by rillip on 2007-08-06
Boot into the recovery mode.  Ext3 reserves room for root so that you can avoid this kind of situation.  But you'll have to find SOMETHING to delete.

---

