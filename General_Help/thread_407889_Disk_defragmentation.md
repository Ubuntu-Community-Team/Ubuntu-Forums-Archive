---
title: "Disk defragmentation"
date: 2007-04-12
forum: General Help
---

### Post by AlbertCarlosEggs on 2007-04-12
Hi, I'd like to know if there is available any kind of tool as disk defragmentation. Where, How. Thanks in advance, Albert.

---

### Post by mujalan on 2007-04-12
I'm no help on this Albert, but I appreciate the question.  I'd like to know too!

Sonny

---

### Post by LMP900 on 2007-04-12
I'm assuming you're using ext3 as your filesystem. If this is so, then don't worry about disk fragmentation. It certainly occurs, but it should not be necessary to defragment. There are defragmentation tools for this filesystem, but I really wouldn't recommend them since there's a small chance that it could destroy your data.

Basically, as long as your computer usage is nothing out of the ordinary and there's sufficient space left on your hard drive, you shouldn't have to worry about fragmentation.

---

### Post by pointone on 2007-04-12
There is a defragmentation tool available for ext2 filesystems; it's found in the "defrag" package.

However, fragmentation in Linux is much less common than in Windows, and even when it does occur, it barely degrades performance at all.

If you're using ReiserFS, fragmentation doesn't exist. I don't think it's necessary to defragment in ext3, either... but I'm not 100% sure.

*EDIT* LMP900 beat me to it...

---

### Post by rsambuca on 2007-04-12
The ubuntu default ext3 filesystem does not require you to defragment your drive.  Unlike NTFS, the ext3 filesystem locates your files in different parts of the drive so files do not tend to get defragmented as much.  Also, the system will run a disk check every 25-30 boots or so (called fsck) and it helps address any problems.  If you run the following in a terminal, you can see how many times the drive has been mounted, and when the next fsck will be.```
sudo tune2fs -l /dev/sda1
```You will have to replace the "sda1" for the drive you want to view.

---

### Post by mujalan on 2007-04-13
Thanks folks.  Looks like another plus for linux to me!

Sonny

---

### Post by az on 2007-04-13
Fragmentation on Ext2/Ext3 filesystems becomes a problem when you fill your disk to the brim (over 90 percent).  If you then free up some space, the fragmentation will go away with normal use.

---

### Post by psusi on 2007-04-23
> **pointone said:**
> 
If you're using ReiserFS, fragmentation doesn't exist. I don't think it's necessary to defragment in ext3, either... but I'm not 100% sure.


Neither of these points is true.  All read-write filesystems can become fragmented, including ReiserFS.  There is no defragmenter for reiserfs, but the defrag package works on ext3.  The only difference between ext3 and ext2 is the use of the journal, so it "needs" defragmented as much as ext2.  

As others have pointed out though, unless you like watching the ascii map show your disk blocks moving around, there really is no need to defrag.

---

### Post by proalan on 2007-04-26
If you would like further insight into fragmentation

[http://www.bleepingcomputer.com/tutorials/tutorial55.html]("http://www.bleepingcomputer.com/tutorials/tutorial55.html")

---

### Post by jiminycricket on 2007-04-26
jdong made some tools to defragment ext3 if you really need it, there's a good discussion here:  [http://www.dslreports.com/forum/remark,18125810](http://www.dslreports.com/forum/remark,18125810)

[quote=jdong]> said by evilghost  :

Actually, there is a tool for ext2/ext3 filesystems but I think it's moot. It's written in Python by a guy over in the Ubuntu forums.

Here's the thread...

»[www.ubuntuforums.org/showthread.php?t=169551](www.ubuntuforums.org/showthread.php?t=169551)
Hi, I'm the guy who wrote pyfragtools 

I did so for the same reason someone mentioned in this thread: streaming performance. To the OP, I encourage you to read that thread at UbuntuForums, because it also answers some questions about fragmentation in Linux.

I'd like to start off agreeing with this thread's consensus that in normal usage patterns, ext2/3 reiserfs XFS JFS all do not need defragmentation, because

(1) their design and allocation policy naturally resists fragmentation.
(2) the filesystem design and the IO layer minimize the impact of fragmentation on performance, even when it does happen.

Fragmentation only arises in a few circumstances. One of the most common examples is torrenting a DVD ISO on a slow server (filling 4.7GB over the course of 1 week, let's say). This grows slowly enough that you can be prone to have some 500 "fragments", and read speed halves. This can cause issues if you must read the file back at some speed (i.e. a DVD burner -- burn quality suffers when buffer underrun prevention is activated). Another case is when you manage to fill a drive past 80% full, where it is difficult to find any large chunks of free space. Even if you manage to free up more space later, any files written in this time would be fragmented more than usual.

In this case, you'd want to "defragment" the file a bit. Pyfragtools is nothing but an overglorified copy-then-move program -- it repeatedly writes a copy of a file, checks if the new copy is less fragmented, and if so, moves that back as the source file.
--
UbuntuForums Administrator: try Ubuntu Linux[/quote]

---

### Post by wolter.kruger on 2008-06-19
Okay, I need to defrag my win2000 c: drive, a ntfs volume. I do not have admin rights under W2k, but my computer is dual boot with Ubuntu, where I am admin/root (sounds weird, but that's how our ICT organized it).

So, if I understood you right, the summary of the above is:
- There is a ntfs defrag-tool under Ubuntu, but it shouldn't be trusted
- My best option is to copy the C: volume back and forth to another disk
- As an alternative, ask the people from ICT to defragment my disk, and learn to speak Swahili in the time they take to respond

Is this correct?

---

