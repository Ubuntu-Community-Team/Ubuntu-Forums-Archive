---
title: "Cannot copy files to external hard drive (&quot;Cannot allocate memory&quot;)"
date: 2015-08-17
forum: General Help
---

### Post by Y.P._Delta on 2015-08-17
I'm attempting to move several files onto an external hard drive. I was able to successfully move a few files over, and I've also got other files on the drive as well (I've had the drive for quite some time by now), but now all of a sudden, when I try to put anything on the drive, I get a dialog box which reads "Error while copying. There was an error creating the folder 'X-52495-2'." Clicking on Show more details gives me "Error creating directory: Cannot allocate memory".

Is there any way I can fix this? I know the drive still has 10GB of free space on it, and the files that are on it work with no problems, so it can't be the drive. I'm running Ubuntu 14.04 currently. If there's anything I need to add to this post (terminal prompts, etc.) I'll gladly do that.

---

### Post by oldfred on 2015-08-17
Does folder name actually have quote symbol in it?

What format is data partition?
Do you already have another X-52495-2?
Post this on external.
ls -l
df -h

---

### Post by Y.P._Delta on 2015-08-17
1) No. The quote marks are present in the dialog box, but not in the actual folder names themselves.
2) If you mean the filesystem type, it's formatted as msdos.
3) No. Each folder I'm attempting to move has its own unique name, and none of them will transfer, even though others did just minutes before.
4a) [FONT=courier new]ls -l [/FONT]doesn't seem to show anything related to my external, weirdly enough. If there's something else I should've done there, I'll do that, but nothing about it appeared.
4b) [FONT=courier new]df -h [/FONT]brings up [FONT=courier new]/dev/sdb1    233G    224G    9.3G    97%    /media/ypdelta/3473-4A7E [/FONT]for the drive. That's all correct, but I'm not sure I understand what I'm looking for there.

---

### Post by efflandt on 2015-08-17
It could be either of 2 things. I think the number of files or directories you can have in a root directory of a FAT32 partition is very limited compared with the number you can have in a subdirectory.

Larger FAT32 partitions have a larger cluster size. So it is possible that counting actual data of many partially filled clusters may use up all the clusters before the actual data stored equals the partition size.

---

### Post by oldfred on 2015-08-18
msdos is a partitioning type, FAT32 or NTFS may be the format.

I know that NTFS gets very slow if less than 10% free space inside it. It just about has no room to run defrag as that has to copy data to unused space to reorganize files. I would consider your drive full or actually over full now.

FAT32 also cannot store a file over 4GB.

---

