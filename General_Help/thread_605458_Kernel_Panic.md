---
title: "Kernel Panic"
date: 2007-11-07
forum: General Help
---

### Post by topher200 on 2007-11-07
I am getting an unexplainable Kernel Panic on boot. I have been using this system for over a year, with no recent major problems. I may have done an update since the last restart that booted, but I think it was all trivial, third party programs. When I do a normal boot, the Ubuntu loading splash screen freezes about halfway through the third bar. When I do a command line boot, I get a variaty of different error messages, depending on where the computer froze on booting, although it is always around the same spot. Here is the most common one:
```

[42.660000] Code: 00 8d b6 00 00 00 00 8d bf 00 ... goes on for about 30 pairs
[42.660000] EIP: [<c02329de>] task_running_tick+0x1e/0x260 SS:ESP 0068:87f7d908
[42.660000] Kernel panic - not syncing: Fatal exception in interrupt
[42.672000] uhci_hcd 0000:00:1d.3: host controller processor, something bad happened!
[42.672000] uhci_hcd 0000:00:1d.3: host controller halted, very bad!
[42.672000] uhci_hcd 0000:00:1d.3: HC died; cleaning up

```

I've also gotten this one:
```

Filesystem is NOT clean
fsck 1.40.2 (12-Jul-2007)
[42.180000] Bug: unable to handle kernel paging request at virtual addess dfb92000
[42.180000] printing eip:
[42.180000] *pde= 1fb91163
[42.180000] PANIC: double fault, gdt at c17f8000[225 Bytes]
[42.180000] double fault, tss at c17f4000
[42.180000] eip= c0284210 esp= ... other random e** combinations with 8 digit addesses, around 10 of them

```
This is transcribed computer to paper to forum, so there are probably typos.

I have no idea what I could have done to cause this problem, or where to start looking to try to solve it. Any help would be greatly appreciated.

Oh, and one more difficulty- I dropped my laptop on its CD drive last year and it doesn't recognize CD's anymore, so I can't do the LiveCD thing. I am dualbooting, so I installed Wubi (creates a folder in Windows that acts as a full Ubuntu install). I can boot into that so I can access all the files on my linux partition, and I will make a LiveUSB if nessissary.

Thanks again!

---

### Post by geraldm on 2007-11-07
The first problem to fix is the dirty filesystem.  Use a rescue disk, or a livecd, but
do a filesystem check.  You do need to know which partition the / root is on, and what
the filesystem type is.  This is normally found in the /etc/fstab file.  The partition needs to 
be unmounted, and then do the check.  The command used would be 
fsck.ext3 <device> (for an ext3 filesystem) OR
fsck.ext2 <device> (for an ext2 filesystem.
Substitute the correct partition for <device>, such as /dev/hda2 (if the second partition)
read the manpage for the command that you use.
Usually there is a reboot after that command.
The problem would possibly come from an improper shutdown or system crash from an
earlier session.


Gerald

---

### Post by topher200 on 2007-11-07
I booted into Wubi, and ran fsck.reiserfs (my root's filesystem). Wubi called my Ubuntu partition /dev/disk. so I used that (I also tried hda2, sda2, sdb and others incase I was reading the naming data wrong, but none of those were found). The output:

```

topher@ubuntu:~$ fsck.reiserfs /dev/disk/
reiserfsck 3.6.19 (2003 www.namesys.com)

*************************************************************
** If you are using the latest reiserfsprogs and  it fails **
** please  email bug reports to reiserfs-list@namesys.com, **
** providing  as  much  information  as  possible --  your **
** hardware,  kernel,  patches,  settings,  all reiserfsck **
** messages  (including version),  the reiserfsck logfile, **
** check  the  syslog file  for  any  related information. **
** If you would like advice on using this program, support **
** is available  for $25 at  www.namesys.com/support.html. **
*************************************************************

Will read-only check consistency of the filesystem on /dev/disk/
Will put log info to 'stdout'

Do you want to run this program?[N/Yes] (note need to type Yes if you do):Yes
bread: Cannot read the block (2): (Is a directory).
reiserfs_open: bread failed reading block 2
bread: Cannot read the block (16): (Is a directory).
reiserfs_open: bread failed reading block 16

reiserfs_open: the reiserfs superblock cannot be found on /dev/disk/.
Failed to open the filesystem.

If the partition table has not been changed, and the partition is
valid  and  it really  contains  a reiserfs  partition,  then the
superblock  is corrupted and you need to run this utility with
--rebuild-sb.

```

I searched for 'stdout' to see if that gave more information, but I was unable to find it, and google was no help in determining what it is (I am guessing a text log file, but I didn't find anything in /var/log). I tried using the rebuild superblock option, since it seemed like the next logical thing to do:

```

topher@ubuntu:~$ fsck.reiserfs /dev/disk/ --rebuild-sb
reiserfsck 3.6.19 (2003 www.namesys.com)

*************************************************************
** If you are using the latest reiserfsprogs and  it fails **
** please  email bug reports to reiserfs-list@namesys.com, **
** providing  as  much  information  as  possible --  your **
** hardware,  kernel,  patches,  settings,  all reiserfsck **
** messages  (including version),  the reiserfsck logfile, **
** check  the  syslog file  for  any  related information. **
** If you would like advice on using this program, support **
** is available  for $25 at  www.namesys.com/support.html. **
*************************************************************

Will check superblock and rebuild it if needed
Will put log info to 'stdout'

Do you want to run this program?[N/Yes] (note need to type Yes if you do):Yes 
bread: Cannot read the block (2): (Is a directory).
reiserfs_open: bread failed reading block 2
bread: Cannot read the block (16): (Is a directory).
reiserfs_open: bread failed reading block 16

reiserfs_open: the reiserfs superblock cannot be found on /dev/disk/.
rebuils_sb: cannot open device /dev/disk/

```

I don't know what to do next. The partion can't be THAT corrupted, as I can access its files from Wubi and Windows (using YAReG). Does anyone have any ideas?

---

### Post by topher200 on 2007-11-09
Does anyone have any ideas? Any config files that could be causing this kind of error to randomly start occurring?

---

### Post by geraldm on 2007-11-10
There are later versions of the  tools 3.6.23
Try to obtain later tools.  The superblock must pass the filesystem check, newer tools 
might help.  
If that does not assist, I would try to salvage all the files that can be saved.

Gerald

---

