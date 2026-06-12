---
title: "Is FAT32 worth it?"
date: 2007-06-19
forum: General Help
---

### Post by timo1023 on 2007-06-19
I have an external hard drive that I routinely store data on. Right now it is formatted as NTFS, but since I would like to make the switch to Ubuntu, I obviously need to change that. I would also like to be able to access the data through windows (I'm going to dual-boot). Is FAT32 decent enough for me to format the whole 250GB hard drive with it, or should I just format everything for Ubuntu and make the complete switch?

Thanks.

---

### Post by Impulse666 on 2007-06-19
FAT32 is accessible for both windows and ubuntu, so if you plan on keeping your windows installation at all and need the space, FAT32 is the best option. it is also good because if you need to move large amounts of data to another pc or a friends computer you dont have to reformat because no matter what OS they use FAT32 can be read and written to.

beware that formatting the drive will erase all data, so backup your data to another drive, format it FAT32, then move the data back.

---

### Post by kuja on 2007-06-19
FAT32 isn't really designed for drives that big, though it can be done. You'd really be better off formatting it with something else like NTFS or ext3 - seeing as with a little work you can make Linux read NTFS and Windows read ext3, take your pick.

---

### Post by Bachstelze on 2007-06-19
No. FAT32 is old and ugly, there's absolutelyt no reason to use it anymore, except on Flash drives (and even on those, I usually recomment ext2 instead).

---

### Post by LaRoza on 2007-06-19
Also be aware that FAT32 has a 4 gig file size limit. That shouldn't be a problem unless you are saving DVD iso's and such.

---

### Post by timo1023 on 2007-06-19
It's already NTFS, and Ubuntu automatically mounts it, so accessing the data isn't the problem. I would just lke to be able to r/w from both OS's. I'd heard bad things about FAT32 beforehand, so I was just checking. I'll probably end up formatting it to ext3.

---

### Post by vexorian on 2007-06-19
you can try the ntfs-conf  package if you want to write to partitions.

But what I used for communication between my OSes is a 1GB fat32 partition, it is enough, Just resize some partition like when you installed ubuntu and reformat the new space as fat32, windows will add it as a new unit to "my computer" and Ubuntu is probably going to find it as well, else you just need to edit fstab.

Although a flash disk is actually great at that as well.

---

### Post by timo1023 on 2007-06-19
After a bit of research, I've discovered that windows can write to ext3. Is this safe? I've also heard of Linux writing to NTFS, but I heard bad thigns about it so I never tried. Is it safe? That would be wonderful if it was.

EDIT:
Looks like 7.04 can write to NTFS
[https://help.ubuntu.com/community/MountingWindowsPartitions](https://help.ubuntu.com/community/MountingWindowsPartitions)
Is this recommended?

---

### Post by Irony on 2007-06-19
Partition it into several bits, do some as Fat32 some as ext3.

---

### Post by merlinus on 2007-06-19
Why bother with FAT32 for anything, even windows?  It wastes space because of the cluster allotments, and gets fragmented just by sneezing.

ntfs-3g will let you read and write from ext3 to ntfs, and ifs will let you go the other way round.

I have not had any problems with either.

-merlin

---

### Post by Yoooder on 2007-06-19
If you want a straight-forward plug and play filesystem, FAT32 will work (but really is a terrible filesystem).  ntfs-3g is good if you want to read/write NTFS from Linux--but I don't have too much trust in it (although this is just due to lack of use, don't take my word for it!).  

If you don't mind installing some apps on the windows host then look at ext2, ext3, or reiserfs.   
Ext2fsd is a windows app that will let you read/write ext2 filesystems, rfstools will let you read/write a ReiserFS filesystem, and LTools is a more generic app that supports ext2/ext3/reiser... all are pretty good options

---

