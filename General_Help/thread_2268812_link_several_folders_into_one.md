---
title: "link several folders into one"
date: 2015-03-11
forum: General Help
---

### Post by Cool_Javelin on 2015-03-11
I would like to setup links (I guess make symlinks) such that when I do a listing of one folder, I see multiple folders elsewhere on different drives. Maybe this might be better called merge, or join, not sure of the terminology.

For example:

I have movies on 3 different disks. I would like to view a single media folder so when I do a ls of media, I get a transparent  listing of the other 3 disks.

I understand this may work for reading of existing files, and creating new files may be created in the media directory not one of the others.

Is this possible?

Thanks, Mark.

---

### Post by Holger_Gehrke on 2015-03-11
Your proposed solution is possible but kind of cumbersome and risky. What are you going to do if you want to move or delete one of the files ? Symbolic links can go 'stale' if the file they are pointing to is not there anymore ...

A better solution would probably be one of the Union-type FUSE (Filesystem in USErspace) modules. A list kind be found [here]("http://sourceforge.net/p/fuse/wiki/UnionFileSystems/"). mhddfs seems like a good fit for what you want. From the description in synaptic : 
> 
This FUSE-based file system allows mount points (or directories) to be
combined, simulating a single big volume which can merge several hard
drives or remote file systems. It is like unionfs, but can choose the
drive with the most free space to create new files on, and can move
data transparently between drives.

Close enough ?

---

