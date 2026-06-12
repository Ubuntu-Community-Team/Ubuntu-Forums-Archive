---
title: "Backup and Recover"
date: 2007-11-28
forum: General Help
---

### Post by lachild on 2007-11-28
Hello everyone,

Just a quick question.  I have to delete and reinstall windows - temporally- to install a bios patch.   Wine and VMWare will not work (I already tried) for this task.

So with that said, isn't it possible to tar up my root directory, save it, then reinstall and finally untar the backup to restore the system.

That should work shouldn't it?

---

### Post by ijason on 2007-11-28
you should check out Partimage. it lets you make full backups of partitions on a physical drive. i'm assuming ubuntu is in it's own partition? you probably need to download their system cd which is called "system rescue disk" because partimage will only backup unmounted drives.

i use it pretty regularly and it works great. partimage will make an image of the partition, and it only saves written data so it will be a good bit smaller than the partition on your drive.

i think you'll be able to find a link to download it on the forums if you search for 'partimage' and 'system rescue cd'. or, just google partimage and get it from their website. :)

---

### Post by lachild on 2007-11-29
Thanks.  That worked like a charm.:KS

---

### Post by bratliff on 2007-11-30
But Partimage will only back up to drive larger than the original. 

Bratliff



> **ijason said:**
> you should check out Partimage. it lets you make full backups of partitions on a physical drive. i'm assuming ubuntu is in it's own partition? you probably need to download their system cd which is called "system rescue disk" because partimage will only backup unmounted drives.

i use it pretty regularly and it works great. partimage will make an image of the partition, and it only saves written data so it will be a good bit smaller than the partition on your drive.

i think you'll be able to find a link to download it on the forums if you search for 'partimage' and 'system rescue cd'. or, just google partimage and get it from their website. :)

---

