---
title: "The file is too large for the destination file system ext3"
date: 2014-12-12
forum: General Help
---

### Post by ahobo on 2014-12-12
I'm rearranging some files.
I'm currently in Windows running ext2fsd from sourceforge.
Mounts fine and turned the readonly check off.
Have a 1TB NTFS drive copying files to a 1TB ext3 external drive.

When I cut and paste files to the external drive I get this error:
```
The file is too large for the destination file system
```

I know there's enough space, the files are mostly linux distros 500mb - 1.5gb.
When I cut & paste some other files, they go through just fine.
It's pretty random as to which files work and which don't. But the ones that don't paste stay that way.

I've yet to try it on my Ubuntu side (dualboot) 'cause it's a little messed up right now.
Should I run fsck from a live environment?
Any suggestions?

---

### Post by carl4926 on 2014-12-12
Try a Live system like parted magic
Here is a fairly recent version
[https://dl.dropboxusercontent.com/u/10573557/pmagic_2013_08_01.iso](https://dl.dropboxusercontent.com/u/10573557/pmagic_2013_08_01.iso)

---

### Post by sudodus on 2014-12-12
> **ahobo said:**
> I'm rearranging some files.
I'm currently in Windows running ext2fsd from sourceforge.
Mounts fine and turned the readonly check off.
Have a 1TB NTFS drive copying files to a 1TB ext3 external drive.

When I cut and paste files to the external drive I get this error:
```
The file is too large for the destination file system
```

I know there's enough space, the files are mostly linux distros 500mb - 1.5gb.
When I cut & paste some other files, they go through just fine.
It's pretty random as to which files work and which don't. But the ones that don't paste stay that way.

I've yet to try it on my Ubuntu side (dualboot) 'cause it's a little messed up right now.
Should I run fsck from a live environment?
Any suggestions?

I used to recommend ext2fsd, but I have seen, that there are problems. It can help but is far from bug-free. I think it is better to mount NTFS from linux (than to mount ext file systems from Windows). Do as suggested by *carl4926* or simply boot a live session from your Ubuntu DVD/USB install drive (until the installed Ubuntu system is running).

---

### Post by ahobo on 2014-12-13
> **sudodus said:**
> I used to recommend ext2fsd, but I have seen, that there are problems. It can help but is far from bug-free. 

I actually wasn't having any problems until I decided to switch from ext2fsd to [Paragon]("http://www.paragon-software.com/home/extfs-windows/")'s extfs driver. That's when things got messed up; like it would copy the file into 4 directories, or change entire folders into files. I'm pretty sure it's what messed up the superblock on one of my other drives. I thought this would be different for some reason, like linux permissions or whatnot.

Anyway, I got xubuntu live up and ran fsck on just about everything and it seemed to fix the problem. There were errors on the disk.

**TL;DR: Ran fsck on live cd and fixed it.**

---

### Post by sudodus on 2014-12-13
Congratulations :KS

And many thanks for sharing your solution :-)

Finally: did you get the version of ***ext2fsd*** that worked well for you directly from the sourceforce web page? I think this information can be valuable for many people.

---

### Post by ahobo on 2014-12-14
> **sudodus said:**
> 
Finally: did you get the version of ***ext2fsd*** that worked well for you directly from the sourceforce web page? I think this information can be valuable for many people.

Yes, I used the latest version (0.53 at time of writing) 

See more info on their website: [http://www.ext2fsd.com/](http://www.ext2fsd.com/)

And download from sourceforge: [http://sourceforge.net/projects/ext2fsd/files/Ext2fsd/](http://sourceforge.net/projects/ext2fsd/files/Ext2fsd/)

---

