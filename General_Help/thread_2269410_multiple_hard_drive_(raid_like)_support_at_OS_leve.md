---
title: "multiple hard drive (raid like) support at OS level"
date: 2015-03-15
forum: General Help
---

### Post by Cool_Javelin on 2015-03-15
I was wondering if there is native support, or perhaps third party that can handle the following...

1) Multiple hard drives but with a single point (either a mount point, or a folder with transparent links to files) for viewing files.

2) When a file is written to the single point, the OS should decide on which drive the file goes based in the space available on the drive (again transparently.)

For example:
I have a lot of movie media, more then will fit on one drive.
 I want a single directory to list all my movies.
When I save a new movie, I would like it to go to the drive that has the most free space (This will tend to balance the drives and keep one from filling up.)

I do not want a RAID like drive where striping is used (Too unreliable.)
I also don't want any special hardware like drive controllers.

LVM looks nice, but I think there are some drawbacks:
   if one drive fails, all the data may be lost. 
   from what I read, one movie may be spread across 2 disks.
   It may be that one disk will fill up before the other gets utilized.

Thanks, Mark.

---

### Post by Holger_Gehrke on 2015-03-15
Might I direct you to my answer to the very similar question [you posted four days ago]("http://ubuntuforums.org/showthread.php?t=2268812") ?

---

### Post by Cool_Javelin on 2015-03-15
Thanks, Holger:

I never got an email telling me that thread had been responded to (I will check my settings) and I will look into that "FUSE" thing and likely mark both these as solved.

Sorry for the redundancy.

Thanks again, Mark.

---

