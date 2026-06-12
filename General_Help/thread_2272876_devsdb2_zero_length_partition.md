---
title: "/dev/sdb2 zero length partition"
date: 2015-04-09
forum: General Help
---

### Post by ELMIT on 2015-04-09
I use the partition /dev/sdb2 for my data and recently it got slower and slower. 

I tried to use:

sudo fsck.ext4 -p -f /dev/sdb2

When I came back after my meeting it was finished, without showing any errors.

After rebooting it could not find the data.

I tried again sudo fsck.ext4 -p -f /dev/sdb2 and got the answer:

fsck.ext4: Attmpt to read block from filesystem resulted in short read while trying to open /dev/sdb2
Could this be a zero-length partition?

What can I do to fix it?

---

### Post by dragonfly41 on 2015-04-09
A quick google search "read block from filesystem resulted in short read" yields this relevant thread ...

[http://ubuntuforums.org/archive/index.php/t-1245536.html](http://ubuntuforums.org/archive/index.php/t-1245536.html)

i.e. probably corrupt superblock requires repair

Here is another article I bookmarked.

[HOWTO: Repair a broken Ext4 Superblock in Ubuntu « Linux Expresso]("http://linuxexpresso.wordpress.com/2010/03/31/repair-a-broken-ext4-superblock-in-ubuntu/")

---

### Post by ELMIT on 2015-04-09
I could not manage to repair:

sudo mke2fs -n /dev/sdb2
mke2fs 1.42.9 (4-Feb-2014)
Filesystem label=
OS type: Linux
Block size=4096 (log=2)
Fragment size=4096 (log=2)
Stride=0 blocks, Stripe width=0 blocks
182099968 inodes, 728372480 blocks
36418624 blocks (5.00%) reserved for the super user
First data block=0
Maximum filesystem blocks=4294967296
22229 block groups
32768 blocks per group, 32768 fragments per group
8192 inodes per group
Superblock backups stored on blocks: 
	32768, 98304, 163840, 229376, 294912, 819200, 884736, 1605632, 2654208, 
	4096000, 7962624, 11239424, 20480000, 23887872, 71663616, 78675968, 
	102400000, 214990848, 512000000, 550731776, 644972544


I tried each Superblock, whereby up to 23887872, I get for each one:

sudo fsck.ext4 -p -f -b 23887872 /dev/sdb2
fsck.ext4: Attempt to read block from filesystem resulted in short read while trying to open /dev/sdb2
Could this be a zero-length partition?


and above:

sudo fsck.ext4 -p -f -b 71663616 /dev/sdb2
fsck.ext4: Invalid argument while trying to open /dev/sdb2
/dev/sdb2: 
The superblock could not be read or does not describe a valid ext2/ext3/ext4
filesystem.  If the device is valid and it really contains an ext2/ext3/ext4
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device>
 or
    e2fsck -b 32768 <device>


What else can I try?

---

### Post by dragonfly41 on 2015-04-09
You can next try e2fsck as suggested ..

> 
then the superblock is corrupt, and you might try running e2fsck with an alternate superblock:
e2fsck -b 8193 <device>
or
e2fsck -b 32768 <device>


however first run this .. man e2fsck .. and read

> 
Note that in general it is not safe to run e2fsck on  mounted  filesystems.  The only exception is if the -n option is specified, and -c, -l, or -L options are not specified.   However, even if it is  safe  to  do so,  the  results  printed by e2fsck are not valid if the filesystem is mounted.   If e2fsck asks whether or not you should check a  filesystem which  is mounted, the only correct answer is ``no''.  Only experts who really know what they are doing should consider answering this question in any other way.


So you should run a LiveCD or LiveUSB on an* _unmounted_* /dev/sdb2.

testdisk is another tool to explore if you need to recover data from /dev/sdb2
again through Live CD/USB on an unmounted partition /dev/sdb2

---

### Post by ELMIT on 2015-04-09
did not lead to success, ... 

Even TestDisk could not find a partition

---

### Post by dragonfly41 on 2015-04-09
Assuming that you have important data on /dev/sdb2 you should now consider creating a clone of /dev/sdb2 onto another disk (not the same one which has bad superblocks) .. then prepare to start trying to recover data from the clone (not the original faulty disk which you should keep aside).

Cloning will be your precaution against sudden total disk failure while you are playing around in data recovery.

Then with LiveUSB return to testdisk and try a "deep search" of the unmounted cloned drive (place it in an external USB enclosure).   

Also investigate photorec .. although using photorec you must be prepared to see the file hierarchy and file naming totally lost.   This can be a problem if you have many files.

Here is just old blog discussing data recovery workflow (there are many others if you search "ubuntu forensic data recovery") ... there is also a ubuntu data recovery document somewhere discussing scalpel etc.

[http://www.howtogeek.com/howto/15761/recover-data-like-a-forensics-expert-using-an-ubuntu-live-cd/](http://www.howtogeek.com/howto/15761/recover-data-like-a-forensics-expert-using-an-ubuntu-live-cd/)

Be prepared for a very long process.

Do you have any old printed dumps of your disk geometry (previous runs of testdisk)? 
If not remember to keep these paper copies for future such recovery.

[later edit]

I've just found the data recovery guide.

[https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)

---

### Post by dragonfly41 on 2015-04-09
After thought ...

did you *reboot* after each attempt to run

sudo e2fsck -b block_number /dev/sdb2

...

and why did you stop tests at block_number 23887872?

> 
Superblock backups stored on blocks: 
    32768, 98304, 163840, 229376, 294912, 819200, 884736, 1605632, 2654208, 
    4096000, 7962624, 11239424, 20480000, 23887872, 71663616, 78675968, 
    102400000, 214990848, 512000000, 550731776, 644972544

I tried each Superblock, [COLOR=#ff0000]whereby up to 23887872[/COLOR], I get for each one:

sudo fsck.ext4 -p -f -b 23887872 /dev/sdb2
fsck.ext4: Attempt to read block from filesystem resulted in short read while trying to open /dev/sdb2
Could this be a zero-length partition?



and .. from the first thread I posted ...

> 
There is a recursive hit yes to continue option with the -y option

$ sudo e2fsck -f -b 32768 -y /dev/sdb1



man e2fsck

> 
       -y     Assume an answer of `yes' to all questions; allows e2fsck to  be
              used non-interactively.  This option may not be specified at the
              same time as the -n or -p options.


---

### Post by ELMIT on 2015-04-15
No, I did not reboot after each 
sudo fsck.ext4 -p -f -b 23887872 /dev/sdb2

Should I????

> and why did you stop tests at block_number 23887872?

I did not stop, the answer changed from then on.

-y flag will only have any effect, if I can get it to work ;-(

---

