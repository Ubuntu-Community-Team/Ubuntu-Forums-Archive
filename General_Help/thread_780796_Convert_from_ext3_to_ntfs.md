---
title: "Convert from ext3 to ntfs"
date: 2008-05-03
forum: General Help
---

### Post by vishnumrao on 2008-05-03
I have two 500 Gb drives in a two bay external case. They are set to be individually seen when plugged to a machine. One drive is formatted ntfs, other is ext3. Both have content with very limited free space (max 10-15 Gb on each).

Problem: Till now I was plugging the external only into my Ubuntu machine. But now I want to hook up the external to my windows Xp latpop. 

Solutions tried: I popped in a GParted live cd and explored options to convert from ext3 to ntfs. But I felt, it would erase all my data and then format the drive to ntfs. Is this true? 

Is there any way I can convert ext3 to nfts without destroying the data on the drive?

Thanks in advance.

---

### Post by ibuclaw on 2008-05-03
Simple truth...

**No**, I don't believe there is a way to **convert**. from Ext3 to NTFS

And you are **wise** not to have gone through with the GParted scheme, as that would of **erased all data and re-formatted your partition.**

Unfortunately, there is not much you can do if your Hard-Drive is full and you have no space to back it up to.

**If you want access to your ext3 partition from Windows**, you can download and install a [**driver**]("http://www.fs-driver.org/index.html") which gives you **complete read/write access** from Windows.

The site says "Ext2", but Ext3 filesystems are backwards compatible (infact, they are both exactly the same in every way, just that one is a journaling file system and the other isn't).

Regards
Iain

---

### Post by vishnumrao on 2008-05-03
Tinivole,

Ext2 IFS for windows is interesting indeed. Will give it shot.

I had another reason for trying to convert to NTFS. My external case hardware is currently set to see the drives as JBOD. But it also has an option to combine the drives and show as one single big partition. 


Thanks for the reply.
Vishnu Rao.

---

### Post by frenchn00b on 2008-05-03
> **vishnumrao said:**
> I have two 500 Gb drives in a two bay external case. They are set to be individually seen when plugged to a machine. One drive is formatted ntfs, other is ext3. Both have content with very limited free space (max 10-15 Gb on each).

Problem: Till now I was plugging the external only into my Ubuntu machine. But now I want to hook up the external to my windows Xp latpop. 

Solutions tried: I popped in a GParted live cd and explored options to convert from ext3 to ntfs. But I felt, it would erase all my data and then format the drive to ntfs. Is this true? 

Is there any way I can convert ext3 to nfts without destroying the data on the drive?

Thanks in advance.

gparted is bit better with this distro: 
[http://partedmagic.com/wiki/PartedMagic.php](http://partedmagic.com/wiki/PartedMagic.php)

you maybe trying ... It should be possible somehow to make it. 
Testdisk can make backup of the partitions, so why not Converting ??
we also have "captive" like

---

