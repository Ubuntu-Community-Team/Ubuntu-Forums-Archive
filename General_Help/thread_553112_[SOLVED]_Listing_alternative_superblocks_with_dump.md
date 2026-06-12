---
title: "[SOLVED] Listing alternative superblocks with dumpe2fs?"
date: 2007-09-17
forum: General Help
---

### Post by lotuseclat79 on 2007-09-17
How do I use dumpe2fs to dump out alternative superblocks with the -ob and -oB options?  I am using Ubuntu 7.04 e2fsprogs.

I know that: $ sudo dumpe2fs -h /dev/devicename will list the primary superblock, but I do not understand how to specify the alternative superblocks using the -ob and -oB options.  I have not found any tutorial on the use of the options or how to specify them.

The blocksize of my device is 4096 and I know that the list of superblock alternatives:
Primary superblock at 0, Group descriptors at 1-5
  Backup superblock at 32768, Group descriptors at 32769-32773
  Backup superblock at 98304, Group descriptors at 98305-98309
  Backup superblock at 163840, Group descriptors at 163841-163845
  Backup superblock at 229376, Group descriptors at 229377-229381
  Backup superblock at 294912, Group descriptors at 294913-294917
  ...
are logical block numbers, e.g. 32768 for the 1st backup superblock alternative, and that given the blocksize=4 then you must multiply logicalblocknumber*4 to get 131072 for the location of the 1st alternative superblock (I think) - is that correct?  Here is the problem with that approach:

With the following command, I get the subsequent output (where devicename is an actual device name):
$  sudo dumpe2fs -h -ob 131072 -oB 4096 /dev/devicename | head -40
dumpe2fs 1.40-WIP (14-Nov-2006)
dumpe2fs: No such file or directory while trying to open 131072
Couldn't find valid filesystem superblock.

The reason I am asking is that on occasion the ext_attr Filesystem feature goes missing and the next time I attempt to mount the ext3 filesystem the journal is not applied until I either bootup with Dapper Live CD, and then reboot back to Fiesty Live CD - note: Dapper never has this problem.

If I can find a valid alternative superblock with the dumpe2fs command properly specified then the plan is to reconstitute the primary superblock using the dd command to fix it and not have to use the Dapper Live CD or actually boot up the ext3 Linux on the device.
Assuming , of course, that there is a valid alternative superblock that can list out the missing ext_attr Filesystem feature (in the primary superblock).

Then again, instead of using dd, it may be easier to just use the alternative superblock (if valid) to mount the ext3 filesytem.

Tia,

-- Tom

---

### Post by lotuseclat79 on 2007-09-17
> **lotuseclat79 said:**
> How do I use dumpe2fs to dump out alternative superblocks with the -ob and -oB options?  I am using Ubuntu 7.04 e2fsprogs.

I know that: $ sudo dumpe2fs -h /dev/devicename will list the primary superblock, but I do not understand how to specify the alternative superblocks using the -ob and -oB options.  I have not found any tutorial on the use of the options or how to specify them.

The blocksize of my device is 4096 and I know that the list of superblock alternatives:
Primary superblock at 0, Group descriptors at 1-5
  Backup superblock at 32768, Group descriptors at 32769-32773
  Backup superblock at 98304, Group descriptors at 98305-98309
  Backup superblock at 163840, Group descriptors at 163841-163845
  Backup superblock at 229376, Group descriptors at 229377-229381
  Backup superblock at 294912, Group descriptors at 294913-294917
  ...
are logical block numbers, e.g. 32768 for the 1st backup superblock alternative, and that given the blocksize=4 then you must multiply logicalblocknumber*4 to get 131072 for the location of the 1st alternative superblock (I think) - is that correct?  Here is the problem with that approach:

With the following command, I get the subsequent output (where devicename is an actual device name):
$  sudo dumpe2fs -h -ob 131072 -oB 4096 /dev/devicename | head -40
dumpe2fs 1.40-WIP (14-Nov-2006)
dumpe2fs: No such file or directory while trying to open 131072
Couldn't find valid filesystem superblock.

The reason I am asking is that on occasion the ext_attr Filesystem feature goes missing and the next time I attempt to mount the ext3 filesystem the journal is not applied until I either bootup with Dapper Live CD, and then reboot back to Fiesty Live CD - note: Dapper never has this problem.

If I can find a valid alternative superblock with the dumpe2fs command properly specified then the plan is to reconstitute the primary superblock using the dd command to fix it and not have to use the Dapper Live CD or actually boot up the ext3 Linux on the device.
Assuming , of course, that there is a valid alternative superblock that can list out the missing ext_attr Filesystem feature (in the primary superblock).

Then again, instead of using dd, it may be easier to just use the alternative superblock (if valid) to mount the ext3 filesytem.

Tia,

-- Tom
After briefly looking at the source code for dumpe2fs.c at sourceforge.net, it was obvious that two mistakes were made in the assumptions I had applied - i.e. absent any good examples on the Internet for guidance - there were none that I could find.

The first mistake was to place a space between the -ob and -oB and their respective values - the command works perfectly when no space is between -ob32768 and -OB4096.  So, the appropriate way to issue the command using an alternative superblock is:

$ sudo dumpe2fs -h -ob32768 -oB4096 /dev/devicename (where devicename is a real device name)

The above command highlights the second mistake which was the bit about multiplying by 4 assuming the logical block not to be the proper usage.

Substituting in the backup superblock values subsequently revealed that the alternative superblocks were missing the ext_attr Filesystem feature, and were in worse shape than the primary superblock.

Since the mount count has just passed the maximum mount count, it looks like it is time to increase the maximum from 30 to a higher number, and see if the debugfs command can be used to set the ext_attr when the primary superblock loses it.

What I should now do is to boot up the Linux ext3 filesystem drive so that fsck will automatically run and hopefully correct all of the superblocks.  Since I am running from a Live CD environment, I know I could choose to issue the fsck without rebooting the Linux ext3 filesystem - but, the home Linux OS knows more about its journal than the Live CD, even though that should make no difference despite the two Linuxes being different versions.

I can now check the condition of all of the alternative superblocks to see if they were corrected after rebooting twice - once to bring up the other Linux filesystem and execute fsck on boot up, and two to get back to the Live CD environment from which I am now booted.

This thread is now resolved as far as I am concerned regarding the thread's question.

-- Tom

---

