---
title: "[SOLVED] corrupted partition(need to recover)"
date: 2008-06-11
forum: General Help
---

### Post by Ender305 on 2008-06-11
I need to recover an encrypted ext3 partition, it tries to automount it during boot(its the /home partition) but it gives me an error about a bad superblock, I used the normal parameters when I made the partition so I need to know where the backup superblock is and if that doesn't work, maybe some more advanced recovery methods

---

### Post by HalPomeranz on 2008-06-12
Before I begin, let me say that I don't have any actual hands-on experience with encrypted ext3 file systems.  I'm not totally certain what I'm telling you applies in this case, but it does work for non-encrypted volumes.

From the e2fsck manual page:

```

       -b superblock
              Instead of using  the  normal  superblock,  use  an  alternative
              superblock  specified  by  superblock.   This option is normally
              used when the primary superblock has been corrupted.  The  loca&#8208;
              tion  of  the backup superblock is dependent on the filesystem’s
              blocksize.   For  filesystems  with  1k  blocksizes,  a   backup
              superblock  can  be found at block 8193; for filesystems with 2k
              blocksizes, at block 16384; and  for  4k  blocksizes,  at  block
              32768.

              Additional  backup  superblocks  can  be determined by using the
              mke2fs program using the  -n  option  to  print  out  where  the
              superblocks were created.   The -b option to mke2fs, which spec&#8208;
              ifies blocksize of the filesystem must be specified in order for
              the superblock locations that are printed out to be accurate.

              If  an alternative superblock is specified and the filesystem is
              not opened read-only, e2fsck will make  sure  that  the  primary
              superblock  is  updated  appropriately  upon  completion  of the
              filesystem check.

```

The comment about using "mkfs -n" means you can do something like:

```

$ **sudo mkfs -n /dev/sdd1**
mke2fs 1.40.8 (13-Mar-2008)
Filesystem label=
OS type: Linux
Block size=4096 (log=2)
Fragment size=4096 (log=2)
9773056 inodes, 39072080 blocks
1953604 blocks (5.00%) reserved for the super user
First data block=0
Maximum filesystem blocks=4294967296
1193 block groups
32768 blocks per group, 32768 fragments per group
8192 inodes per group
Superblock backups stored on blocks: 
	32768, 98304, 163840, 229376, 294912, 819200, 884736, 1605632, 2654208, 
	4096000, 7962624, 11239424, 20480000, 23887872

```

Notice that the last couple lines of output show you where all the superblock backups should be.  You can use these numbers with "fsck -b ...".

It is ***ABSOLUTELY VITAL*** that you include the "-n" option, which means "show me what you would do, but don't actually create a new file system".  Otherwise you'll end up blowing away all your data!  Substitute the name of your partition for "/dev/sdd1" in the above example.

---

### Post by Ender305 on 2008-06-12
ok, I tried that and finally found a valid superblock, I tried to run fsck but I got a lot of errors, here's what I got

```
root@echo419:/# e2fsck -b 294912 /dev/sda5
e2fsck 1.40.2 (12-Jul-2007)
Superblock has an invalid ext3 journal (inode 8).
Clear<y>? yes

*** ext3 journal has been deleted - filesystem is now ext2 only ***

Resize inode not valid.  Recreate<y>? yes

/dev/sda5 was not cleanly unmounted, check forced.
e2fsck: Illegal triply indirect block found while reading bad blocks inode
This doesn't bode well, but we'll try to go on...
Pass 1: Checking inodes, blocks, and sizes
Bad block inode has illegal block(s).  Clear<y>? no

Illegal block #0 (3964639546) in bad block inode.  IGNORED.
Illegal block #1 (1673600430) in bad block inode.  IGNORED.
Illegal block #2 (2328476011) in bad block inode.  IGNORED.
Illegal block #3 (2762639274) in bad block inode.  IGNORED.
Illegal block #4 (409569702) in bad block inode.  IGNORED.
Illegal block #5 (3816775671) in bad block inode.  IGNORED.
Illegal block #6 (1488741223) in bad block inode.  IGNORED.
Illegal block #7 (32189806) in bad block inode.  IGNORED.
Illegal block #8 (2851085601) in bad block inode.  IGNORED.
Illegal block #9 (3503483399) in bad block inode.  IGNORED.
Illegal block #10 (3616690042) in bad block inode.  IGNORED.
Illegal block #11 (3013845196) in bad block inode.  IGNORED.
Illegal block #-1 (3752925249) in bad block inode.  IGNORED.
Illegal block #-2 (262176290) in bad block inode.  IGNORED.
Illegal block #-3 (2538493338) in bad block inode.  IGNORED.
Error while iterating over blocks in inode 1: Illegal triply indirect block found
Recreate journal to make the filesystem ext3 again?
Fix<y>? yes

Creating journal (32768 blocks): Error : File exists 
        while trying to create journal
e2fsck: aborted

```

I didn't keep going because I didn't want to lose any data, do you think the errors are because of the encryption or have the files been corrupted

---

### Post by HalPomeranz on 2008-06-12
> **Ender305 said:**
> do you think the errors are because of the encryption or have the files been corrupted

How exactly did you create the encrypted file system?  Are you using the built-in cryptloop stuff in the kernel, or are you using some extra package like Truecrypt, or perhaps an encrypting hard drive?  Are you doing full disk encryption, encrypting on a partition-by-partition basis, or creating an encrypted volume within an existing (non-encrypted) partition?

---

### Post by Ender305 on 2008-06-12
It uses cryptoloop and its encrypted on the partition level; I encrypted the partition using the standard encryption options in the alternate install cd.

---

### Post by HalPomeranz on 2008-06-12
> **Ender305 said:**
> It uses cryptoloop and its encrypted on the partition level; I encrypted the partition using the standard encryption options in the alternate install cd.

Then I would speculate that the problems you were having with fsck were due to the encryption.  I assume fsck was trying to treat the partition as an unencrypted volume and of course the superblocks, inodes, etc wouldn't be readable because they were encrypted.

Again, because I don't have a lot of experience with the built-in Linux disk encryption technology, I'm not sure how to advise you.  For you to be able to fsck the file system, you'd have to get to the point where fsck can see the decrypted file system image.  I'm not sure how to do that without mounting the volume (which of course you probably can't do because the file system is corrupted).

What's the state of your backups of the data in this partition?  :(

---

### Post by Ender305 on 2008-06-12
haha, if the superblocks are encrypted, why was I able to find a valid backup superblock? the chances of that happening at random are approximately zero

---

### Post by HalPomeranz on 2008-06-12
> **Ender305 said:**
> haha, if the superblocks are encrypted, why was I able to find a valid backup superblock? the chances of that happening at random are approximately zero

Mmmm, yeah.  Unencrypted superblocks but encrypted data/inodes?  Seems possible because the kernel would need to look at the superblocks to identify the type of file system.  I'm just not clear on the technical implementation details.

---

### Post by Ender305 on 2008-06-12
this is kinda like a Catch 22, I have to mount the partition so its unencrypted and I can check it, but I cant mount it because its corrupter and I need to check it, there must be some way around this though

---

### Post by Herman on 2008-06-13
I'm new at working with encrypted file systems too, but I have these two links which I hope might be helpful,  [Running fsck on a LUKS encrypted partition in LVM]("http://iquaid.org/2008/03/04/running-fsck-on-a-luks-encrypted-partition-in-lvm/"), and [Rescue an encrypted LUKS LVM volume]("http://www.ubuntugeek.com/rescue-an-encrypted-luks-lvm-volume.html").
The first link looks as if it could be more applicable to Red Hat Linux, but it is about the subject of this thread.
The second link is applicable to Ubuntu, but it's more about mounting, whch is different from what we're trying to do, but maybe the first half of it will be of some use.
I hope some combination of the two will get the job done.

---

### Post by Ender305 on 2008-06-13
do you know if clearing the journal or recreating the inode was a bad idea, I'm worried that might have caused even more problems

---

### Post by Ender305 on 2008-06-13
it looks like running the fsck the first time worked, when I mounted it using  those instructions, it was fine, I didn't need to check it

---

