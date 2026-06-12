---
title: "Dual-boot: Vista locks partitions in hibernate."
date: 2007-12-16
forum: General Help
---

### Post by Vanten on 2007-12-16
When hibernating in vista, vista seams to place some kind of lock on the partitions that are visible in windows. So when starting ubuntu, ubuntu cannot access the partitions that were locked by vista. 

Is there a way to solve this?
It functions correctly when shuting down vista instead of hibernating it.

Running a dualboot system with vista and ubuntu 7.10. 4 partitions on one harddrive.
1. Vista system
2. Random files - this partition i'd like to access from ubuntu
3. swap
4. ubuntu

---

### Post by t-bone510 on 2007-12-16
As for the first question, I have no idea... the best I can say is "don't hibernate?" :)

What format is the "random files" partition in

---

### Post by Vanten on 2007-12-16
The random files partition is NTFS.

---

### Post by fain on 2007-12-16
This happened to me when my vista didn't shutdown properly once. When i tried to mount the drive it gave me a NTFS lock error, but said i could force it with a certain option but i did not want to try this.

---

### Post by mbeierl on 2007-12-17
Just as a note of caution: Windows is probably doing the right thing by "locking" the partitions when hibernated (did I just say that Windows is doing something right ?!?)

See, if you modify the filesystem in any manner at all while Windows is hibernated, you could get massive filesystem corruption when it comes back.  Windows (correctly) assumes that nothing else will touch the filesystem while it's gone.  This is part of optimized filesystem access for any os (Linux does the same thing with its filesystem cache.)

Just something to watch out for - never modify a filesystem out from under a hibernated os.

---

### Post by jooo on 2008-03-24
Sorry to ressurect an old thread. But is there no way to stop vista from locking it's partition/s when hibernating?

I've got a laptop that has both vista and ubuntu (hibernate works on both... it's a little buggy on ubuntu, but it's functional none the less). And thunderbird on both OSes share the same profile/data directory.

Currently the thunderbird settings reside on the same partition as vista. I'm planning to move it to another partition (formatted as ntfs) IF i can be sure that vista won't attempt to lock it when it hibernates.

Anyone care to share their wisdom regarding this? Thanks!

---

### Post by mbeierl on 2008-03-24
Again, if you perform any sort of modification of those Thunderbird files, when Vista comes back, it won't know about them and you'll get file system corruption and probably lose your email data.

If your intent is to view them read only, maybe consider putting them on a FAT32 file system instead, and mount that read-only under linux when Vista is hibernated.

Bottom line: writing directly to a file system that is "owned" by another operating system (be it Windows, Linux or whatever) is a dangerous operation.  File access is a very highly tuned aspect of an OS, and many assumptions are made about the OS being the only thing that writes to the file system - whether hibernated or live.

---

### Post by prshah on 2008-03-24
> **jooo said:**
> Sorry to ressurect an old thread. But is there no way to stop vista from locking it's partition/s when hibernating?

Anyone care to share their wisdom regarding this? Thanks!

Nope, and it's not just vista; hibernating XP will also not allow you to mount the partition.

If you are really keen maybe you can force-mount (--force) the partitions but I wouldn't do that; it seems to me to be as good a way as any to rack and ruin.

---

### Post by jooo on 2008-03-24
thanks for the answers.

but say if i put my data files on another partition and unmounted that partition (assuming vista allows that) before sending vista into hibernate, it should work fine?

---

### Post by mbeierl on 2008-03-24
Correct, if Vista *could* unmount it, then all would be good.  I've not heard of such a thing, unfortunately.  Except for going into the drive manager and unassigning its drive letter.  But that would be a real pain prior to every hibernation.

---

### Post by jooo on 2008-03-25
lol. i thought that there might be some easy way of doing this... maybe i should see if i can find/write a script of sorts to do this for me... And here I was thinking that it was an easy thing :|

---

### Post by lswest on 2008-03-25
actually, making a seperate partition and hibernating should be fine, as hibernate stores information on the system drive only, leaving the data partition completely free and accessible.  Might be worth a try.  Since the data written to the system disk makes it appear "in use" you can't mount it, if there is no such data on the data partition, it should work fine.

---

### Post by mbeierl on 2008-03-25
Again, the warning: operating systems aggressively cache information about their file systems, even when hibernated.  Changing the data out from underneath *any* suspended operating system without unmounting the file system first can result in data loss.  This is true for Linux as well as Windows.

jooo:  LOL!!!  Writing a script to do something in Windows :)  I'm sure something can be done, but I have no idea how, or where to even begin looking.  Unfortunately Windows was not designed to share things with other operating systems, so you really are working against a fundamental principle of the OS.  Best of luck!

---

### Post by jooo on 2008-03-25
I just found something rather bizzare by accident.

It seems that if you hibernate ubuntu, the boot into vista and hibernate it, you can still access your vista partitions via ubuntu. And of course weird things happen (same symptoms as force mounting the partition)

But then dell's media direct (stripped down/embedded win xp) seems to be able to access the vista partition even if vista has been hibernated... unless it's some how forcing an unlock... but still dosen't indicate why it's not causing me grief (unless, it's secretly trashing my partition bit by bit).

---

