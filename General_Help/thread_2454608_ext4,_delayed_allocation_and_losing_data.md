---
title: "ext4, delayed allocation and losing data"
date: 2020-12-02
forum: General Help
---

### Post by jcdenton1995 on 2020-12-02
Hello all,

So I fell down the rabbit hole and now I'm trying to understand a passage taken from the [Wikipedia article]("https://en.wikipedia.org/wiki/Ext4") on ext4:

> A new temporary file ("file.new") is created, which initially contains  the new contents. Then the new file is renamed over the old one.  Replacing files by the rename() call is guaranteed to be atomic by [POSIX]("https://en.wikipedia.org/wiki/POSIX")  standards – i.e. either the old file remains, or it's overwritten with  the new one. Because the ext3 default "ordered" journaling mode  guarantees file data is written out on disk before metadata, this  technique guarantees that either the old or the new file contents will  persist on disk. ext4's delayed allocation breaks this expectation,  because the file write can be delayed for a long time, and the rename is  usually carried out before new file *contents* reach the disk.

So my understanding is that the safe method that programmers traditionally use to overwrite a file on a storage device is to write a copy of the updated version of the file to the drive, then use the rename system call which overwrites the old version of the file with the new one 'atomically', and because the rename (overwrite) is forced to either occur or not occur, and because ext3 defaults to 'data=ordered', the files metadata won't be updated until the main write is complete, meaning there is no chance of a situation where the filesystem *believes *that the data has been updated when in fact power was lost during the write and the data is corrupted.

But ext4 and specifically delayed allocation breaks this, because if the updated version of the file hasn't been flushed from the write cache, the rename can still take place but if, for example, power is lost, the old version will be corrupted by the unsuccessful write and the new version will be gone due to having being stored in volatile memory only.

If anyone can critique that I'd appreciate it!

---

### Post by TheFu on 2020-12-02
Ever noticed that moving a huge file within the same file system is nearly instantaneous, but moving a file across file systems takes as long as a full copy?

Learn about inodes.  This understanding is critical to understanding how file systems work and why having 2 versions of the same file immediately swap, nearly instantaneously, is possible, assuming the files are on the same file system.  The old copy of the file isn't overwritten. It is just orphaned.

---

### Post by jcdenton1995 on 2020-12-02
I know a bit about inodes, like how inode numbers are unique at the partition level and they store metadata, how they relate to hard / symbolic links, and store everything about their file except the data itself, and the OS references files by their inode number, some filesystems can run out of them if they are filled with tiny files etc.

But I don't understand how they relate to this, are the inode tables part of the journal?

---

