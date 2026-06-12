---
title: "lost+found"
date: 2006-08-04
forum: General Help
---

### Post by tonyisntcreative on 2006-08-04
Something I've been wondering for a while and can't seem to find an answer on.

What is the "lost+found" folder for on ext3 filesystems?  (Might be in others, too, but I've only been on linux for about 9 months and ext3 is the only one I've used.)

I'm kind of clueless as to what it's there for.  Anyone?

---

### Post by moma on 2006-08-04
Fsck -- File System Check.

In the rare cases of crash or malfunction of a harddrive the system vil automatically perform a filesystem check (fsck) at next boot. You can also perform fsck manually.

Fsck puts all corrupted (possibly damaged)  and rescued files to "lost+found" directory. Each partition has its own lost+found.

Fsck has separate tools for each filesystem type; fsck.ext2, fsck.ext3, fsck.reiserfs, fsck.cramfs etc. You must unmount a partition before perfoming fsck.

Read:
[http://www.tldp.org/LDP/Linux-Filesystem-Hierarchy/html/lostfound.html]("http://www.tldp.org/LDP/Linux-Filesystem-Hierarchy/html/lostfound.html")

Note: I believe that Ubuntu will run fsck each 30'th day or after 180'th boot or mount, which ever come first. Correct me if you know better ;-)

You can probably force a filesystem check at next boot by creating a "forcefsck" file in the root of partition.
Sample:
$ [COLOR="Green"]sudo touch /forcefsck[/COLOR]
or
$ [COLOR="Green"]sudo touch /media/sdb1/forcefsck[/COLOR]
----

shutdown -F is another way to force fsck at next reboot.
$ [COLOR="Green"]sudo shutdown -F -h now[/COLOR]
And you'll see "Checking all filesystems" message in the boot screen when starting up.

Then check "lost+found" directory in each partition to see if any bad files was rescued.

---

### Post by tonyisntcreative on 2006-08-04
That explains it!  Thanks.

I've sometimes deleted it and when it does do a check (I think I've read it say something much like "this file system has been mounted 30 times without being checked...check forced") it will automatically add the lost+found folder.

---

### Post by tIcK_tAcK on 2007-10-27
but what if I have 3 ext3 disk's and only the 1st is were linux is located, all of the disk's will have a enormous "lost+found" (+2GB) taking several hard disk space. How can I shut this off?

---

### Post by theta4 on 2008-06-02
> **moma said:**
> Fsck -- File System Check.

...

Note: I believe that Ubuntu will run fsck each 30'th day or after 180'th boot or mount, which ever come first. Correct me if you know better ;-)

...

I believe that's the default, but you can change that when you create the partition, and I think after you've made it as well.

---

### Post by wolfen69 on 2008-06-02
> **moma said:**
> 
Note: I believe that Ubuntu will run fsck each 30'th day or after 180'th boot or mount, which ever come first. Correct me if you know better ;-)



it's every 30-ish boot. sometimes less, sometimes more.

---

### Post by tdrusk on 2008-06-03
> **wolfen69 said:**
> it's every 30-ish boot. sometimes less, sometimes more.

Yeah. If it's 180 I need to go to some addiction class.

---

### Post by MaxIBoy on 2008-06-04
> **tIcK_tAcK said:**
> but what if I have 3 ext3 disk's and only the 1st is were linux is located, all of the disk's will have a enormous "lost+found" (+2GB) taking several hard disk space. How can I shut this off?
That would be dangerous, as it would seriously screw up disk checking, and if you corrupted a file system (happens more often than you'd think, usually you don't notice because it's repaired on startup) you'd be screwed. 

I don't know how big a lost and found directory normally is, I don't have my laptop with me to check. But it certainly sounds bigger than it should be. If your lost and found is extra big, your file systems might be corrupted very often (only cause I could think of,) unless you have a lot of files. Might be something to look into.

---

### Post by K.Mandla on 2008-06-04
Moved to General Help (archive).

Closed to prevent further necromancy.

---

