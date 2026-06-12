---
title: "[SOLVED] Help: recovering lost partition"
date: 2007-08-30
forum: General Help
---

### Post by xavier_r on 2007-08-30
I was trying to dual boot Mac OS X and Ubuntu
But Mac wouldnt boot because GRUB was still in MBR
So i planned to install rEFIt after overwriting MBR

fdisk -u would have done it
But by mistake I typed
fdisk -i

Here's what fdisk looks like in Mac
```

fdisk:
        -i: initialize disk with new MBR
        -u: update MBR code, preserve partition table
```

So my partition tables are now gone

When I booted using GParted Live CD
it recognized filesystem as HFS
But when I boot from UBUNTU LiveCD and ran cfdisk, it still showed a Linux partition

So the data might be out there
There is so much in there including some precious memories :(

I tried TestDisk for Mac OS, and am not getting results...
Maybe I am not using it correctly...

Any kind of help would be greatly appreciated...
I am in a mess now...


Here's my partition map, using rEFIt partition analyser...
> 
*** Report for internal hard disk ***

Current GPT partition table:
 No GPT partition table present!

Current MBR partition table:
 # A    Start LBA      End LBA  Type
 1             63     59038874  83  Linux
 2 *     59038875     75505499  af  Mac OS X HFS+
 3       75505500     78156224  82  Linux swap / Solaris

MBR contents:
 Boot Code: Unknown, but bootable

Partition at LBA 63:
 Boot Code: None
 File System: HFS Extended (HFS+)
 Listed in MBR as partition 1, type 83  Linux

Partition at LBA 59038875:
 Boot Code: Unknown, but bootable
 File System: HFS Extended (HFS+)
 Listed in MBR as partition 2, type af  Mac OS X HFS+, active

Partition at LBA 75505500:
 Boot Code: None
 File System: Unknown
 Listed in MBR as partition 3, type 82  Linux swap / Solaris


---

### Post by splintercellguy on 2007-08-30
Use TestDisk from Linux System Rescue CD or Ubuntu LiveCD. Do not continue doing any r/w with your HDD.

---

### Post by xavier_r on 2007-08-30
Here's what I did...

Hi I used TestDisk from Mac OS X
And I searched for superblock backups
I got the superblock number and block size using TestDisk

Next I booted using GParted LiveCD
and repaired the filesystem using command

$ fcsk.ext3 -y -b block_no -B block_size /dev/hda1

I put the same arguments as I got from TestDisk...
So this time I started GParted and its showing used space in first partition (last time it was blank)

Now what? How to recover the data
GRUB says it cant find /boot/grub/stage1

---

### Post by xavier_r on 2007-08-30
Anyone please...
I am stuck... I haven't done anything with my computer for two days now...

---

### Post by xavier_r on 2007-08-30
I think I should post this somewhere else...

---

### Post by southernman on 2007-08-30
If I remember right, using testdisk you would want to select the advanced option after it's scanned the drive and found partitions. Selecting one of the partions you can press p which will show you a list of files it sees on that partition and I think c will copy the files for you.

Still, you should be able to solve this by just reinstalling grub... no?(edited) maybe not! duh!

---

### Post by rebelDNS on 2007-08-31
> **xavier_r said:**
> Here's what I did...

Hi I used TestDisk from Mac OS X
And I searched for superblock backups
I got the superblock number and block size using TestDisk

Next I booted using GParted LiveCD
and repaired the filesystem using command

$ fcsk.ext3 -y -b block_no -B block_size /dev/hda1

I put the same arguments as I got from TestDisk...

I tried to same thing with the results i got, I even tried supposed locations of "backup superblocks" but keep getting

"Bad magic number in superblock"

I tried it again with 8193, 32768 and all the other supposed places of "backup ext3 superblocks" but get the same thing.  Can anyone help?

---

### Post by gtdaqua on 2007-08-31
You could try Hiren's Boot CD which will recover any partition (NTFS, Ext) etc. There are quite a few partition recovery tools built on to that CD. I have recovered accidentally deleted partitions from several servers. 

You can get this easily from Torrents. Just dont panic. Dont do any read/write activity until you get a solid recovery tool. The latest version Hiren's Boot CD 9.2.

I am sure recovering is easy. But not sure about configuring GRUB entries to reflect the recovered partitions. If data is what u want, then there is no reason to worry.

---

### Post by xavier_r on 2007-08-31
> **southernman said:**
> If I remember right, using testdisk you would want to select the advanced option after it's scanned the drive and found partitions. Selecting one of the partions you can press p which will show you a list of files it sees on that partition and I think c will copy the files for you.


Pressing P shows only lost+found directory :(

---

### Post by southernman on 2007-08-31
That doesn't sound good. Look into using the tool suggested in post number 8 and also look into using ddrhelp. I've not used either of those as testdisk always served my purpose well.

Wish I had good news, but it really doesn't look good if testdisk only shows the lost+found directory. Sorry!

Don't do anything rash until you've looked into other recovery methods though... ok.

Good Luck xavier_r

Let me know what transpires from this.

---

### Post by xavier_r on 2007-08-31
Thanks southernman
Your wishes brought some good news ;)

I looked into lost+found after mounting /dev/hda1 using Gparted LiveCD and found a lot of hashed files
Next I booted using Mac OS X and using TesDisk I could see those files too
And when I looked inside those hashed files, Voila !!!!
All my files are there, althought very randomly placed
I think, fsck.ext3 did the trick
Yay...:lol:

Now all that is needed to do is to burn those files on a DVD backup
How do i do that? Can I burn DVDs from LiveCD?
Or else, how do I mount ext2fs on Mac OS X 10.4.3?

---

### Post by southernman on 2007-08-31
Very good news xavier_r... indeed!

As for buring to dvd using a livecd. I can't help you with that one. I would suggest if you have a spare drive you can plug into the system, to copy the files onto it, install ubuntu to the original drive and then burn them from there. I am pretty sure there is a way to burn them from a livecd, just don't have that task under my belt as of yet.

However (always a butt, isn't there) seeing as they are all in the lost+found directory, it could be that they were broken when placed in there. This is where ddrhelp may be just the tool you need as I've read that it can copy files byte by byte... or something to that effect. Again, I can't tell you how to use that program as I've only used testdisk and mostly for recovering files from dead hard drives. Hence another reason I suggest looking into (read- learning how to use) ddrhelp in your particular situation. For the simple fact I think you had some file system corruption take place. You could still copy the files to another disk mind you, just don't install or write anything to the disk in question until you are certain that the integrity of the old files are in tact.

Really glad you found them! Hopefully there in good shape. My grandmother used to tell me, "prepare for the worst and hope for the best." *sighs*

---

### Post by gtdaqua on 2007-08-31
I am really glad u got it now. See? just a little bit of playing around and you will get it!!

---

### Post by xavier_r on 2007-08-31
Thanks u guys :)

Here's my plan on what I intend to do
Since I cannot mount ext2 filesystem on Mac OS X(/dev/hda2)
I am going to install UBUNTU on /dev/hda2, leaving /dev/hda1(original UBUNTU drive) untouched

When I boot using UBUNTU, I guess I can access files from /dev/hda1 directly
and then I can write from there...

Should i follow this route?

---

### Post by tact on 2007-08-31
I would be DEAD careful about writing ANYTHING to that disk until you have ALL the files you want off it.

I had a situation with my office laptop - WinXP refused to boot and all the windows based recovery disks, BartPE, and the rest just saw the HDD as "unpartitioned space"  -   I had too much stuff on there (not backed up!) that i didnt want to lose...  in desperation I booted a ubuntu desktop LiveCD (back then it was Edgy)...

Fortunately Edgy could see the old NTFS partition and I could mount it and read the files off it while booted to the LiveCD.  The liveCD also let me connect to my corporate LAN and access a windows fileserver shares!    So -  booted from liveCD I could copy all my precious data across the LAN to the fileserver.

I could even surf the web and access corporate exchange server email via OWA...

I'd recommend you try the rescue while booted from a liveCD ...  once your files are safe see if you can install a bootable OS and still not destroy whats on the HDD.   You might be lucky there. :)

---

### Post by southernman on 2007-08-31
To be safe xavier_r, I wouldn't. Not without solid proof from someone else who knows for sure it would be safe. It should be ok, but the expense you've paid to this point, I wouldn't risk it without concrete proof.

What you should do *IMO* if you have enough room on that harddrive is setup hda2 if not already done so, and copy the files from hda1 into there.

Let's rescue that data first, and then you can install. I still wish you had a backup hard drive that you could install to after recovering the files... if nothing but a temporary installation on an older 4, 10, 20GB hdd.

I'll be retiring soon but will try to hang on a little while longer to see what you can/can't do from here.

---

### Post by xavier_r on 2007-08-31
Hey guys, I just wanted to tell that all my data has been found ok...
Only a Music folder with some 4-5 songs is gone, but thats ok...
Most important some precious photos have been found in proper shape...

I installed a fresh version UBUNTU 7.04 on the Mac partition (/dev/hda2) and now can access /dev/hda1 from there

Moreover now, I dont have to write any stuff on a DVD backup...
Because I can now access files from my UBUNTU,,,

It looks like nothing has changed...
The thing i learned is you need to take time a lot of time in situations like these...
And not do anything without knowing...
Thanks for the support guys :)
I'll mark this thread as solved

---

### Post by southernman on 2007-09-03
Hey xavier_r - glad you got them in tact... glad to have been able to offer* some* assistance.

---

