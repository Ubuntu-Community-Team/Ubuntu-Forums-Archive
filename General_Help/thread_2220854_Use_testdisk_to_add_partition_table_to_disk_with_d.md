---
title: "Use testdisk to add partition table to disk with data, but no part table"
date: 2014-04-29
forum: General Help
---

### Post by jimmy the saint on 2014-04-29
So my 2TB disk has an ext4 filesystem, but no partitions.  I think this came about as the result of a ddrescue operation in which I apparently forgot to partition the current drive before resucing the data from the old, failing drive.

Anyway, there are TONS of tutorials for recovering partition tables with testdisk, but none seem to cover adding a partition table and preserving a filesystem on the block device.

Has anyone experienced this?  I have backed up the data, but I'm trying to save myself the 12 hour delay of having to repopulate the drive data after partitioning it.

---

### Post by oldfred on 2014-04-29
As I mentioned in your other thread, several others have posted same issue and none that I know of were able to force a reconfiguration.

Normally partition table info is in MBR, and now first partition starts at sector 2048. And a partition has a hidden first sector that is a PBR or another partition table. The PBR is used for the extended or logical partitions to have a link entry to the next logical partition and Windows stores boot code.
Since you may have data starting at sector 1, I do not see how you could force a partition table into drive without overwriting data. And I do not know how data is written in a drive that is not partitioned.

 Here is the specification of the partition table format:
[http://www.win.tue.nl/~aeb/partitions/partition_tables.html#toc3](http://www.win.tue.nl/~aeb/partitions/partition_tables.html#toc3)

---

### Post by jimmy the saint on 2014-04-29
Thanks for the replies (to both posts).

I started a new thread since I was asking a new question, though related to the same incident.  

I'm just going to format the drive and copy everything back over.  I figured I'd see if there was a way to go about this without doing that, because I would have learned something new in the process.

---

### Post by dragonfly41 on 2014-04-30
> I'm just going to format the drive and copy everything back over.  I  figured I'd see if there was a way to go about this without doing that,  because I would have learned something new in the process.

This tip might be too late to help you .. however ..

I'm currently using testdisk and I note that in the dropdown menu
"please select the partition type"
there is an option 
[None]Non partitioned media ... 
(usually I select [Intel] in this menu)
selecting [None] and if you click on Enter and then select
[Advanced] you should see a list of your files.

This might have worked on your files .. but you've probably reformatted and added a partition by now.

---

