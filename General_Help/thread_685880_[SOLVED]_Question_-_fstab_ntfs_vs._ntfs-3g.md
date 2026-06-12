---
title: "[SOLVED] Question - fstab: ntfs vs. ntfs-3g"
date: 2008-02-02
forum: General Help
---

### Post by mirzmaster on 2008-02-02
I have an fstab question pertaining to NTFS partition mounting.

In gutsy, what is the difference between mounting an NTFS partition with the filesystem type of "ntfs" vs. "ntfs-3g"?

So what would be the difference between this...

```
/dev/sda3       /media/windows  ntfs defaults,locale=en_US.UTF-8     0       0
```

... and this... 

```
/dev/sda3       /media/windows  ntfs-3g defaults,locale=en_US.UTF-8     0       0
```

I would also like to better understand what the difference is between mounting partitions under /media and anywhere else on the filesystem.  I noticed that when I mount a partition under /media it now appears as a separate media drive in Computer.  In my case, this is desired.

But, when I asked a friend to mount one of his ext3 partitions under /media, it resulted in the drive being available in a read-only mode, which was not desired.  On the other hand, I can still write perfectly fine to my mounted NTFS partition under /media (mounted as filesystem type ntfs-3g).

Ideally I'd like to mount some of my ext3 partitions under /media as well, but would like to retain read-write permissions on them.

Bear in mind that all the ext3 partitions mentioned here -- mine and my friend's -- are non-essential partitions... just for storing files.  We are not trying to mount the home, root, or any other partition to /media.  :)

Thanks in advance!

---

### Post by jan quark on 2008-02-02
I am not that proficient in partitions and mounting as these guys are:

[http://users.bigpond.net.au/hermanzone/p10.htm](http://users.bigpond.net.au/hermanzone/p10.htm)

[http://ubuntuforums.org/showthread.php?&t=282018](http://ubuntuforums.org/showthread.php?&t=282018)

but here I have create a small list of useful links

[http://janquark.fatfreehost.com/partitions.html](http://janquark.fatfreehost.com/partitions.html)

---

### Post by wolfen69 on 2008-02-02
> I would also like to better understand what the difference is between mounting partitions under /media and anywhere else on the filesystem. I noticed that when I mount a partition under /media it now appears as a separate media drive in Computer. In my case, this is desired.
it doesnt really matter where you mount a drive. media is fine.

also, ntfs-3g is required to have read/write support in linux.

---

### Post by danwood76 on 2008-02-02
In gutsy there is no difference between ntfs and ntfs-3g.
Ntfs is just an alias for ntfs-3g.

As for the other question the only difference with mounting at /media is as you say it appears as a seperate drive.
Are you sure you (or your friend) mounted the ext3 with the correct privilages stated? as if you choose the wrong settings in fstab it will mount in root only mode.

regards,
Danny

---

### Post by mirzmaster on 2008-02-02
Thank you all for your input and the extremely helpful links.

I'm still unsure as to why my friend's ext3 partition mounted in a read-only mode.  I will play around with it though and see if I can force it into read-write mode.

---

### Post by danwood76 on 2008-02-02
You could try copying the settings from your /home entry in the fstab, that should give you write permissions.

---

