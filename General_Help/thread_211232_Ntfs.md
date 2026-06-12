---
title: "Ntfs"
date: 2006-07-08
forum: General Help
---

### Post by mnmmichael on 2006-07-08
Hello everyone

Is there a way that I can acess an NTFS file system with read and write capabilities? I use Windows as my primary operating system. However, there are files I would like to be acess on the Windows partition.

Also, is there a way to mount this onto a folder on my desktop? I think I can figure out how to do this, so if you don't know this one, please still answer my first question.

Thanks a ton!


Michael

---

### Post by adwait on 2006-07-08
NTFS support in linux is stil nascent and writing to an NTFS parttition is not possible, reading though is possible. IF you can, make a FAT32 partition through which you can share files between windows and linux. AS for mounting, not really sure about the GUI way to do this in Gnome, but in a terminal use
```
sudo vi /etc/fstab
```

Now find the parition you want and change its mount location to wherever you want it to be.

---

### Post by RAOF on 2006-07-08
> **adwait said:**
> NTFS support in linux is stil nascent and writing to an NTFS parttition is not possible, reading though is possible. 
...

Not true; you **can** have write access to NTFS partitions.  It's even safe, and (relatively) complete.  Check out the [NTFS-FUSE](http://www.ubuntuforums.org/showthread.php?t=142481&highlight=ntfs-fuse) howto :)

---

### Post by FredB on 2006-07-08
> **RAOF said:**
> Not true; you **can** have write access to NTFS partitions.  It's even safe, and (relatively) complete.  Check out the [NTFS-FUSE]("http://www.ubuntuforums.org/showthread.php?t=142481&highlight=ntfs-fuse") howto :)

Oh... Maybe it is great to some people, but I prefer not to write on NTFS using linux ;)

Anyway, thanks for the how-to.

---

### Post by RAOF on 2006-07-08
> **FredB said:**
> Oh... Maybe it is great to some people, but I prefer not to write on NTFS using linux ;)

Anyway, thanks for the how-to.

The old NTFS driver ate data regularly.  The new one is totally different, and has been written from the ground up for safety.  I believe the site of interest is [http://www.linux-ntfs.org/](http://www.linux-ntfs.org/), particularly [http://wiki.linux-ntfs.org/doku.php?id=whyisittakingsolong#bad_heritage](http://wiki.linux-ntfs.org/doku.php?id=whyisittakingsolong#bad_heritage).

---

