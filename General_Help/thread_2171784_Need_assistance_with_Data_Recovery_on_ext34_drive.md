---
title: "Need assistance with Data Recovery on ext3/4 drive"
date: 2013-09-01
forum: General Help
---

### Post by Scrumps on 2013-09-01
I seem to be having an issue with recovery/mounting drives that were corrupted due to processor failure.
I had cloned the malfunctioning drive to a 2TB drive to work off that.

Afterwards, I run fsck -yft ext4 /dev/sdf1

It resulted in this output:
> 
music: ***** FILE SYSTEM WAS MODIFIED *****
Recreate journal? yes

Creating journal (32768 blocks):  Done.

*** journal has been re-created - filesystem is now ext3 again ***
e2fsck: aborted

music: ***** FILE SYSTEM WAS MODIFIED *****


So I went to mount the drive:
> 
root@server:/home/user# mount -t ext3 /dev/sdf1/ /media/tmp/
mount: wrong fs type, bad option, bad superblock on /dev/sdf1,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so


Which then displays this message (note that I did attempt to mount this as ext4 as it was supposed to be a an ext4 fs):> 
root@server:~#dmesg | tail
[...]
[608718.829959] EXT4-fs (sdf1): ext4_check_descriptors: Checksum for group 0 failed (22511!=0)
[608718.829966] EXT4-fs (sdf1): group descriptors corrupted!
[608725.344120] EXT4-fs (sdf1): ext4_check_descriptors: Checksum for group 0 failed (22511!=0)
[608725.344127] EXT4-fs (sdf1): group descriptors corrupted!
[608742.524348] EXT3-fs (sdf1): error: couldn't mount because of unsupported optional features (240)


If I run dump2efs -h I get the following:> 
dumpe2fs 1.42.5 (29-Jul-2012)
Filesystem volume name:   music
Last mounted on:          /srv/music
Filesystem UUID:          12803c48-(omit)
Filesystem magic number:  0xEF53
Filesystem revision #:    1 (dynamic)
Filesystem features:      has_journal ext_attr resize_inode dir_index filetype extent flex_bg sparse_super large_file huge_file uninit_bg dir_nlink extra_isize
Filesystem flags:         signed_directory_hash 
Default mount options:    user_xattr acl
Filesystem state:         clean with errors
Errors behavior:          Continue
Filesystem OS type:       Linux
Inode count:              30457856
Block count:              121830927
Reserved block count:     6091546
Free blocks:              60898777
Free inodes:              30421418
First block:              0
Block size:               4096
Fragment size:            4096
Reserved GDT blocks:      994
Blocks per group:         32768
Fragments per group:      32768
Inodes per group:         8192
Inode blocks per group:   512
Flex block group size:    16
Filesystem created:       Tue May 28 16:59:20 2013
Last mount time:          Mon Aug 26 11:01:42 2013
Last write time:          Mon Aug 26 11:04:48 2013
Mount count:              38
Maximum mount count:      -1
Last checked:             Tue May 28 16:59:27 2013
Check interval:           0 (<none>)
Lifetime writes:          235 GB
Reserved blocks uid:      0 (user root)
Reserved blocks gid:      0 (group root)                                                                                                                                                             
First inode:              11                                                                                                                                                                         
Inode size:               256                                                                                                                                                                        
Required extra isize:     28                                                                                                                                                                         
Desired extra isize:      28                                                                                                                                                                         
Journal inode:            8                                                                                                                                                                          
Default directory hash:   half_md4                                                                                                                                                                   
Directory Hash Seed:      7ba6ce48-325c-4f90-971a-ffba7e839da3                                                                                                                                       
Journal backup:           inode blocks                                                                                                                                                               
FS Error count:           35                                                                                                                                                                         
First error time:         Wed Aug 14 11:59:41 2013
First error function:     ext4_iget
First error line #:       3889
First error inode #:      8
First error block #:      0
Last error time:          Mon Aug 26 11:02:23 2013
Last error function:      ext4_readdir
Last error line #:        224
Last error inode #:       22020234
Last error block #:       9249
dumpe2fs: A block group is missing an inode table while reading journal inode

I was told it might be good to run debugfs (was in the ext fs channel on OFTC IRC) and this results in the following message:
> 
root@server:~# debugfs -R "stat <8>" /dev/sdf1
debugfs 1.42.5 (29-Jul-2012)
stat: A block group is missing an inode table while reading inode 8



So I have a drive that appears to be ext3/4, but won't mount, and I have no idea how to resolve this so I can try and scrape as much data off of it as possible. I was wondering if anyone was familiar with data recovery techniques, that might be able to assist me in getting any of the data back, or at least partially recoving some of the data listed here. Because right now, I am out of luck with some of these drives. Especially the ones that operate like this, and aren't correctly applied.

---

### Post by dragonfly41 on 2013-09-01
It's possible that this might offer a clue  ...

> bad superblock on /dev/sdf1

Here are some links which I saved as bookmarks which might help you .. if it is a bad superblock to correct ..

[http://www.cgsecurity.org/wiki/Advanced_Find_ext2_ext3_Backup_SuperBlock](http://www.cgsecurity.org/wiki/Advanced_Find_ext2_ext3_Backup_SuperBlock)

[http://linuxexpresso.wordpress.com/2010/03/31/repair-a-broken-ext4-superblock-in-ubuntu/](http://linuxexpresso.wordpress.com/2010/03/31/repair-a-broken-ext4-superblock-in-ubuntu/)

[http://unix.stackexchange.com/questions/33284/recovering-ext4-superblocks](http://unix.stackexchange.com/questions/33284/recovering-ext4-superblocks)

this link is for EXT2/EXT3 only .. but might apply to EXT4

[http://kezhong.wordpress.com/2009/06/27/linux-ext2ext3-superblock-recovery/](http://kezhong.wordpress.com/2009/06/27/linux-ext2ext3-superblock-recovery/)

There is more discussion on superblock recovery in the testdisk forum.  You can install testdisk from ubuntu repo.

---

### Post by Scrumps on 2013-09-01
> **dragonfly41 said:**
> It's possible that this might offer a clue  ...



Here are some links which I saved as bookmarks which might help you .. if it is a bad superblock to correct ..

[http://www.cgsecurity.org/wiki/Advanced_Find_ext2_ext3_Backup_SuperBlock](http://www.cgsecurity.org/wiki/Advanced_Find_ext2_ext3_Backup_SuperBlock)

[http://linuxexpresso.wordpress.com/2010/03/31/repair-a-broken-ext4-superblock-in-ubuntu/](http://linuxexpresso.wordpress.com/2010/03/31/repair-a-broken-ext4-superblock-in-ubuntu/)

[http://unix.stackexchange.com/questions/33284/recovering-ext4-superblocks](http://unix.stackexchange.com/questions/33284/recovering-ext4-superblocks)

this link is for EXT2/EXT3 only .. but might apply to EXT4

[http://kezhong.wordpress.com/2009/06/27/linux-ext2ext3-superblock-recovery/](http://kezhong.wordpress.com/2009/06/27/linux-ext2ext3-superblock-recovery/)

There is more discussion on superblock recovery in the testdisk forum.  You can install testdisk from ubuntu repo.

I have tried doing that, but unfortunately, every superblock I have tried ends up coming out like this:
> 
mke2fs -n /dev/sdf1
Superblock backups stored on blocks: 
        32768, 98304, 163840, 229376, 294912, 819200, 884736, 1605632, 2654208, 
        4096000, 7962624, 11239424, 20480000, 23887872, 71663616, 78675968, 
        102400000, 214990848


@server:~$ sudo fsck -b 163840 -fyt ext4 /dev/sdf1
fsck from util-linux 2.20.1
e2fsck 1.42.5 (29-Jul-2012)
fsck.ext4: Bad magic number in super-block while trying to open /dev/sdf1

The superblock could not be read or does not describe a correct ext2
filesystem.  If the device is valid and it really contains an ext2
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device>

@server:~$ sudo fsck -b 32768 -fyt ext4 /dev/sdf1
fsck from util-linux 2.20.1                                                                                                                                                                          
e2fsck 1.42.5 (29-Jul-2012)                                                                                                                                                                          
fsck.ext4: Bad magic number in super-block while trying to open /dev/sdf1                                                                                                                            
                                                                                                                                                                                                     
The superblock could not be read or does not describe a correct ext2                                                                                                                                 
filesystem.  If the device is valid and it really contains an ext2                                                                                                                                   
filesystem (and not swap or ufs or something else), then the superblock                                                                                                                              
is corrupt, and you might try running e2fsck with an alternate superblock:                                                                                                                           
    e2fsck -b 8193 <device>                                                                                                                                                                          
                                                                                                                                                                                                     
server:~$ sudo fsck -b 20480000 -fyt ext4 /dev/sdf1        
fsck from util-linux 2.20.1                                                                                                                                                                          
e2fsck 1.42.5 (29-Jul-2012)                                                                                                                                                                          
fsck.ext4: Bad magic number in super-block while trying to open /dev/sdf1                                                                                                                            
                                                                                                                                                                                                     
The superblock could not be read or does not describe a correct ext2                                                                                                                                 
filesystem.  If the device is valid and it really contains an ext2                                                                                                                                   
filesystem (and not swap or ufs or something else), then the superblock                                                                                                                              
is corrupt, and you might try running e2fsck with an alternate superblock:                                                                                                                           
    e2fsck -b 8193 <device>


It can work with the very last superblock, but, I feel like that might be the superblock it already uses when I do an fsck in the first place. I can tell when it finishes here in a second, but unfortunately, there is so much input during the fsck, that it would be an issue to manually do it.

EDIT: It just completed, and it does indeed induce the same issue.

EDIT2: I also think it has something to do with this:
> [B]Block #3147160 (886622) causes directory to be too big.  CLEARED.
Error storing directory block information (inode=1049388, block=0, num=184248): Memory allocation failed
[/B]
music: ***** FILE SYSTEM WAS MODIFIED *****
Recreate journal? yes

Creating journal (32768 blocks):  Done.

*** journal has been re-created - filesystem is now ext3 again ***
**e2fsck: aborted**

music: ***** FILE SYSTEM WAS MODIFIED *****

I honestly think this has something to do with it.

I say that, because after running it again, it fails at a different section:
> Inode 89988 is too big.  Truncate? yes

Block #3148812 (111948529) causes directory to be too big.  CLEARED.
Error storing directory block information (inode=89988, block=0, num=2822785): Memory allocation failed

music: ***** FILE SYSTEM WAS MODIFIED *****
e2fsck: aborted



---

### Post by dragonfly41 on 2013-09-02
This thread does suggest that you can COPY your files .. even with corrupt superblock .. using TestDisk > Advanced > List
to analyse your drive

[http://forum.cgsecurity.org/phpBB3/corrupted-superblock-t1042.html](http://forum.cgsecurity.org/phpBB3/corrupted-superblock-t1042.html)

[http://tenabletechtips.com/2013/05/28/repair-a-broken-ext3-superblock/](http://tenabletechtips.com/2013/05/28/repair-a-broken-ext3-superblock/)

So try copying found files to an uncorrupted drive.

---

### Post by Scrumps on 2013-09-02
Copying the files that I can see isn't the problem really, I mean, I can do that fine on some drives. For instance my music drive, I have it setup/structured so that:

/srv/music
.
../music
.../?
../Foobar
.../themefile1
.../themefile2

So I can see some of the files there, but the other parts (mainly the ? under music) is the issue that I am trying to recover. Unfortunately I made a goof up on my recovery drive that I am using (accidentally did the wrong command and started copying over another drive) so I am waiting for the music drive to be cloned back again so I can start testing this.

---

### Post by dragonfly41 on 2013-09-03
I did read this in last article (see last link above) ...

> If the first backup doesn’t work, you will need to try to restore it  from the next backup and so on until it is successful.  After each  restore, you should reboot your system and see if it boots correctly.   If not, repeat the steps and eventually it will work.

I admit I don't know why a reboot should be necessary between each attempt to restore superblock .. but you could try that advice.

The testdisk forum has various threads on superblock recovery.

---

