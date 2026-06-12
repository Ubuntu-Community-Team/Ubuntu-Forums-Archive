---
title: "Longer Boot Time"
date: 2007-01-15
forum: General Help
---

### Post by FFfanatic on 2007-01-15
Ok, recently after I installed edgy I started to get a longer boot time. From about 30s on a new system to 1 min 30s now. After about 25%-33% load complete it switches to text and this is what it says:

Starting up, can't allocate resource ...... (5+ times this line shows up with a different .....)
Activating swap.
Checking root filesys
fsck 1.39(29 May 2006)
/dev/hda3: clean, .......files, ......clusters
dosfsck 2.11, 12 Mar 2005, Fat32, LFN
/dev/had1: .....files, ......clusters
dosfsck 2.11, 12 Mar 2005, Fat 32, LFN
There are differences between boot sector and it's backup.
Differences: (offset: original/backup)
71:53/00, 72:68/00, 73:61/00, 74:72/00, 75:65/00, 76:64/00
Not automatically fixing this.
/dev/hda5 ....files, ......clusters

Any ideas on what's causing my increased boot time and how to fix it?

---

### Post by FFfanatic on 2007-01-15
bump

---

### Post by FFfanatic on 2007-01-16
Bump!

---

### Post by FFfanatic on 2007-01-17
Bump! Bump! Bump!

---

### Post by Patrick-Ruff on 2007-01-17
lol wow, perhaps you should make your statement a bit clearer, and don't bump all the time. that gets really annoying for moderators and people passing by reading the thread.

I'm not quite sure what has increased your boot time, but I recommend you try to recall ANY system changes you may have applied before this started happening.

---

### Post by FFfanatic on 2007-01-17
> **Patrick-Ruff said:**
> lol wow, perhaps you should make your statement a bit clearer, and don't bump all the time. that gets really annoying for moderators and people passing by reading the thread.
What's happening is that when I boot up, it goes through the progress bar of how much "ready" it is. When the bar gets to ~33%, it switches to a text-based mode and spits out that code from before and finishes the boot up. And with the bumping, I only tried to do it once it was a couple of pages down, but I'll hold off on that a bit more.

I'm not quite sure what has increased your boot time, but I recommend you try to recall ANY system changes you may have applied before this started happening.

And the system changes would have been those differences that it showed in the code (I have no clue what they mean).
*Possible Solve* Maybe?
Do you think that if I removed Ubuntu, resized my XP partition to full HD, then resize it back, that would overwrite and completely destroy any of those differences, and then reinstall edgy to get a fresh start.

---

### Post by FFfanatic on 2007-01-17
Sorry, posted 2x.

---

### Post by lukew on 2007-01-17
> **FFfanatic said:**
> Sorry, posted 2x.

It goes into the text based move when either a forced check is occurring or it runs into a problem.

Check you fstab to ensure that you are not enforcing a check each time; it does not look it but it is worth a try.

I would run a fsck and fix any errors as it look like it is checking for a reason, perhaps there is a disk problem which could be fixed with a fsck?

Luke

---

### Post by lukew on 2007-01-17
> **lukew said:**
> It goes into the text based move when either a forced check is occurring or it runs into a problem.

Check you fstab to ensure that you are not enforcing a check each time; it does not look it but it is worth a try.

I would run a fsck and fix any errors as it look like it is checking for a reason, perhaps there is a disk problem which could be fixed with a fsck?

Luke

Googled it and came up with this.

[http://www.linuxquestions.org/questions/showthread.php?t=40214](http://www.linuxquestions.org/questions/showthread.php?t=40214)

fsck will fix your issue by the sounds of it.

Luke

---

### Post by FFfanatic on 2007-01-17
OK, the fsck fixed the differences problem but I'm still having it check the system, since I'm not sure what to change. But here's my fstab:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda3
UUID=73ed431f-1fc7-4fc1-b8a6-155c240ce948 /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda1
UUID=02D2-3690  /media/hda1     vfat    defaults,utf8,umask=007,gid=46 0       1
# /dev/hda5
UUID=049B-BF0A  /media/hda5     vfat    defaults,utf8,umask=007,gid=46 0       1
# /dev/hda6
UUID=01f18b0f-82e0-4e28-a09f-2248689a9a76 none            swap    sw              0       0
/dev/hdb        /media/cdrom0   udf,iso9660 user,noauto     0       0

Either change this and repost it or tell me what to change..

---

### Post by FFfanatic on 2007-01-17
YAY! I found the problem, fixed the differences with fsck, then changed the 1 in /etc/fstab to a 0 (the bolded 0 is the 1 that I changed). Then I ran tune2fs -c 50 -i 2w /dev/hd** in terminal to disk check every 50 boot ups or every 2 weeks, whatever happens first.
The ** denotes the hard drive partition that Ubuntu is on. And it all worked.

# /etc/fstab: static file system information.
#
# <file system> <mount point> <type> <options> <dump> <pass>
proc /proc proc defaults 0 0
# /dev/hda3
UUID=73ed431f-1fc7-4fc1-b8a6-155c240ce948 / ext3 defaults,errors=remount-ro 0 **[SIZE="3"]0[/SIZE]**
# /dev/hda1
UUID=02D2-3690 /media/hda1 vfat defaults,utf8,umask=007,gid=46 0 1
# /dev/hda5
UUID=049B-BF0A /media/hda5 vfat defaults,utf8,umask=007,gid=46 0 1
# /dev/hda6
UUID=01f18b0f-82e0-4e28-a09f-2248689a9a76 none swap sw 0 0
/dev/hdb /media/cdrom0 udf,iso9660 user,noauto 0 0

---

### Post by dcstar on 2007-01-18
> **FFfanatic said:**
> YAY! I found the problem, fixed the differences with fsck, then changed the 1 in /etc/fstab to a 0 (the bolded 0 is the 1 that I changed). Then I ran tune2fs -c 50 -i 2w /dev/hd** in terminal to disk check every 50 boot ups or every 2 weeks, whatever happens first.
The ** denotes the hard drive partition that Ubuntu is on. And it all worked.

# /etc/fstab: static file system information.
#
# <file system> <mount point> <type> <options> <dump> <pass>
proc /proc proc defaults 0 0
# /dev/hda3
UUID=73ed431f-1fc7-4fc1-b8a6-155c240ce948 / ext3 defaults,errors=remount-ro 0 **[SIZE="3"]0[/SIZE]**
# /dev/hda1
UUID=02D2-3690 /media/hda1 vfat defaults,utf8,umask=007,gid=46 0 1
# /dev/hda5
UUID=049B-BF0A /media/hda5 vfat defaults,utf8,umask=007,gid=46 0 1
# /dev/hda6
UUID=01f18b0f-82e0-4e28-a09f-2248689a9a76 none swap sw 0 0
/dev/hdb /media/cdrom0 udf,iso9660 user,noauto 0 0

So you stop auto-checking of your root file system because the obvious problem with it slows your boot up?

How long before you are posting here complaining that your whole Linux system has crashed and it won't boot any more?

---

### Post by lukew on 2007-01-18
You don't have to have the  UUID in the file; strange how the device has been commented out and replaced by the UUID. 


Seen this:

[HTML]http://www.ubuntuforums.org/showthread.php?t=309645&highlight=fsck+on+boot[/HTML]

Looks like even changing the check options in: 

[HTML]http://www.die.net/doc/linux/man/man8/tune2fs.8.html[/HTML]

wont do anything.

If you want to disable the checking all the time and then check manually the last 1 in the column (the very last character on each line) can be changed to 0. This will flag the drive as not being checked. I would in all honetly change this back once 

[HTML]https://launchpad.net/ubuntu/+source/e2fsprogs/+bug/63175[/HTML]

has been fixed.

Luke

---

### Post by SlCKB0Y on 2007-01-18
bla

---

### Post by lukew on 2007-01-18
I agree with dcstar. If you disable it temporary I would start manually checking on a regular basis.

Dont forget to init 2 when you check /

Luke

---

### Post by Delkster on 2007-01-18
> **dcstar said:**
> So you stop auto-checking of your root file system because the obvious problem with it slows your boot up?

It may be that his partition (or something) is having some problems, but I've also had the automatic fsck of a vfat partition routinely take long enough that the boot splash screen switches to the text console even though the partition has no problems.

I've disabled it, too. (I never even write to that partition from Linux so the chances of breaking it from there aren't great.)

If there still is a real problem (besides the routine fsck.vfat taking a while), of course that should be corrected, but just because it takes a while doesn't have to mean that the original problem didn't get solved.

---

### Post by mcduck on 2007-01-18
> **FFfanatic said:**
> YAY! I found the problem, fixed the differences with fsck, then changed the 1 in /etc/fstab to a 0 (the bolded 0 is the 1 that I changed). Then I ran tune2fs -c 50 -i 2w /dev/hd** in terminal to disk check every 50 boot ups or every 2 weeks, whatever happens first.
The ** denotes the hard drive partition that Ubuntu is on. And it all worked.

# /etc/fstab: static file system information.
#
# <file system> <mount point> <type> <options> <dump> <pass>
proc /proc proc defaults 0 0
# /dev/hda3
UUID=73ed431f-1fc7-4fc1-b8a6-155c240ce948 / ext3 defaults,errors=remount-ro 0 **[SIZE="3"]0[/SIZE]**
# /dev/hda1
UUID=02D2-3690 /media/hda1 vfat defaults,utf8,umask=007,gid=46 0 1
# /dev/hda5
UUID=049B-BF0A /media/hda5 vfat defaults,utf8,umask=007,gid=46 0 1
# /dev/hda6
UUID=01f18b0f-82e0-4e28-a09f-2248689a9a76 none swap sw 0 0
/dev/hdb /media/cdrom0 udf,iso9660 user,noauto 0 0
Actually that's the exact opposite of the way I'd fix this. You should leave the '1' for the root partition, and then change the number for your FAT partitions to either 2 or 0 (2 to check them _after_ the root, or 0 to never check them). The important thing is that they shouldn't have the '1', which is for / only.

```
# /etc/fstab: static file system information.
#
# <file system> <mount point> <type> <options> <dump> <pass>
proc /proc proc defaults 0 0
# /dev/hda3
UUID=73ed431f-1fc7-4fc1-b8a6-155c240ce948 / ext3 defaults,errors=remount-ro 0 1
# /dev/hda1
UUID=02D2-3690 /media/hda1 vfat defaults,utf8,umask=007,gid=46 0 0
# /dev/hda5
UUID=049B-BF0A /media/hda5 vfat defaults,utf8,umask=007,gid=46 0 0
# /dev/hda6
UUID=01f18b0f-82e0-4e28-a09f-2248689a9a76 none swap sw 0 0
/dev/hdb /media/cdrom0 udf,iso9660 user,noauto 0 0
```
Edgy's installer has done the same mistake on all installs I've made on machines with FAT partitions..

---

### Post by FFfanatic on 2007-01-20
With regards to changing the values from 1 to 0, I also changed the other two 1's to 0's so it won't check. But using tune2fs, I have it check every 50 times or every two weeks, so wouldn't that take care of manual checking?

---

### Post by mcduck on 2007-01-20
> **FFfanatic said:**
> With regards to changing the values from 1 to 0, I also changed the other two 1's to 0's so it won't check. But using tune2fs, I have it check every 50 times or every two weeks, so wouldn't that take care of manual checking?

no. having a '0' in fstab completely disables the fsck for that partiton.

You really should use a '1' for root, and I recommend using '2' for all Ext partitions. I don't think fsck is any use with FAT or NTFS partitions so use '0' for those.

---

