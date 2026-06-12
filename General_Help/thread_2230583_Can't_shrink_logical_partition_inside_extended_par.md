---
title: "Can't shrink logical partition inside extended partition."
date: 2014-06-20
forum: General Help
---

### Post by Bucky Ball on 2014-06-20
Hi all,

As per the title. I'm am intending to install a minimal 14.04 LTS on a Compaq 610 and trying to get the hard drive ready, but having issues.

I am typing this on my computer and am booted into the Compaq using System Rescue CD. No screenshots or long output I'm afraid. Just the crunchy bits. 

This is the setup, exactly how Gparted is reading them when booted from System Rescue (Gparted is part of the SysRes ISO, sweet):

sda1 = Extended partition: 16Gb;
[INDENT][/INDENT]sda5 = logical partition: 16Gb, 12.04 on EXT4;
sda2 = Primary partition: XP; 
sda4 = Primary partition: Unallocated (where 14.04 is going);
sda3 = Primary partition: storage

We are focusing here on sda1 and the logical partition inside it. What I'm wanting to do is shrink sda5 by 2Gb and create a /swap partition. I have no choice as this is a legacy boot and as I already have four partitions the /swap has to be inside the extended, sda1.
 
If I could achieve this seemingly straightforward task I would be good to go and install the 14.04 LTS minimal, but no. When I try to shrink sda5 by 2Gb it stops with an error and 'details' tells me:

resize2fs: New size smaller than minimum.

I've hunted high and low and yes, there are plenty of links and pages. Nothing's worked so far. I'll keep digging, but perhaps one of you good people could shed some light ... :-k

Here's hoping and thanks in advance.

---

### Post by Bucky Ball on 2014-06-20
Bit more info. I've moved the computer now, am now online and can paste from the screen. Below is the output file created by clicking the 'Save Details' button when things stop and I get the error in Gparted.

```
GParted 0.17.0

Libparted 3.1

Shrink /dev/sda5 from 14.03 GiB to 12.12 GiB  00:00:42    ( ERROR )
    	
calibrate /dev/sda5  00:00:00    ( SUCCESS )
    	
path: /dev/sda5
start: 2048
end: 29427711
size: 29425664 (14.03 GiB)
check file system on /dev/sda5 for errors and (if possible) fix them  00:00:42    ( SUCCESS )
    	
e2fsck -f -y -v -C 0 /dev/sda5
    	
Pass 1: Checking inodes, blocks, and sizes
Pass 2: Checking directory structure 
Pass 3: Checking directory connectivity 
Pass 4: Checking reference counts 
Pass 5: Checking group summary information 

831526 inodes used (90.36%, out of 920272)
676 non-contiguous files (0.1%)
628 non-contiguous directories (0.1%)
# of inodes with ind/dind/tind blocks: 0/0/0
Extent depth histogram: 758038/336
2490422 blocks used (67.71%, out of 3678208)
0 bad blocks
1 large file

615495 regular files
130660 directories
57 character device files
25 block device files
1 fifo
23 links
85276 symbolic links (73058 fast symbolic links)
3 sockets
------------
831540 files
e2fsck 1.42.8 (20-Jun-2013)
shrink file system  00:00:00    ( ERROR )
    	
resize2fs -p /dev/sda5 12712960K
    	
resize2fs 1.42.8 (20-Jun-2013)
resize2fs: New size smaller than minimum (3343567)

========================================
```

Oddly, I can shrink the partition by a mb! But not 2Gb. I'm wondering if it has anything to do with the fact I shrank sda3 to create sda4 and the patition table is now out. I have also now deleted sda4 and that is unallocated space. But I'm nowhere near the partition I'm trying to alter. :-k

As I'm running System Rescue I have access to a heap of appropriate tools, including Testdisk. Starting to wonder about running it, but rather not go there unless I have to. Thoughts?

---

### Post by sudodus on 2014-06-20
Sometimes ***fixparts*** can help in situations like yours:

Install it if it is not available in your live drive, and run it.

---

### Post by coffeecat on 2014-06-20
Could this be your problem?

[quote="Bucky Ball"]```
831526 inodes used (90.36%, out of 920272)
```[/quote]

You're trying to shrink the partition by about 14% and that will affect the size of the filesystem.

---

### Post by Bucky Ball on 2014-06-20
> **coffeecat said:**
> You're trying to shrink the partition by about 14% and that will affect the size of the filesystem.

Thanks but not quite sure I understand completely. Is there anyway around this? Further explanation, please. 14Gb partition with 9.50 used and 4.53 unused. Trying to shrink 2Gb off. Still not making much sense to me.

---

### Post by coffeecat on 2014-06-20
> **Bucky Ball said:**
> Thanks but not quite sure I understand completely. Is there anyway around this? Further explanation, please. 14Gb partition with 9.50 used and 4.53 unused. Trying to shrink 2Gb off. Still not making much sense to me.

I'm not really that knowledgeable about filesystems, but if you've used 90% of the available inodes, and only about 68% of the available space, I'd guess you have a lot (hundreds if not thousands) of small files.

---

### Post by Bucky Ball on 2014-06-20
> **coffeecat said:**
> I'm not really that knowledgeable about filesystems, but if you've used 90% of the available inodes, and only about 68% of the available space, I'd guess you have a lot (hundreds if not thousands) of small files.

Hmm, that's interesting. Wonder what they could be? Maybe I should boot from the hard drive and 'sudo apt-get clean/autoclean' and have a bit of a sniff around ... :-k

* Just thought of something ... this is my wife's computer and she NEVER cleans her email. Evolution. She's got hundreds of emails! I didn't think they were stored locally, but I'll have a look at her profile and see what I can dig up there.

---

### Post by sudodus on 2014-06-20
Maybe you should backup what is important and re-partition the whole drive to get it clean and nice. (I must admit that I don't understand the details explained by coffeecat.)

---

### Post by Bucky Ball on 2014-06-20
> **sudodus said:**
> Maybe you should backup what is important and re-partition the whole drive to get it clean and nice. (I must admit that I don't understand the details explained by coffeecat.)

Valuable stuff backed up, but your option is definitely a last resort and I will try everything before thinking about that. I just don't have the time or inclination! I'll run test disk in a minute.

The 12.04 partition I'm trying to shrink MUST remain exactly as is which would mean screwing around with Clonezilla and hours spent on something that, on paper, should be fairly straightforward. I have successfully used testdisk before so fingers crossed ...

---

### Post by Morbius1 on 2014-06-20
inodes ( index nodes ) represents filesystem objects ( files and folders ) and contains information about them. The more files you have the more inodes are used.

If I do a "df -l" and look at my older partition it shows that I'm using 33% of the available space:
> /dev/sdb2       60344404  18821088  38434932  33% /Xub1204
If I do a "df -i" it shows that I'm using 39% of the available inodes:
> Filesystem        Inodes   IUsed     IFree IUse% Mounted on
/dev/sdb2        3842048 1491608   2350440   39% /Xub1204
I'm not exactly sure how you get out of this problem without purging a whole mess of files.

---

### Post by Bucky Ball on 2014-06-20
> **Morbius1 said:**
> :

I'm not exactly sure how you get out of this problem without purging a whole mess of files.

That's what I'm thinking, and I've come up with an idea. 

The /music folder on sda5 is fully backed up and there's hundreds of songs in there = files. If I delete the /music folder from sda5, effectively 'purging a whole mess of files', then try again? 

If that works and I can then create the /swap in the extended partition, I can put the /music folder back on sda5 when I'm done? Am I then going to get a 'not enough disk space' type error message when I attempt to put the music files/folder back on sda5 or will it 'cram the data in somehow!'?

---

### Post by Morbius1 on 2014-06-20
I honestly don't know but I don't think that will work. If you decrease the partition size you will also decrease the available inodes so you may end up with an out of space error when you try to copy /music back even though there is space available. 

Can you move the /music folder to sda3 assuming it has available space ( and inodes ) and then symlink back to sda5?

---

### Post by Bucky Ball on 2014-06-20
> **Morbius1 said:**
> 
Can you move the /music folder to sda3 assuming it has available space ( and inodes ) and then symlink back to sda5?

Ha! My mistake. That is exactly how I have it set up already. Like I said, it's my wife's computer, we have a few, and I forget! That is my usual set-up, though (with about four installs symlinked to the same folders on my computer ... ;)).

So, forget moving the /music folder anywhere, already on sda3. Back to the drawing board. Testdisk must be the direction to go next. Unless I can find what all those files are.

I repeat, I only want to shrink the sda5 partition by 2Gb which will leave it plenty of headroom (well, 2.5Gb anyway). I did a clean up on sda5 about two weeks ago and freed up about 4Gb.

---

### Post by sudodus on 2014-06-20
> **Bucky Ball said:**
> Valuable stuff backed up, but your option is definitely a last resort and I will try everything before thinking about that. I just don't have the time or inclination! I'll run test disk in a minute.

The 12.04 partition I'm trying to shrink MUST remain exactly as is which would mean screwing around with Clonezilla and hours spent on something that, on paper, should be fairly straightforward. I have successfully used testdisk before so fingers crossed ...

Often it is enough to keep files and directories (and their permissions) in a linux partition for it to work after moving, restoring etc. This makes it possible to backup and restore via rsync or tar (also a compressed tarball). Tarballs are what I use in the [One Button Installer]("https://help.ubuntu.com/community/OBI") using the portability of Ubuntu flavour systems. So unless you have something very special, the 12.04 partition must *not* remain exactly as is.

If you move the head end of the partition you have to reinstall the bootloader, but otherwise it will work. You can even use the One Button Installer to make a tarball and later on reinstall it.

---

### Post by Bucky Ball on 2014-06-21
Sorry for not reporting back sooner, but I finally got it installed.

The original setup was this:

sda1 = Extended partition: 16Gb;
sda5 = logical partition: 16Gb, 12.04 on EXT4;
sda2 = Primary partition: XP;
sda4 = Primary partition: Unallocated (where 14.04 is going);
sda3 = Primary partition: storage

I killed XP, the path of least resistance and easiest because there is nothing to save there; it is used for one game. I then shrank sda3 leaving 30Gb free space. I then expanded the extended partition until there was 15Gb free space left between it and sda3, whacked a 15Gb logical partition and a 2Gb /swap partition inside the extended partition and installed 14.04. That now leaves the 15Gb free space between the extended partition and sda3  for XP on a primary partition. Sweet. But before that can happen ...

I am having problems logging in to the 14.04 install, nothing to do with this, but outlined here:

[http://ubuntuforums.org/showthread.php?t=2230872](http://ubuntuforums.org/showthread.php?t=2230872)

So thanks for your help, thoughts and ideas, everyone, but let's now consider this part of the journey resolved as we're moving onward and upward! Solved.

* Just for clarity, it now looks like:

sda1 = Extended partition: 16Gb;
sda5 = logical partition: 16Gb, 12.04 on EXT4;
sda6 = logical partition: 16Gb, 14.04 on EXT4;
sda7 = logical partition: 2Gb, /swap;
sda2 = Primary partition: XP;
sda3 = Primary partition: storage

Done and everything working fine. ;)

---

