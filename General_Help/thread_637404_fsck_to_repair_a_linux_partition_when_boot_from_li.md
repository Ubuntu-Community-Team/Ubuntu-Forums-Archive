---
title: "fsck to repair a linux partition when boot from liveCD...grub error 17"
date: 2007-12-10
forum: General Help
---

### Post by phineaus on 2007-12-10
So here goes round number 3! (because its a repost...no responses in Hardware, so maybe I miscategorized it...been sitting unanswered for a week)

I recently rebooted my desktop PC that has been up and running for quite some time without problems, and received error 18 from Grub, resulting in me not being able to boot in either WinXP or UBUNTU Gutsy. To make a long story short, I did not update or change anything...I was just rebooting because it was slow. I posted this thread about it and if you would like the long story check it out:

[http://ubuntuforums.org/showthread.php?t=625568](http://ubuntuforums.org/showthread.php?t=625568)

That entailed me booting the live CD, checking the partition table after installing testdisk, and eventually changing the number of heads from 16 to 255 in order to have it read the partition correctly. Basically, before or after this change, testdisk could not output the contents of my linux partition, saying that it seemed damaged. After the change, I get error 17 from Grub. I think some part of the filesystem is damaged, and I want to learn how to use fsck to try and fix it and recover my data. Any recommendations on how to do that?

The following is a printout of my fdisk results and what happens when I try to run fsck on that partition:

ubuntu@ubuntu:~$ sudo fsck -v -f /dev/hda5
fsck 1.40.2 (12-Jul-2007)
e2fsck 1.40.2 (12-Jul-2007)
fsck.ext3: Attempt to read block from filesystem resulted in short read while checking ext3 journal for /dev/hda5

ubuntu@ubuntu:~$ sudo mke2fs -n /dev/hda5
mke2fs 1.40.2 (12-Jul-2007)
Filesystem label=
OS type: Linux
Block size=4096 (log=2)
Fragment size=4096 (log=2)
5636096 inodes, 11261549 blocks
563077 blocks (5.00%) reserved for the super user
First data block=0
Maximum filesystem blocks=0
344 block groups
32768 blocks per group, 32768 fragments per group
16384 inodes per group
Superblock backups stored on blocks:
32768, 98304, 163840, 229376, 294912, 819200, 884736, 1605632, 2654208,
4096000, 7962624, 11239424

ubuntu@ubuntu:~$ sudo fsck -b 32768 -v -f /dev/hda5
fsck 1.40.2 (12-Jul-2007)
e2fsck 1.40.2 (12-Jul-2007)
fsck.ext3: Attempt to read block from filesystem resulted in short read while checking ext3 journal for /dev/hda5

ubuntu@ubuntu:~$ sudo fsck -b 32768 -cf /dev/hda5
fsck 1.40.2 (12-Jul-2007)
e2fsck 1.40.2 (12-Jul-2007)
fsck.ext3: Attempt to read block from filesystem resulted in short read while checking ext3 journal for /dev/hda5

ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/hda: 60.0 GB, 60022480896 bytes
255 heads, 63 sectors/track, 7297 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x783d8f59

Device Boot Start End Blocks Id System
/dev/hda1 * 1 1612 12948358+ 7 HPFS/NTFS
/dev/hda2 1613 7297 45664731 f W95 Ext'd (LBA)
/dev/hda5 1613 7220 45046197 83 Linux
/dev/hda6 7221 7297 618471 82 Linux swap / Solaris

Disk /dev/hdd: 8455 MB, 8455200768 bytes
255 heads, 63 sectors/track, 1027 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x1f7be346

Device Boot Start End Blocks Id System
/dev/hdd1 * 1 1026 8241313+ 7 HPFS/NTFS
ubuntu@ubuntu:~$

HELP is more than appreciated! I am an intermediate to basic user...have been only booting UBUNTU for about 9 months now on my laptop and more recently my desktop I got out of storage...Thats a lot of info...but hey...the best guys usually ask for it anyway in my experience.  

Since I posted this the first time, my laptop crashed and had problems with the forced fsck after 30 boots, so I had to do it manually with fsck -y

That got that machine back up and running...hoping for a cure here too!

---

### Post by matthewcraig on 2007-12-11
How did you change the heads on your hard disk?  Brings me back to the olden days of computing to hear you say that.  More information would be helpful in helping you.  For example, what partition is GRUB installed?  You show all these fsck outputs, but they are not meaningful if you don't say what you are intending to do at each step.  I am guessing GRUB is not installed at "hda5" since it is the fifth partition on the disk, but who knows!?

It does stink when you cannot boot your computer - in any operating system.  At least Ubuntu has a boot disk where you can still get online and access your hard drive.  Put in more information about your computer, and hopefully someone can be of some assistance.

---

### Post by phineaus on 2007-12-11
Maybe I should clarify that this whole business started in the post that I linked to at the top.  It was there that I used testdisk to analyze the partition that I was unable to mount when I used the liveCD for Gutsy to boot.  It corresponds to my 43gb linux partition.  When I boot with the LiveCD, I can access all of the files on the NTFS partition containing windows.  Please read that post as it has a detailed history of what changes I made when I originally received GRUB error 18 upon my random reboot...

[http://ubuntuforums.org/showthread.php?t=625568](http://ubuntuforums.org/showthread.php?t=625568)

As far as my fdisk output, /dev/hda5 is my linux partition, but my understanding is that the bootable partition on which GRUB is installed is /dev/hda1 (NTFS).  I believe it starts to load GRUB there, but is it not referred to my primary linux partition?  The numbering of partitions seems arbitrary if it worked before, but upon looking at it, it does seem odd that my disk starts with hda1 and not hda0.  I have read that the way that partitions are named has changed from Fiesty to Gutsy, but I also had installed Gutsy directly to a clean partition without upgrading.  Everyday that has passed since the problem first occurred (more than a week ago), I feel like I lose my grasp on what the cause of this error may be.

---

### Post by matthewcraig on 2007-12-11
You know your other thread is entitled "GRUB boot error 18"...

So, what do we have:
Device Boot Start End Blocks Id System
/dev/hda1 * 1 1612 12948358+ 7 HPFS/NTFS
/dev/hda3 1613 7297 45664762+ 5 Extended
/dev/hda5 7221 7297 618471 82 Linux swap / Solaris
/dev/hda6 1613 7220 45046197 83 Linux

Your inodes are corrupt on hda6:
[ 577.268533] EXT3-fs error (device hda6): ext3_get_inode_loc: unable to read inode block - inode=8, block=1027

Did you try to run fdisk with the disk unmounted (through the liveCD ?)

---

### Post by mozetti on 2007-12-11
FYI - GRUB starts numbering partitions at 0, linux/fdisk lists them starting at 1.

To check the partition from the LiveCD, just boot into the LiveCD and open a terminal. Run fdisk -l to get your partition table, and then run e2fsck on /dev/hdx# (corresponding to hour HDD (hda, hdb, etc) and the partition number (hda1, hda2, etc).

Before you run e2fsck, check the man page (man e2fsck) to see what options you want to use. But, basically your command would be: ```
sudo e2fsck /dev/hda6 -y -f
```

If you have a bad superblock (happened to me before, and e2fsck should tell you if it runs into a problem), then you need to use the -b option and specify the superblock. For example```
sudo e2fsck -y -f -b 8193
sudo e2fsck -y -f -b 16384

or most likely sudo e2fsck -y -f -b 32768
```

---

### Post by phineaus on 2007-12-11
I am about to boot the LiveCD again and I will try that.  In the meanwhile...an interesting finding.  Just for the hell of it I turned Mode to OFF on my harddrive in the bios, which I believe means not to use LBA.  Instead of error 17, I got error 5, which signifies a corrupt partition table.  Maybe my use of testdisk (in my previous thread where, yes, I was trying to solve my problems after getting error 18), to rewrite the number of heads from 255 to 16 in the partition table was a bad move.  It seemed odd to me at the time that somehow that specific value could have been changed during my reboot.  

I will post in 10 or 15 with the results of my trying to run fdisk, and also my attempt to run e2fsck on hda6 (which I thought was my swap partition for linux?).  Thanks for the help and attention!

---

### Post by phineaus on 2007-12-11
Ok...quick update.  ACTUALLY, the information quoted in matthewcraigs response:

So, what do we have:
Device Boot Start End Blocks Id System
/dev/hda1 * 1 1612 12948358+ 7 HPFS/NTFS
/dev/hda3 1613 7297 45664762+ 5 Extended
/dev/hda5 7221 7297 618471 82 Linux swap / Solaris
/dev/hda6 1613 7220 45046197 83 Linux

Your inodes are corrupt on hda6:
[ 577.268533] EXT3-fs error (device hda6): ext3_get_inode_loc: unable to read inode block - inode=8, block=1027

was from a previous fdisk and dmesg (bar) tail from before I used testdisk to change the partition table, and I will post with the updated information in one moment...

but basically, now /dev/hda6 is now /dev/hda5, both referring to my linux partition, and the subject of this current thread is why I cant seem to run fsck with the exact command (except different partition) that you recommended.  sorry for the confusion.  pasted output coming right up...

---

### Post by phineaus on 2007-12-11
Here goes...

ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/hda: 60.0 GB, 60022480896 bytes
255 heads, 63 sectors/track, 7297 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x783d8f59

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        1612    12948358+   7  HPFS/NTFS
/dev/hda2            1613        7297    45664731    f  W95 Ext'd (LBA)
/dev/hda5            1613        7220    45046197   83  Linux
/dev/hda6            7221        7297      618471   82  Linux swap / Solaris

Disk /dev/hdd: 8455 MB, 8455200768 bytes
255 heads, 63 sectors/track, 1027 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x1f7be346

   Device Boot      Start         End      Blocks   Id  System
/dev/hdd1   *           1        1026     8241313+   7  HPFS/NTFS
ubuntu@ubuntu:~$ sudo e2fsck /dev/hda6 -y
e2fsck 1.40.2 (12-Jul-2007)
/dev/hda6 is mounted.  

WARNING!!!  Running e2fsck on a mounted filesystem may cause
SEVERE filesystem damage.

Do you really want to continue (y/n)? no

check aborted.
ubuntu@ubuntu:~$ sudo e2fsck /dev/hda5 -y
e2fsck 1.40.2 (12-Jul-2007)
e2fsck: Attempt to read block from filesystem resulted in short read while checking ext3 journal for /dev/hda5
ubuntu@ubuntu:~$ fdisk /dev/hda5

Unable to open /dev/hda5
ubuntu@ubuntu:~$ 
ubuntu@ubuntu:~$ dmesg | tail
[  902.203457] usb 1-1: new low speed USB device using uhci_hcd and address 3
[  902.377548] usb 1-1: configuration #1 chosen from 1 choice
[  902.399935] input: Logitech Trackball as /class/input/input6
[  902.400036] input: USB HID v1.10 Mouse [Logitech Trackball] on usb-0000:00:11.2-1
[ 1000.782414] hda: dma_intr: status=0x51 { DriveReady SeekComplete Error }
[ 1000.782428] hda: dma_intr: error=0x40 { UncorrectableError }, LBAsect=25905122, sector=25905122
[ 1000.782439] ide: failed opcode was: unknown
[ 1000.782447] end_request: I/O error, dev hda, sector 25905122
[ 1000.782482] EXT3-fs error (device hda5): ext3_get_inode_loc: unable to read inode block - inode=8, block=1027
[ 1000.782780] EXT3-fs: invalid journal inode.
ubuntu@ubuntu:~$ 

That last part was me running dmesg | tail after attempting to open my linux partition in the GUI and it recommending just that in an error message saying it was unable to mount.  I hope that my problem is clearer.  My issue at hand seems to be why I am unable to run fsck on /dev/hda5, and instead get this error message: 

ubuntu@ubuntu:~$ sudo e2fsck /dev/hda5 -y
e2fsck 1.40.2 (12-Jul-2007)
e2fsck: Attempt to read block from filesystem resulted in short read while checking ext3 journal for /dev/hda5

---

### Post by mozetti on 2007-12-11
Try specifying the superblock and turning on verbose mode (to get as much detail from e2fsck as possible). By default your superblock should be for 4k clusters, so the command would be: ```
sudo e2fsck /dev/hda5 -v -y -b 32768
```

Some notes:

The -y flag means e2fsck will just assume "yes" for any questions it would ask, like "fix this problem?"

Make sure the disk isn't mounted before you run e2fsck ```
sudo umount /dev/hda5
```

The reason fdisk -l didn't work for hda**5** is because fdisk is for entire hard drives, not partitions.

---

### Post by phineaus on 2007-12-11
ubuntu@ubuntu:~$ sudo e2fsck /dev/hda5 -v -y -b 32768
e2fsck 1.40.2 (12-Jul-2007)
e2fsck: Attempt to read block from filesystem resulted in short read while checking ext3 journal for /dev/hda5
ubuntu@ubuntu:~$ 

I have read the fsck and e2fsck man pages and had tried all but the -v flag before.  

So I get what you mean about fdisk.  fdisk is a partitioner table manipulator, right?  so other than seeing what it outputs without the -l flag, that was just a test to see if it worked.  Any other ideas?

---

### Post by mozetti on 2007-12-11
Ok, based on some googling, it doesn't look good. Apparently the journal is massively corrupted. _Try to recover any data first._

You can try to recover whatever data is on it by using the **dd** command. I haven't used it myself, but it might help.

After that, you can try to use tune2fs to try to repair it. Check the man page for any options, but at the least you'd want to use:```
sudo tune2fs -f /dev/hda5
```

Just be aware that the -f flag will force tune2fs to keep going despite any errors. It could cause total data loss and filesystem corruption, but at this point you're already there (IMO).

If that doesn't work, then your best bet is to blast the partition and make a new one (after you've attempted to recover the data).

---

### Post by phineaus on 2007-12-11
Thats kinda the impression I got.  However, I just googled dd and not sure what that is?  Is it a switch on fsck?  How do I try and use that?  Otherwise, I am going to hope for the best and try tune2fs...

---

### Post by mozetti on 2007-12-11
dd is a command for copying files. Do a search here to find out how to use it for recovering files from a partition or making an image of the partition -- not sure how to use it myself.

Of course, if the data on the partition isn't important and you don't care about losing it then I'd just run tune2fs to see if it can be fixed. If not, then just delete and re-make the partition.

---

### Post by phineaus on 2007-12-11
So after reading the man file on tune2fs, I found that:

 tune2fs - adjust tunable filesystem parameters on ext2/ext3 filesystems

Running the basic command you specified resulted in:

ubuntu@ubuntu:~$ sudo tune2fs -f /dev/hda5
tune2fs 1.40.2 (12-Jul-2007)
Usage: tune2fs [-c max_mounts_count] [-e errors_behavior] [-g group]
        [-i interval[d|m|w]] [-j] [-J journal_options]
        [-l] [-s sparse_flag] [-m reserved_blocks_percent]
        [-o [^]mount_options[,...]] [-r reserved_blocks_count]
        [-u user] [-C mount_count] [-L volume_label] [-M last_mounted_dir]
        [-O [^]feature[,...]] [-T last_check_time] [-U UUID] device

That said, I think that I should use the following switches to tell the computer that there is no journal, since the corrupt journal seems to be the issue correct?  

 -f     Force the tune2fs operation to complete even in the face of errors.  This option is useful when removing the has_journal filesystem feature from a filesystem which has an  exter&#8208;
              nal journal (or is corrupted such that it appears to have an external journal), but that external journal is not available.

              WARNING: Removing an external journal from a filesystem which was not cleanly unmounted without first replaying the external journal can result in severe data loss and filesystem
              corruption.
 

-O [^]feature[,...]
              Set  or clear the indicated filesystem features (options) in the filesystem.  More than one filesystem feature can be cleared or set by separating features with commas.  Filesystem features prefixed with a caret character (’^’) will be cleared in the filesystem’s superblock; filesystem features without a prefix character or prefixed with a plus  character (’+’) will be added to the filesystem.

              The following filesystem features can be set or cleared using tune2fs:

                   dir_index
                          Use hashed b-trees to speed up lookups in large directories.

                   filetype
                          Store file type information in directory entries.

                   has_journal
                          Use a journal to ensure filesystem consistency even across unclean shutdowns.  Setting the filesystem feature is equivalent to using the -j option.

                   sparse_super
                          Limit the number of backup superblocks to save space on large filesystems.

              After  setting  or  clearing  sparse_super and filetype filesystem features, e2fsck(8) must be run on the filesystem to return the filesystem to a consistent state.  Tune2fs will print a message requesting that the system administrator run e2fsck(8) if necessary.  After setting the dir_index feature, e2fsck -D can be run to convert existing directories to the hashed B-tree format.

              Warning:  Linux kernels before 2.0.39 and many 2.1 series kernels do not support the filesystems that use any of these features.  Enabling certain filesystem features may prevent the filesystem from being mounted by kernels which do not support those features.


Maybe running the following would allow me to use e2fsck:

sudo tune2fs -f -O^has_journal /dev/hda5
 
Does that make logical sense?  I did not read anything that lent me to believe that tune2fs does anything but alter parameters, much less fix the filesystem.  Am I missing something? 

Thanks for your help hashing this out.

---

### Post by mozetti on 2007-12-11
I haven't used tune2fs before because I haven't needed to, but yes I think that would be the command and options you'd want to run.

---

### Post by phineaus on 2007-12-11
Can I get a second on that anyone?  

I just dont want to mess with my partition table in such a way if there is some other solution to recovering my data and getting GRUB to load...

---

### Post by matthewcraig on 2007-12-11
Why, oh why, where you playing around with your head and cylnder disk parameters in your BIOS.  How much data is on there?  Can you re-install?  Remember to backup /home next time.

---

### Post by phineaus on 2007-12-11
Ok. I know that this thread makes me the KING of embedded threads.  But its pretty clear in my last thread (were I was getting error 18 from GRUB) why I did what I did WITH testdisk (not in the bios).  Testdisk had trouble correctly reading my partition table, and recommended that I try changing that setting from.  I did and it read the table correctly.  Now I get error 17 instead of 18.  

EITHER WAY, both before and after this alteration, the problem seems to be the same.  I am trying to get to the bottom of it, but uncertain about using tune2fs to tell the partition table that there is not journal (since it seems to be corrupt).  Even if I succeed in doing this and running fsck to do some repairs, I believe I have to get an uncorrupt journal to replace the old one, right?  This might be time for a new thread...haha.

---

### Post by mozetti on 2007-12-11
Actually, you may not need a journal. We're clearly in theoretical territory for me, as I haven't screwed up my hard drive this bad before. :)

But, the ext3 file system is basically just the ext2 file system with journaling. You might not need to add the journal back right away. If you could get the file system available you can move the data off, and then try to put the journal back using tune2fs and see if you can turn it back into an ext3 system.

But man, you really did a number here, didn't you? :D

Any luck with the dd command to recover your data first?

---

### Post by phineaus on 2007-12-11
Again...I know that this thread only references my first post with a link, but what happened to my hard drive is mystery.  I shut down the computer and it completed shut down, then when I rebooted I got an error 18 from GRUB.  No idea why as I had not updated anything.  My computer had crashed before, but not for almost a week before this problem, so there is a possibility of filesystem corruption that went undetected over time.  Still, unless it is rather extensive damage, I dont get why GRUB wont even load.  That pretty much means that the MBR is damaged, correct?  

As far as dd goes, I read the man file, and there are multiple ways to reference the location of the data to be copied, but none are as comprehensive as the directory structure that I use when mounting the partition...so I dont even know where to start.

I will post results from my adventures in tune2fs in a bit...

---

### Post by phineaus on 2007-12-11
ubuntu@ubuntu:~$ sudo tune2fs -f -O^has_journal /dev/hda5
tune2fs 1.40.2 (12-Jul-2007)
The needs_recovery flag is set.  Please run e2fsck before clearing
the has_journal flag.
ubuntu@ubuntu:~$ sudo e2fsck /dev/hda5 -v -y -b 32768
e2fsck 1.40.2 (12-Jul-2007)
e2fsck: Attempt to read block from filesystem resulted in short read while checking ext3 journal for /dev/hda5
ubuntu@ubuntu:~$ 

AND there we have it folks.  Yet another catch 22.  Any further ideas as to what my problem could be?  Thinking of starting another thread...

---

### Post by phineaus on 2007-12-11
Ok, I read in another post on this subject that I should try the following:

ubuntu@ubuntu:~$ sudo debugfs /dev/hda5
debugfs 1.40.2 (12-Jul-2007)
/dev/hda5: Can't read an inode bitmap while reading inode bitmap

Thats no good.  Being as there was NO crash or anything, I find it hard to believe that my disk is damaged.  I have not had any major issues with UBUNTU until this, and I REALLY do not want to lose my faith.  I VERY MUCH enjoy using an OS that does not have MYSTERY problems, like the kind I always experienced as a windows user.  There MUST be a rational explanation and method by which I can repair this parition and/or recover the data (luckily I have a backup of all of it about a month and a half ago, but I things I will lose include email correspondence since I am a pop3 account user).  

Is there a way to remove the so called needs_recovery flag from the partition so I can turn off the has_journal flag and see if that is the issue with not being able to run e2fsck?

---

### Post by phineaus on 2007-12-12
bump...help?!  I need to get past this brick wall I am up against...

---

### Post by phineaus on 2007-12-12
This entry in the tune2fs man file keeps calling my attention when I ponder this.  
 
 -f     Force the tune2fs operation to complete even in the face of errors.  This option is useful when removing the has_journal filesystem feature from a filesystem which has an  external journal (or is corrupted such that it appears to have an external journal), but that external journal is not available.

              WARNING: Removing an external journal from a filesystem which was not cleanly unmounted without first replaying the external journal can result in severe data loss and filesystem corruption.

If I invoke tune2fs as follows:

ubuntu@ubuntu:~$ man tune2fs
ubuntu@ubuntu:~$ sudo tune2fs -f -O ^has_journal /dev/hda5
tune2fs 1.40.2 (12-Jul-2007)
The needs_recovery flag is set.  Please run e2fsck before clearing
the has_journal flag.

I still hit the same wall?  If I am FORCING it, then why am I still not able to reset the flag with tune2fs?  

I have found this exact same dilemma brought u on other internet posts, but have yet to see someone offer a solution or explanation...PLEASE HELP

---

### Post by mozetti on 2007-12-12
Well, it's pretty much just you and me talking here at this point. And I've passed my real world experience halfway down page 2 of this thread.

As someone else eluded to, I think you really, really borked your filesystem when messing with the heads/sectors. I don't know what you've got on this partition, but IMO it's time to just forsake the data if you can't find a way to recover it and delete that partion. Then, just set up a new partition in the empty space.

---

### Post by phineaus on 2007-12-12
Thanks for the response.  I would agree but for the reason part.  What I changed about the partition table can be undone with testdisk just as it was done.  Then I will have error 18 I suppose.  Maybe I will try that and then rerun a lot of these diagnostics and attempts at repair to see if I can figure it out.  

Mainly this is just a matter of principle at this stage, as I had not updated my filesystem or ANYTHING prior the the original crash.  Things happen for reasons, but the probability of some physical damage to my disk during a clean shutdown process that happened to affect my ext3 journal and/or MBR seems like a long shot...  I will be back later today with an update as I have not seen a fix for anything resembling my issue.

---

