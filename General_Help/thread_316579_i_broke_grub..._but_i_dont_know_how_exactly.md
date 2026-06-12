---
title: "i broke grub... but i dont know how exactly"
date: 2006-12-11
forum: General Help
---

### Post by Darth_tater on 2006-12-11
i was in windows (office 07 is like a drug, cant live w/o it)and i needed access to my Ubuntu partition.  To do this, i have been using the Ex2FSdriver... i don't remember exactly what i was doing, but i switched the partition type to NTFS or something similar and later rebooted.  Grub loaded to stage 1.5 then gave me a Error 17 message

when i try to reinstall, i do the following
find /grub/boot/state1

i get an error, something about file not found (IIRC, ill post back ASAP w/ accurate info)

then 
root <the location found above... had0,5 IIRC>

then setup (hd0)
that gives me an error as well (i cant remember what it is...)
something about an unknown partition type.

Ill post back with updated error  messages ASAP, but in the meantime, can you offer any advice/help?

THANKS!!!!

Edit: i am posting this in windows ( i was able to run "fixmbr" from the Windows recovery console... that got me access to vista/xp)

---

### Post by Bigbluecat on 2006-12-11
I don't know if this is your problem but grub cannot read NTFS file systems.

So if you switched the partition to NTFS and then try to use the grub command line to "find" it won't work.

This is not to say that the file you are trying to find is missing - it is just that grub cannot read the file system.

---

### Post by Darth_tater on 2006-12-11
i do believe thats what happened.. how do i fix it?

edit: i have had a little time to Google around... is there anyway to fix this W/o reformatting?

edit2 :  ok.  i think i figured it out.  in order to have fully automatic mounting (mounted at boot time) in windows, the mount manager assignees UID's to the recognized partitions.  EXT3 isint one of those recognized partitions.  to circumvent this.... well, hers a quote from the FAQ


> Q) What's a permanent mount point ?

A) Windows system's mount manager will automatically mount volumes and
   assign driver letters during booting. For xp and later systems, windows
   only create unique volume ids for all the recognized volume/partitions,
   such as FAT32, NTFS. The ext2/ext3 volumes could not be mounted by the
   windows mount manager.

   In this case, you can not select the "permanent mount point ..." or it
   will fails, so the drive letter you assigned will lose after rebooting.

   The "Ext2 Volume Manager" uses a workaround to change the partition table
   to assign the linux partition as the type of NTFS (0x07). Then mount
   manager could take over the linux partition.



so, my partition table says that my main ubuntu partition is ntfs.  this is not so.  how can i revert this?

---

### Post by Darth_tater on 2006-12-11
WOooo Hooo

im posting this from with in my ubuntu installation!  
i had to get a windows proggie that can scan the partitions and the partition table and fix the inconstancies.

IIRC it was called the partition doctor, then i had to reinstall grub and it finally worked!!!

---

