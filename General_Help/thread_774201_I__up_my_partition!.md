---
title: "I ****** up my partition!"
date: 2008-04-29
forum: General Help
---

### Post by Fixman on 2008-04-29
I wanted to format my computer when I installed Hardy, but I wanted to keep some files, so I created a secondary partition, installed Hardy there, and copied the files I needed from the primary partition. After that, I just deleted my primary partition, and moved to the left and resized my secondary partition so it could fit my whole entire disk. But, while I was doing this last operation, there was a lightout on my neighborhood, so my computer shutted down. Now, the only thing I got is a messed up partition, and a big unused space. Is there any way I can recover some files that I lost? Is there any program recovery file for Linux?

[[IMG]http://img180.imageshack.us/img180/3874/screenshotdevsdagpartedjz4.th.png[/IMG]](http://img180.imageshack.us/my.php?image=screenshotdevsdagpartedjz4.png)

[[IMG]http://img139.imageshack.us/img139/6776/screenshotdiskfilebrowsqy8.th.png[/IMG]](http://img139.imageshack.us/my.php?image=screenshotdiskfilebrowsqy8.png)

---

### Post by bigken on 2008-04-29
I know [this]("http://www.diskinternals.com/linux-reader/") works well using windows

---

### Post by bingoUV on 2008-04-29
[B]messed up partition
[/B]    What do you mean when you say messed up partition? 
1. Was the second screenshot taken after this "messing up"?  Many files seem to be accessible.
2. Can you mount this partition?
3. Did you try booting the system? 
4. Does the system boot? 
5. Did you try fsck? 
6. Any errors in general system usage?
7. Any other symptoms of messing up?

[B]Steps to probably fix it
[/B]1. Backup the whole hard disk to a spare hard disk, except maybe the swap partition. In case the steps below may further damage your data, you can restore to this state.
2. 
```

sudo resize2fs /dev/sda2 68.94G

```
3. 
```

sudo e2fsck -f /dev/sda2

```

---

