---
title: "Fiesty Live CD file system mount bug, Dapper ok"
date: 2007-08-19
forum: General Help
---

### Post by lotuseclat79 on 2007-08-19
I run Fiesty from a Live CD, either Kubuntu or Ultimate Ubuntu 1.4 Live CDs.  This problem does not occur when using Dapper Live CD.  I do not have an Edgy Live CD.

I have an 80GB SATA Linux disk with a journalled ext3 file system installed (Fedora Core 3 aka FC3).  I mount it during a Live CD session to copy initialization scripts and data that has been stored from previous Live CD sessions using these commands from the root account:
# mkdir /tmp/disks-conf-sdb2
# mount -v -t ext3 -o sync /dev/sdb2 /tmp/disks-conf-sdb2

When I boot from either Fiesty Live CD, the FC3 disk is spinning but not booted and running FC3 in my computer desktop system - i.e. no Lan here.

If the FC3 disk is mounted about 23 times without actually being booted up, the next actual boot will trigger an fsck of the disk's file ext3 system.  As data has been stored in a /root subdirectory (from a Live CD session) since the last boot of the FC3 disk, I kindof expect the FC3 file system journal is out-of-phase, but have no idea whether that may influence, contribute to, or cause this problem.  If it does then why does the problem not occur with Dapper?  Source code changes in the Edgy-Fiesty file system?

Here is a description of the problem with Fiesty which Dapper does not have (I do not know if Edgy Eft has the same problem since I have never run it's Live CD).

After somewhile, at the start of a Live CD session when I run the two commands above and try to access the subdirectory under the /root directory on the FC3 ext3 file system, not only are not all of the files in the FC3 /root directory not accessible - e.g. mbox has a date and size that is inconsistent when everything is accessible, the size is way smaller and the date is from its original installation.  The main problem being that my subdirectory under /root on the FC3 disk ext3 file system is not visible or accessible in any way shape or form as are a lot of files that have been created since the original FC3 installation on the disk.  Remeber, the FC3 disk is only spinning and is not booted up, so its journal software cannot be running which leads me to believe that it can neither cause nor contribute to the mount problem.

As I said above, the problem does not exist in Dapper Drake Ubuntu 6.0.6 LTS Live CD, but does exist in Kubuntu and Ultimate Ubuntu 1.4, both Fiesty Fawn 7.04 releases.

A file system change in the source code between Dapper-Edgy-Fiesty may be the cause and a file system guru familiar with the source code may be able to determine the cause or if there is any differences in the file system source code that could possibly cause this problem.

When I booted up the FC3 disk immediately after checking whether Dapper had the problem (No), an fsck was not performed as the file system was scanned in the ext3 file systems's superblock as "clean", and a subsequent Fiesty Live CD session still manifested the problem.  I have reverted to using the Dapper Live CD in order to post this new thread message.

Can an Ubuntu Linux file system guru and/or someone familiar with any file system coding changes between Dapper-Edgy-Fiesty please comment on this problem.  Perhaps the Live CD file system mount command is different from an installed version of Fiesty?

Tia,

-- Tom

P.S.  I am on a dialup account, so I do not have the bandwidth to check the file sytem source code changes myself.

---

### Post by lotuseclat79 on 2007-08-20
Since an ext3 filesystem is simply a journaled version of an ext2 filesystem, looking at the e2fsck (8) man page revealed that the journal is first applied and then the fsck command is executed.

The problem then may be that the Fiesty Live CD mount command is not appliying the journal before mounting the FC3 ext3 filesystem.  At least Dapper has been consistent and I have not seen this problem with it.

Since the symptom I am experiencing appears to be equivalent to using the ext3 option, noload, which would not load the jornal on the mount command, I may be able to recreate what I am seeing.  The contents of the /root directory should have the latest file be an mbox file with the date of original installation.  That, at least to me, would be confirming evidence that the Live CD mount command is failing to load and apply the journal of the ext3 FC3 filesystem before mounting it.

If that is the case, then it would appear that the Fiesty Live CD mount command is not applying the journal before completing the mount.  If so, that would mean there may be a bug in the Fiesty mount command (source code change I assume between Dapper-Edgy-Fiesty).

I will try to recreate the symptom (although it will inevitably happen in due time) with the noload option in the mount command to see if the files under the /root directory are what I have observed when the problem has occured, and then report the results here in this thread.

-- Tom

P.S.  A debugging/trace version of the executable code of the Live CD mount command would be very helpful at this point in time to confirm that when this problem occurs what is happening in the mount command.

---

### Post by lotuseclat79 on 2007-08-20
In attempting to use the noload ext3 option on the mount command to recreate what happens when the problem occurs, I did the following:

From the root account, I tried the following command, and got the results:
# mount -v -t ext3 -o noload /dev/sdb2 /tmp/disks-conf-sdb2
mount: wrong fs type, bad option, bad superblock on /dev/sdb2,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so
and upon checking with the dmesg command got:
ext3: No journal on filesystem on sdb2

At least now I know when the problem does occur to use the dmesg command to check what is recorded.

I suspect that what is really happening here is that since there are max-mount-counts and/or time dependent checks that can be used to tune a filesystem (recorded in the filesystem's superblock), that what appears to be a problem is that I am actually running into the case whereby the Fiesty Live CD mount command "acts" like the noload parameter has been given as a default behavior when the max-mount-count in the FC3 superblock is encountered.

In that case, this behavior occurs because the FC3 ext3 filesystem has not been booted for the max-mount-count number of times.

I may yet be able to trigger the condition I have observed by running a number of mount/umount sequences (23-46 should do it) to recreate it, and then check what dmesg reports.

-- Tom

---

