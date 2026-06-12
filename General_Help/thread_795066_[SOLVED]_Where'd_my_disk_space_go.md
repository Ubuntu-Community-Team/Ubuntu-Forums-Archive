---
title: "[SOLVED] Where'd my disk space go?"
date: 2008-05-15
forum: General Help
---

### Post by fyo on 2008-05-15
OK, so I ran out of disk space the other day and started deleting files. After deleting several gigs worth of stuff, "df" still claimed nothing was available (and error messages abounded if I tried creating or copying a file).

Several gigs later, a few hundred megabytes were available.

What the heck is happening to my disk space?

I tried rebooting, I tried everything I could think of and nothing makes any difference. When I do a df, this is what's shown:

/dev/sda2             234G  226G  898M 100% /

Now, my math skills are pretty good, but even if they weren't I would probably still be able to see that something doesn't add up here. 234G total, 226G used, but less than 1 available. OK, so where's the missing disk space?

GParted shows 8GB unused space on sda2.

For fun, I tried resizing sda2, creating a new partition with the unused 8GB. That worked just fine and the new partition did indeed have 8GB free.

Can anyone tell me wtf is going on? This is getting really annoying.

---

### Post by mattiast on 2008-05-15
I had a similar problem in Gutsy, when emptying the trashcan in Nautilus didn't really empying in.. so I had to use the trashcan at the rightbottom on the screen, the bottom panel, then I got all the disk space back again .. very strange problem...

---

### Post by prshah on 2008-05-15
> **fyo said:**
> OK, so I ran out of disk space the other day and started deleting files. After deleting several gigs worth of stuff, "df" 
Can anyone tell me wtf is going on? This is getting really annoying.

Looks like you're running out of inodes; check the output of ```
df -i
```

You get only a limited number of inodes (usually 1%) which store information about files and directories. Having lots of tiny files and/or heavily nested directories will eat up inodes.

I believe you can change the default inode allocation; but I've never found the need for it and can't really tell you how.

---

### Post by Wandering on 2008-05-15
Free space is always significantly less than disk space minus used space because of a number of bookeeping issues and sparse storage. There is an equivalent to checkdisk in Ubuntu, and it would be good to run it. It should run automatically every 37 boots unless you disabled it. 

Remember, deleting a small file only leaves a small place to put another file, and many small files scattered across the disk when deleted free a large space, but not all in one piece, and so with limited usefulness.

Good luck.

---

### Post by unutbu on 2008-05-15
Please post 
```
sudo tune2fs -l /dev/sda2
```

From the tune2fs man page:

```
-m reserved-blocks-percentage
   Set the percentage of the filesystem which may only be allocated by priv&#8208;
   ileged processes.   Reserving some number of filesystem blocks for use by
   privileged processes is done to avoid filesystem  fragmentation,  and  to
   allow  system  daemons,  such as syslogd(8), to continue to function cor&#8208;
   rectly after non-privileged processes are prevented from writing  to  the
   filesystem.  Normally, the default percentage of reserved blocks is 5%.
```

I think it is a little silly that the percentage is set at 5% since 5% could be measly on a small disk and ridiculously large on a huge disk. On your 234GB disk, 5% would be almost 12GB for stuff like syslogd. (Run `du -sh /var/log` to see how big /var/log is. syslogd writes there.) I'm no expert, but 12GB seems excessive to me.

If you want to reduce the amount of reserved space to say 1%, you can run

```
sudo tune2fs -m1 /dev/sda2
```

---

### Post by fyo on 2008-05-15
inodes: I'm using 411k of 31M inodes.

checkdisk: I already ran "e2fsck -f -v" on it and no problems were detected.

bookkeeping and sparse storage: Last one first... "sparse" storage refers to files only taking up what they actually contain and not the fully allocated amount. This is not supported on all file systems, but is on ext3, which is what I use.

I do have a bunch of "sparse" files and I certainly realize that if I delete a sparse file which claims to contain, say, 1GB, only whatever space is actually allocated to that file will be released.

None of the files I deleted to get more space were sparse files and I don't see how the issue would affect the output of "df" (total-avail >> free).

Note that I'm also well aware of the "du" command and the total usage reported by it matches that of "df" quite well.

For the hell of it, I tried giving the ubuntu partition half my swap partition. The result was 400MB more free disk space on the ubuntu partition after getting half my 8GB swap partition. Looks like I just lost another 4GB to the beast...

Anyhooo.... I just noticed another thing. I previously saved the output of df and noticed a strange discrepancy. The total size of sda2 (the ubuntu partition) used to be reported as 247GB. After feeding it MORE space from other partitions, the total size is now reported as 234GB.

WTF?

---

### Post by fyo on 2008-05-15
> **unutbu said:**
> Please post 
```
sudo tune2fs -l /dev/sda2
```


```

$ sudo tune2fs -l /dev/sda2
tune2fs 1.40.8 (13-Mar-2008)
Filesystem volume name:   <none>
Last mounted on:          <not available>
Filesystem UUID:          4c924613-ac6b-4dc7-af2e-2a8734f0f820
Filesystem magic number:  0xEF53
Filesystem revision #:    1 (dynamic)
Filesystem features:      has_journal resize_inode dir_index filetype needs_recovery sparse_super large_file
Filesystem flags:         signed_directory_hash 
Default mount options:    (none)
Filesystem state:         clean
Errors behavior:          Continue
Filesystem OS type:       Linux
Inode count:              31145984
Block count:              62291968
Reserved block count:     1868757
Free blocks:              4753315
Free inodes:              30735049
First block:              0
Block size:               4096
Fragment size:            4096
Reserved GDT blocks:      1009
Blocks per group:         32768
Fragments per group:      32768
Inodes per group:         16384
Inode blocks per group:   512
Filesystem created:       Thu Aug  2 13:13:43 2007
Last mount time:          Thu May 15 14:59:37 2008
Last write time:          Thu May 15 14:59:37 2008
Mount count:              2
Maximum mount count:      36
Last checked:             Thu May 15 14:24:02 2008
Check interval:           15552000 (6 months)
Next check after:         Tue Nov 11 13:24:02 2008
Reserved blocks uid:      0 (user root)
Reserved blocks gid:      0 (group root)
First inode:              11
Inode size:		  128
Journal inode:            8
First orphan inode:       26689673
Default directory hash:   tea
Directory Hash Seed:      b987c31f-5baa-43ed-86df-f74b5e615d51
Journal backup:           inode blocks
```

1.8M reserved blocks x 4k block size = 7GB reserved space.

Hmm... this could go some ways to explaining the initial issue.

When I originally ran out of disk space, I was transferring some video from a DV camera over firewire. Now, by default in Ubuntu, accessing firewire requires the use of sudo (yes, I realize that adding a dedicated user for the device would probably be the right way to do it, but I was lazy and did it the default Ubuntu way), so I probably gobbled this reserved space right up with my root process...

Still... I'm MISSING quite a chunk of disk space since before this whole debacle. As reported in my previous post, the total size of sda2 as reported by df has dropped by 13GB despited having been "fed" 4GB from my swap partition.

Worryingly, the total space reported by df matches the total space calculated from the total block count in the output above (234GB vs 237GB).

GParted currently reports sda2 as beign 254.79GiB (with 18.13GiB unused). "df" claims 234GB total size and 12GB available (yes, I freed up a bunch of more space). This is weird on a number of levels:

- Why is the total size as reported by df so much lower than that reported by GParted?
- Why is df unable to do math? It reports the following when NOT specifying -h (human readable):

total size: 245258456
used: 226245676
available: 11537752

And the following when -h is specified:

total size: 234GB
used: 216GB
available: 12GB

Now, the first two sizes (total and used) are correctly calculated (with proper rounding, even). But the "available" space is off by a gigabyte (it should be 11.00GB, which cannot be rounded to 12GB).

Still, my main concern now is the 13GB or so that I'm just plain missing since before this whole mess started. Space that's simply disappeared from the size reported by df, despite having increased the size of the partition.

Any chance GParted f*cked (fscked?) by disk?

---

### Post by unutbu on 2008-05-15
GParted measures the size of the partition,
`df` measures the size of the filesystem that has been formated onto the partition.
A file system needs to record superblocks which store the structure of the filesystem. Ext3 is also a journaled filesystem and the journaling takes up space too. 

GParted reports sda2 as 254.79 GiB = 254.79 * 10^9 / 2^30 = 237.3 GB.
`df` reports 234GB. The difference is 3.3GB. This, apparently, is the amount of space ext3 reserves to manage the filesystem structure.

`df` reports 
total=245258456 1K-blocks.
used=226245676 1K-blocks.

total-used = 19012780 1K-blocks.

`df` reports available=11537752 1K-blocks.

The discrepancy = (total-used)-available = 19012780-11537752 = 7475028 1K-blocks.

tune2fs reports reserved blocks = 1868757 4K-blocks. That equals 1868757*4 = 7475028 1K-blocks. 

So the "discrepancy" is really just the reserved blocks. `df` output is unintuitive, but correct when properly interpreted.

Now putting all this aside, you say `df -h` reported sda2 started out with 247GB. I have no idea how that could have changed to 234GB.

I hope the above explanation, however, makes you a bit more comfortable believing the output reported by both gparted and df. If so, then you can look at the size of each of your partitions as reported by gparted, add that up and see if it agrees with the reported size of your hard drive. It you get agreement then at least, in some sense, you'll know you're not missing 13GB.

---

### Post by ekp on 2008-05-15
> **unutbu said:**
> GParted measures the size of the partition,
`df` measures the size of the filesystem that has been formated onto the partition.
A file system needs to record superblocks which store the structure of the filesystem. Ext3 is also a journaled filesystem and the journaling takes up space too. 

GParted reports sda2 as 254.79 GiB = 254.79 * 10^9 / 2^30 = 237.3 GB.
`df` reports 234GB. The difference is 3.3GB. This, apparently, is the amount of space ext3 reserves to manage the filesystem structure.

`df` reports 
total=245258456 1K-blocks.
used=226245676 1K-blocks.

total-used = 19012780 1K-blocks.

`df` reports available=11537752 1K-blocks.

The discrepancy = (total-used)-available = 19012780-11537752 = 7475028 1K-blocks.

tune2fs reports reserved blocks = 1868757 4K-blocks. That equals 1868757*4 = 7475028 1K-blocks. 

So the "discrepancy" is really just the reserved blocks. `df` output is unintuitive, but correct when properly interpreted.

Now putting all this aside, you say `df -h` reported sda2 started out with 247GB. I have no idea how that could have changed to 234GB.

I hope the above explanation, however, makes you a bit more comfortable believing the output reported by both gparted and df. If so, then you can look at the size of each of your partitions as reported by gparted, add that up and see if it agrees with the reported size of your hard drive. It you get agreement then at least, in some sense, you'll know you're not missing 13GB.

I am reading from your post that there is not really any lost space on hard drive.  Just semantics of how it is determined.  I will admit to skimming your reply for an answer to my problem.  I also have lost free space over night.  Not perceived but real disk space.  I am seeing only 300 megs of free space.  I deleted an iso of over 600 megs and still do not get any more free space.  My system is running funky for lack of disk space and I can not download anything for lack of space. 

> code
ed@ed-desktop:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1             7.5G  7.1G     0 100% /
varrun                379M  116K  379M   1% /var/run
varlock               379M     0  379M   0% /var/lock
udev                  379M   64K  379M   1% /dev
devshm                379M   52K  379M   1% /dev/shm
lrm                   379M   38M  342M  10% /lib/modules/2.6.24-16-generic/volatile
df: `/home/ed/.gvfs': Transport endpoint is not connected
/dev/sdb1             978M  607M  371M  63% /media/disk







---

### Post by fyo on 2008-05-15
> **unutbu said:**
> GParted reports sda2 as 254.79 GiB = 254.79 * 10^9 / 2^30 = 237.3 GB.

That's incorrect, unfortunately.

GiB is gibibyte, aka "binary gigabyte", with the "i" added to distinguish it from the standard decimal/SI giga "G" prefix.

Both GParted and df report values in "binary gigabytes" (1024^3).

This is also evident from GParted's report of the number of sectors used for sda2 (534.34 million at 0.5kB each = 254.79GB).

---

### Post by fyo on 2008-05-15
> **ekp said:**
> I am reading from your post that there is not really any lost space on hard drive.  Just semantics of how it is determined.  I will admit to skimming your reply for an answer to my problem.  I also have lost free space over night.  Not perceived but real disk space.  I am seeing only 300 megs of free space.  I deleted an iso of over 600 megs and still do not get any more free space.  My system is running funky for lack of disk space and I can not download anything for lack of space.

Skimming is dangerous ;-).

I am, actually, missing REAL disk space.

I'm not sure you are, however. You might be suffering from one of the things I was also suffering from: Reserved Blocks. The filesystem reserves 5% of disk space by default. This space can only be accessed by a privileged user. That allows "core" functions to continue (for a while) even after user accessible space is used up. Now, if you had something running with sudo, that process could have used up some of that 5% extra space. In essence, as a user, you would have negative space available (even though df and the like would only show 0). The result is that when you delete something, the freed space first goes towards restoring the 5% reserved space. See *unutbu*'s reply to me in this thread for more info.

---

### Post by unutbu on 2008-05-15
Run 

```
resize2fs /dev/sda2
```

From the resize2fs man page:

>  The  size  of  the
       filesystem  may never be larger than the size of the partition.  If size parame&#8208;
       ter is not specified, it will default to the size of the partition.

The wording of the first sentence implies that it is possible for the size of a filesystem to be smaller than the size of a partition. I think that's what happened to you.

I agree with you that I was mistaken: 1GiB = 2^30 bytes. However, after studying my own system and doing some googling, I believe the gist of my previous post is correct. There is a difference between the sizes GParted and df are going to report because GParted reports the size of the partition and df reports the size of the filesystem. Even after you run resize2fs, the sizes will differ.

See [http://www.mail-archive.com/debian-user@lists.debian.org/msg85494.html](http://www.mail-archive.com/debian-user@lists.debian.org/msg85494.html)

---

### Post by fyo on 2008-05-16
> **unutbu said:**
> Run 

```
resize2fs /dev/sda2
```


THANK YOU! That did it:

```

/dev/sda2             251G  216G   28G  89% /

```

Apparently, what happens is that gparted does not resize the filesystem when the partition is resized. That resulted in my *filesystem* becoming smaller since in one of the steps I split off the end of my /dev/sda2, creating a new partition. When I merged the partition back at a later point, the partition size of /dev/sda2 returned to what it was (plus the 4GB from the swap that I had also added), but the filesystem size stayed the same (as the smallest size the partition had been).

I'm not sure why gparted didn't run resize2fs... that would seem to be a logical thing to do. Anyway, it was an old version of gparted from an old Ubuntu CD I had lying around.

So, I learned two things from this:

- Use resize2fs to make sure the filesystem is taking up all the space on the partition.
- Reserved Blocks, the existence of which I was not even aware of, do not show as available (free) space and can only be used by a privileged process. tune2fs can be used to adjust the percentage of reserved blocks (default is 5%).

Marking this one as well and truly solved.

---

### Post by ekp on 2008-05-18
> **fyo said:**
> Skimming is dangerous ;-).

I am, actually, missing REAL disk space.

I'm not sure you are, however. You might be suffering from one of the things I was also suffering from: Reserved Blocks. The filesystem reserves 5% of disk space by default. This space can only be accessed by a privileged user. That allows "core" functions to continue (for a while) even after user accessible space is used up. Now, if you had something running with sudo, that process could have used up some of that 5% extra space. In essence, as a user, you would have negative space available (even though df and the like would only show 0). The result is that when you delete something, the freed space first goes towards restoring the 5% reserved space. See *unutbu*'s reply to me in this thread for more info.

I believe you are correct.  I reinstalled and I am seeing a smaller amount of reserved blocks.  With time and use of sudo I will loose more space for this.  How do I prevent that from happening?  I have run many distros and this is the first time I have run into anything like this.

---

### Post by unutbu on 2008-05-18
Hi ekp, the reserved blocks are set aside when the filesystem is formatted. It is a fixed amount and you shouldn't lose any more space as time goes on. 

I think when your disk is not near "full capacity" commands run as root consume regular space -- it does not go for the reserved blocks. By "full capacity" I mean that from the point of view of a regular user, not counting reserved blocks.

When your disk is near "full capacity" the reserved blocks are available only to root so that root can still function a little longer while regular users feel the pinch. This is an early warning system -- you as a regular user will realize there is a problem, and you as root still have some space (so the computer doesn't completely lock up) so you can fix the problem (by deleting stuff).

Every ext2/ext3 filesystem you've ever had came with reserved blocks. You just might not have been aware of this.

See my previous post regarding tune2fs if you want to change the number of reserved blocks.

---

