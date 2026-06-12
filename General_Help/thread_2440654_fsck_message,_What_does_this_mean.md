---
title: "fsck message, What does this mean?"
date: 2020-04-13
forum: General Help
---

### Post by wyattwhiteeagle on 2020-04-13
What does this mean and what should be my next steps?

```
wyatt@wyatt-Aspire-5733Z:~$ fsck -f -n
fsck from util-linux 2.31.1
e2fsck 1.44.1 (24-Mar-2018)
Warning!  /dev/sda1 is mounted.
fsck.ext4: Permission denied while trying to open /dev/sda1
You must have r/o access to the filesystem or be root
wyatt@wyatt-Aspire-5733Z:~$

```

---

### Post by wyattwhiteeagle on 2020-04-13
> **wyattwhiteeagle said:**
> What does this mean and what should be my next steps?

```
wyatt@wyatt-Aspire-5733Z:~$ fsck -f -n
fsck from util-linux 2.31.1
e2fsck 1.44.1 (24-Mar-2018)
Warning!  /dev/sda1 is mounted.
fsck.ext4: Permission denied while trying to open /dev/sda1
You must have r/o access to the filesystem or be root
wyatt@wyatt-Aspire-5733Z:~$

```

Ok, I found what the problem is. I need to use...

```
sudo fsck -f -n
```

I will post the results :)

---

### Post by wyattwhiteeagle on 2020-04-13
Why were some files ignored?

How do i correct those corrupted or broken files?

```

wyatt@wyatt-Aspire-5733Z:~$ sudo fsck -f -n
[sudo] password for wyatt: 
fsck from util-linux 2.31.1
e2fsck 1.44.1 (24-Mar-2018)
Warning!  /dev/sda1 is mounted.
Warning: skipping journal recovery because doing a read-only filesystem check.
Pass 1: Checking inodes, blocks, and sizes
Inodes that were part of a corrupted orphan linked list found.  Fix? no


Inode 46139134 was part of the orphaned inode list.  IGNORED.
Deleted inode 46142319 has zero dtime.  Fix? no


Inode 46143715 was part of the orphaned inode list.  IGNORED.
Inode 46143719 was part of the orphaned inode list.  IGNORED.
Inode 46143757 was part of the orphaned inode list.  IGNORED.
Pass 2: Checking directory structure
Pass 3: Checking directory connectivity
Pass 4: Checking reference counts
Pass 5: Checking group summary information
Block bitmap differences:  -34176 -(95453664--95453673) -(95470616--95470618) -184613665 -(184639397--184639404) -184676706 -(184678067--184678069)
Fix? no


Free blocks count wrong for group #2913 (8657, counted=8647).
Fix? no


Free blocks count wrong for group #5633 (372, counted=371).
Fix? no


Free blocks count wrong (238183630, counted=238179499).
Fix? no


Inode bitmap differences:  -46139134 -46142319 -46143715 -46143719 -46143757
Fix? no


Free inodes count wrong (60867473, counted=60867171).
Fix? no


Block bitmap differences: Group 2913 block bitmap does not match checksum.
IGNORED.
Group 5633 block bitmap does not match checksum.
IGNORED.


/dev/sda1: ********** WARNING: Filesystem still has errors **********


/dev/sda1: 187503/61054976 files (0.2% non-contiguous), 6006578/244190208 blocks
wyatt@wyatt-Aspire-5733Z:~$ 

```

---

### Post by wyattwhiteeagle on 2020-04-13
Ok, what's going on here...

```

wyatt@wyatt-Aspire-5733Z:~$ sudo fsck /-f /-y /-z
fsck from util-linux 2.31.1
e2fsck 1.44.1 (24-Mar-2018)
e2fsck 1.44.1 (24-Mar-2018)
e2fsck: need terminal for interactive repairs
e2fsck: need terminal for interactive repairs
e2fsck 1.44.1 (24-Mar-2018)
e2fsck: need terminal for interactive repairs
wyatt@wyatt-Aspire-5733Z:~$ 

```

---

### Post by TheFu on 2020-04-13
You cannot run fsck on any mounted storage.   Normally, fsck has a file system device as the input.
So, 
```
sudo fsck /dev/sdb1
```
would work, assuming that sdb1 is NOT mounted and has a Linux file system.  To run a check on sda1,  which is almost always mounted as /, then we need to boot from alternate media to run the command, or provide boot options to force it.  Since systemd, the easy method has been removed which is too bad.

What said to use those options?  On Unix, options don't use /h.  they use either short or long options.  -h or --help.

Don't use force unless someone you trust AND has the expertise says to do that.  it can do damage in this command.

[https://www.tecmint.com/fsck-repair-file-system-errors-in-linux/](https://www.tecmint.com/fsck-repair-file-system-errors-in-linux/)  has more detailed  info.  The /forcefsck method doesn't work anymore thanks to systemd.

---

### Post by TheFu on 2020-04-13
the fsck manpage says the -n is
```
       -n     For some filesystem-specific checkers, the -n option will  cause
              the fs-specific fsck to avoid attempting to repair any problems,
              but simply report such problems to stdout.  This is however  not
              true  for  all  filesystem-specific  checkers.   In  particular,
              fsck.reiserfs(8) will not report any corruption  if  given  this
              option.  fsck.minix(8) does not support the -n option at all.
```
Why use that option at all?

-y is to prevent questions.

-z isn't in my manpages.

Check your local manpages for what works on yours.  **man fsck** to access it.

---

### Post by wyattwhiteeagle on 2020-04-13
-z in fsck help is to create an undo file

```
wyatt@wyatt-Aspire-5733Z:~$ fsck help
fsck from util-linux 2.31.1
Usage: fsck.ext4 [-panyrcdfktvDFV] [-b superblock] [-B blocksize]
        [-l|-L bad_blocks_file] [-C fd] [-j external_journal]
        [-E extended-options] [-z undo_file] device


Emergency help:
 -p                   Automatic repair (no questions)
 -n                   Make no changes to the filesystem
 -y                   Assume "yes" to all questions
 -c                   Check for bad blocks and add them to the badblock list
 -f                   Force checking even if filesystem is marked clean
 -v                   Be verbose
 -b superblock        Use alternative superblock
 -B blocksize         Force blocksize when looking for superblock
 -j external_journal  Set location of the external journal
 -l bad_blocks_file   Add to badblocks list
 -L bad_blocks_file   Set badblocks list
 -z undo_file         Create an undo file
wyatt@wyatt-Aspire-5733Z:~$ 



```

---

### Post by Yellow Pasque on 2020-04-14
> **TheFu said:**
> -z isn't in my manpages.
That's because you didn't fully read the manpage, or you completely missed this part:
> In actuality, fsck is simply a front-end for the various filesystem checkers (fsck.fstype) available under Linux.  ... ** Please see the filesystem-specific checker manual pages for further details.**
i.e.:
```
man fsck.ext4
```
;)

---

### Post by TheFu on 2020-04-14
```
$ man fsck
..
fsck  [-lsAVRTMNP] [-r [fd]] [-C [fd]] [-t fstype] [filesystem...] [--]
       [fs-specific-options]
```

Ain't no -z there.

OR
```
$ man fsck.ext4
...
NAME
       e2fsck - check a Linux ext2/ext3/ext4 file system

SYNOPSIS
       e2fsck  [  -pacnyrdfkvtDFV ] [ -b superblock ] [ -B blocksize ] [ -l|-L
       bad_blocks_file  ]  [  -C  fd  ]  [  -j   external-journal   ]   [   -E
       extended_options ] device

```
there. My point is that different releases have different versions of commands.  The supported options on 1 system may not exist on another.  My 16.04 servers don't have any -z option for fsck.

Always check the manpage ON THE SYSTEM where the command is to be run.  That _should_ have the correct, current, manpage for each command.   Except systemd stuff, it seems. The SystemD guys have a habit of mismatch between the code and the manpages, I’ve heard.

As long as the OP uses -n, nothing will be fixed.  The OP should be using something like
```
sudo fsck /dev/sdb1
```
after booting from a Try-Ubuntu flash drive.

---

### Post by Yellow Pasque on 2020-04-14
> **TheFu said:**
>  My point is that different releases have different versions of commands. ... Always check the manpage ON THE SYSTEM where the command is to be run.  That _should_ have the correct, current, manpage for each command.

If this is so important that it has to be Caps Lock'd, then why didn't you look at manpages that matched the OP's version (e2fsck 1.44.1 (24-Mar-2018)) instead of just saying "-z isn't in my (outdated) manpages"?
That's not exactly helpful..

---

### Post by TheFu on 2020-04-14
The OP is very new to Linux based on a number of other posts here.

Post #5 has the answer to the question.

Posts after that were about manpages and versioning of commands.  Basic understanding for someone working at the command line.

**$ fsck help** is a shadow of the information provided in the manpages.  Saying that -z isn't in the manpages on my system ( which **is** supported for another year, so not outdated at all ) just points out that local manpages have the most current, correct, information about commands ON THAT SYSTEM.  From the attempted use of odd options later in the thread, it is clear that some struggles are happening.

Using manpages is a basic skill that I teach in all my beginning Linux classes in the 1st or 2nd session.  Anyone working towards Linux certifications will use the manpages during the practical tests to ensure they have the correct options, for that specific system.

Whether it is useful or not is a matter of opinion.

BTW, do you have a short, quick, easy, answer, for the OPs original question?  How to run fsck on /dev/sda1?  Would love to learn it.  Since SystemD broke **sudo touch /forcefsck**, there hasn't been one to my knowledge.

---

### Post by Yellow Pasque on 2020-04-14
> **TheFu said:**
>   Saying that -z isn't in the manpages on my system just points out that local manpages have the most current, correct, information about commands ON THAT SYSTEM.
You don't need to CAPS LOCK it. I basically agree with you. I just asked why you didn't take your own advice and do a quick google for a newer version of the page if you didn't know or understand the "-z" option. It would have been quicker and less confusing than mentioning it the OP, who, as you noted, was already struggling.

> my system ( which **is** supported for another year, so not outdated at all )
It depends on which definition of outdated you use. Outdated does not necessarily mean obsolete. Anyway, your system is relatively outdated compared to the OP's, which, according to you, is the only version that matters.

> BTW, do you have a short, quick, easy, answer, for the OPs original question?  How to run fsck on /dev/sda1?  Would love to learn it.  Since SystemD broke **sudo touch /forcefsck**, there hasn't been one to my knowledge.

I've always done it from recovery mode in grub menu, and if that didn't work, I grabbed a LiveUSB. *Shrug*

---

### Post by DuckHook on 2020-04-14
May I politely request that the discussion be guided back to the OP's problem? I realize that we are all under stress given the current world circumstances. I'm not functioning at 100% patience either. So it's especially important for we old-timers to set the appropriate tone here.

I'm sure you will both agree.

---

### Post by Yellow Pasque on 2020-04-14
> **DuckHook said:**
> May I politely request that the discussion be guided back to the OP's problem?

Apologies for going out on the tangent there, but the user seemed confused by -z option and TheFu's response.

Anyway, the ball is in the OP's court. Maybe it got lost in the shuffle, but the way forward is to boot a LiveCD/USB and run fsck there. If the OP needs further instruction there, s/he should clarify.
If a USB stick isn't available (or one doesn't feel like downloading a full Ubuntu install just to make a LiveUSB) there's a relatively small distro made for this purpose that can even be burned to a CD : [http://www.system-rescue-cd.org/](http://www.system-rescue-cd.org/)

---

### Post by TheFu on 2020-04-15
I apologize too.  Just need to see where wyattwhiteeagle is with the fsck issue.  The live-boot storage doesn't have to be a USB flash drive. It can be an optical disc or SDCard or anything else that the computer can boot.  The only requirement is that /dev/sda1 not be mounted so fsck can be run on an unmounted file system.  Forcing an fsck on a mounted file system has always corrupted data IME.

All the manpage stuff was a tangent, but important.  It still is not the primary purpose for this thread.

Why I didn't go and look up the specific version of the manpage?  It never occurred to me. Sorry.

---

