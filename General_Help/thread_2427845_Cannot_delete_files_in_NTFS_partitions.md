---
title: "Cannot delete files in NTFS partitions"
date: 2019-09-26
forum: General Help
---

### Post by orthoducks on 2019-09-26
My system disk has an ext4 partition containing Ubuntu, an NTFS partition containing Windows, and an NTFS partition containing shared data. I backed it up and restored it using dd...conv=sparse. First I filled all of the partitions with a copy of /dev/zero to ensure that unallocated space in each partition was actually zeroed.

I was interrupted before the disk finished copying, and when I got back to the task I forgot the zero files were there. I tried to boot both Linux and Windows 10 and found that I couldn't.

I tried to use live Linux to delete the files. It says the Windows partition has no recognizable filesystem and suggests that I install packages ntfs-3g and ntfsprogs to get full NTFS support. The first package is already installed and apt-get can't find the second. Linux says the data partition is in an "unsafe state" and mounts it read-only.

I booted Windows from the original disk, but it won't recognize the existence of the cloned disk. I don't know why.

The only fix I can think of is to get another hard disk and restore the backup again, delete the zero files from it first, then boot Windows and use it to delete the zero files in the original restore's NTFS partitions. Only by the time I got that far I'd have another functioning disk, so there's be no point.

Is there any other way around this?

---

### Post by yancek on 2019-09-26
>  Linux says the data partition is in an "unsafe state" and mounts it read-only.

That message generally means the windows systems was left hibernated and no Linux OS will mount a hibernated filesystem partition.  You need hibernation off in windows.

---

### Post by orthoducks on 2019-09-26
Yancek, I appreciate your effort to be helpful, but you didn't read my message carefully. I know the cause of the problem and I explained it; it has nothing to do with hibernation. In any case I don't need to know how to prevent it; I need to know how to fix it.

---

### Post by yancek on 2019-09-27
How to fix it will probably require using windows tools as you won't be able to access it from Linux, it's a windows filesystem so best  to use windows tools on windows filesystems.

---

