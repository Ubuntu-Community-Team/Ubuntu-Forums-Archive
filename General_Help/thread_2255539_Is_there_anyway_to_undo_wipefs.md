---
title: "Is there anyway to undo wipefs?"
date: 2014-12-05
forum: General Help
---

### Post by jason152 on 2014-12-05
So I (very stupidly) performed a wipefs on my XFS formated 4tb linux (software) raid 5 array in trying to convert over to a bcache setup (I was following some instructions online and should have payed more attention to what wipefs does...). Is there anyway to recover the filesystem without deleting all the data? If the filesystem is unrecoverable what are my options for recovering the data so I can format the drives? If I have to I could buy more disks to copy the data over to a new array, its not financially ideal but I guess its the price I pay for my stupidity.

Thanks

---

### Post by coldcritter64 on 2014-12-05
I am just looking at an online man pages for wipefs. 
> Description
wipefs allows to erase filesystem or raid signatures (magic strings) from the device to make the filesystem invisible for libblkid. **wipefs does not erase the whole filesystem or any other data from the device.** When used without options -a or -o, it lists all visible filesystems and offsets of their signatures. Source : [http://linux.die.net/man/8/wipefs](http://linux.die.net/man/8/wipefs)

That bolded bit sounds like your data may still be on the drive and may possibly be recoverable with testdisk.
Testdisk is in the ubuntu repositories. 
An online guide for its use is [[COLOR=#0000ff]--here--[/COLOR]]("http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step").
I have never used testdisk for such an array, you may need to research it further before any recovery attempt, to mainly check if it is likely to be usable in your circumstances. I have used it to recover a whole large multi partitioned drive which had the MBR including partition tables overwritten rendering it invisible to the blkid command and thus gparted as well. 
A RAID array recovery is likely to be a bit more involved than my situation was. Good luck with the data recovery work, hope testdisk works for you.

Edit: I just spotted "XFS formated" on re-reading the opening post. A quick look at the testdisk guide **doesn't** mention XFS support. 
Await further advice from other helpers with more experience using testdisk before any actual recovery attempt for your data's safety.

---

### Post by jason152 on 2014-12-05
It turns out an xfs_repair is all I needed, it just took a long time since the drives are so large, wipefs doesn't delete the secondary superblocks so xfs is able to recover itself

---

### Post by coldcritter64 on 2014-12-05
> wipefs doesn't delete the secondary superblocks so xfs is able to recover itself                  That is fantastic news. 
Could you mark the thread as [SOLVED] please ? The last link in my sig line has a guide on how to if needed. Cheers.

---

