---
title: "Advice on converting a large NTFS partition"
date: 2006-12-15
forum: General Help
---

### Post by chombee on 2006-12-15
A friend of mine recently replaced Windows with Ubuntu. He has a 200GB external hard drive that appeared to work fine on Ubuntu -- plug it in and a folder opens up. But it transpires that the disk has a 200GB NTFS filesystem on it, so he can read it but can't write to it.

He has about 90GB of data on the drive, all of which he wants to keep.

What is the easiest way to make this thing Linux-compatible?

It seems to me that we need to get a new filesystem on there. The smartest thing to do would be to make a FAT32 because then both Windows and Ubuntu can read and write to it and he won't have any problems. I think FAT32 can expand to 200GB, right?

My best plan is to use Ubuntu to resize the NTFS partition to 100GB, then make a new 100GB FAT32 partition in the free space, then copy all the files from the NTFS partition over to the FAT32 partition, then delete the NTFS partition, then expand the FAT32 partition to 200GB. Is this possible?

But I know there is a risk he will lose all his files if editing the partitions goes wrong, so I'm encouraging him to backup everything to DVDs. He'll need about 10 DVDs and it'll take ages. What is the easiest safe way to do the backup? We would want to use something that can compress the files first, to save time and DVDs, and that can verify the archive after compression, then burn it across several DVDs, verifying the burns also. Any graphical or command-line tools recommended? It needs to be a simple process so we don't mess it up.

---

### Post by ngch on 2006-12-18
Creating a 200GB FAT32 partition is generally not a good idea, because it has severe performance issue on such a large capacity. Also, the maximum file size on an FAT32 partition is 4GB, so any file bigger than 4GB on the NTFS drive will not be writeable on FAT32. It is possible though, so you can try.

As for backing up those stuff... the only solution I can think of is, copying it to another external hard drive? ](*,)

---

