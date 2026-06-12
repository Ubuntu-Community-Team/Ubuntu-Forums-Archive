---
title: "Disk analysis tools"
date: 2008-05-27
forum: General Help
---

### Post by achelis on 2008-05-27
Hi coming from Windows I'm used to having to defrag once in a while (every day really ;)) Now I've read that ext2/3 doesn't get fragmented which sounds brilliant. My system is starting to get really slow however, and judging by the hard disk activity it sounds like a good old NTFS fragmentation. 

Now my question is: Is there any tool to analyze my disk, to see if it is really fragmented or whether I'm just paranoid ?

Then if it turns out it is I'll be interested in what to do about.. and if it isn't I'd be interested in other ways of speeding up my system.

/Thanks

(I'm using Ubuntu, but figured disk analysis applies to all variants)

---

### Post by abhiroopb on 2008-05-27
ext3 filesystems don't get fragmented because it uses an inherently different method of storing files. I can't remember but there is a long descriptive article about this. Even so you're computer will perform a check disk every 28 times you start the computer (or "mount" your primary partition. This should take care of it.

Otherwise open up gparted (type sudo gparted in the terminal) and there are some check disk tools here.

---

### Post by sdennie on 2008-05-27
You probably aren't suffering from fragmentation if you are using ext3 on a desktop system.  Sometimes Windows converts have a sort of paranoia about a linux machine running slower over time because it's something they are accustomed to with Windows.  It's not usually the case unless you are running really poorly behaved apps that are eating through your memory and causing you to swap to disk.  Before blaming the filesystem, I'd have a look at the apps you are running.

---

### Post by achelis on 2008-05-27
I thought swap had it's own partition ?

As for the file system check I thought it only checked for corrupt files et.c.

So does this mean there isn't any tools to check for fragmentation ?

Thanks for the gparted pointer - turns out I have my home folder on my boot partition.. is it possible to split that partition without doing a re-install?

---

### Post by ibuclaw on 2008-05-27
> **vor said:**
> You probably aren't suffering from fragmentation if you are using ext3 on a desktop system.  Sometimes Windows converts have a sort of paranoia about a linux machine running slower over time because it's something they are accustomed to with Windows.  It's not usually the case unless you are running really poorly behaved apps that are eating through your memory and causing you to swap to disk.  Before blaming the filesystem, I'd have a look at the apps you are running.

+1

Look for anything that you never user and disable it in the startup apps.

ie: Do you ever use Tracker? Tomboy? Bluetooth Manager?


Although, there is a small [defrag tool]("http://ubuntuforums.org/showthread.php?t=169551") a fellow ubuntuer of the community made.

Though, I would recommend that you use it **only for your NTFS drive**, and **only use it once every 6 months**.

> 
Small Note
**Do _not_ obsessive-compulsively run passes trying to achieve perfection.**
...
If you try too hard to defrag, what will happen is that while files may defragment, **free space will become fragmented in the process, which will ultimately lower write performance.**

You have been warned...

As for performance, I think that it is only natural for humans to think so.
We relish the speed.
We habituate the speed.
We supplicate for more.

ie:
0.8 seconds to open "Movie Player"???
That's point 1 of a second too slow!
I can juggle two balls in the boredom of that time! :mad:

:lolflag:

Create a new user and login to the account, if you are utterly convinced that it's quicker than your current one, you either need to tone down on your compiz effects or start removing junk from the startup menus.

Regards
Iain

---

### Post by ibuclaw on 2008-05-27
> **achelis said:**
> 
Thanks for the gparted pointer - turns out I have my home folder on my boot partition.. is it possible to split that partition without doing a re-install?

Yes.
Grab you're Ubuntu LiveCD and boot into it, as you cannot alter mounted partitions.

When you load gparted, shrink the size of your home folder, and create a new partition in the empty space.

Regards
Iain

---

### Post by justleen on 2008-05-27
> **tinivole said:**
> Yes.
Grab you're Ubuntu LiveCD and boot into it, as you cannot alter mounted partitions.

When you load gparted, shrink the size of your home folder, and create a new partition in the empty space.

Regards
Iain

... and do not forget to edit your /etc/fstab  to mount that new partition as /home.

and copy the old /home to this drive..

---

### Post by achelis on 2008-05-27
ah thanks.. that would have been logical next question :)

Anyways.. lunch, then download LiveCD and then fix partioning...

I'm currently trying to work out the results of the defrag tool - seems there are some files that are very fragmented. Oh well... copying to a new partition should make the whole fragmentation issue obsolete anyways ;)

and thanks to tinivole for the pointer to the defrag tool and partioning help..

---

### Post by sdennie on 2008-05-27
achelis: I completely understand the spirit of what you are trying to do (I too am a performance and power savings lunatic) but, if you are going to do low level things to your system, I would really find some benchmarks and try them before and after making your changes.  An informational tool saying, "The filesystem is 5% fragmented" or having a "general feeling of slowness" isn't really a benchmark and so you have no objective basis for comparison.  In fact, without some sort of formal benchmark, because you think you are making a beneficial change, psychologically, you are likely to believe that your change is beneficial even if it wasn't.

Just a tip.  ;)

Edit:
Basically, don't try to optimize something that isn't slow in the first place.

---

### Post by niteshifter on 2008-05-27
Hi,

These pages may be useful in understanding why defrag isn't needed:
[why_doesn_t_linux_need_defragmenting  (simple)]("http://geekblog.oneandoneis2.org/index.php/2006/08/17/why_doesn_t_linux_need_defragmenting").

[e2fsprogs site]("http://e2fsprogs.sourceforge.net/ext2.html"), in particular the "Design and Implementation of the Second Extended Filesystem" document. Keep in mind ext3 is just ext2 with journaling.

My 2 cents on the various defrag "tools": If they don't consolidate free space then what's the use? One is simply fixing a "problem" now at the expense of future r/w access times. If file consolidation is wanted, just roll the files / folder off the partition (to CD/DVD/NAS/another partition), delete, then roll it back onto the partition, letting the kernel / filesystem handle placement.

---

