---
title: "Recover lost ext3 partition"
date: 2007-05-03
forum: General Help
---

### Post by muguwmp67 on 2007-05-03
I wasn't paying attention while repartitioning in Windows, and accidentally deleted an ext3 partition.  This partition contained all of my media files (mp3, primarily, 150 GB worth).  I'm really depressed now and don't even want to think about how long it will take me to re-rip over 300 cd's.

I have not:
a.) formatted, or repartitioned the drive
b.) deleted any files from the drive

I'm hopeful that if all I have done is remove the partition header tables, there might be a way to rebuild them if I haven't written anything to the disk since.  (I've disconnected it in the meantime, to ensure this)

Can someone please tell me if there is any way to restore this, and either tell me the steps or point me at a howto that will help?  I haven't found anything isn the ubuntu forum.

I've never begged on these forums before, I am now.

Someone please help me!!!!

---

### Post by muguwmp67 on 2007-05-03
Ok, I was able to add an unformatted partition to the drive, and now I can see the files on it. 

However, when I look at gparted, it says that the filesystem is 'unformatted'

I'm afraid to write or read from the disk at this point, What do I need to do to change the filesystem ID?

---

