---
title: "Critical File System Error PLEASE HELP!"
date: 2007-07-02
forum: General Help
---

### Post by Beamerboy on 2007-07-02
I have a corrupted superblock on a drive with a month's worth of University work that I haven't backed up (I normally backup monthly).  If I don't recover this data it is very likely I will fail my degree and not be able to do my PhD so I can't emphasize enough how important it is to recover this data.

First of all I booted to an edgy LiveCD and did the following on the drive when it was not mounted:

e2fsck -c /dev/sda1

I got the following output:

```

ubuntu@ubuntu:~$ sudo e2fsck -c /dev/sda1
e2fsck 1.39 (29-May-2006)
/dev/sda1: recovering journal
/dev/sda1: Attempt to read block from filesystem resulted in short read while reading block 23890

JBD: Failed to read block at offset 22322
JBD: IO error -5 recovering block 22322 in log
/dev/sda1: Attempt to read block from filesystem resulted in short read while reading block 23891

JBD: Failed to read block at offset 22323
JBD: IO error -5 recovering block 22323 in log
/dev/sda1: Attempt to read block from filesystem resulted in short read while reading block 23892

JBD: Failed to read block at offset 22324
JBD: IO error -5 recovering block 22324 in log
e2fsck: Bad magic number in super-block while trying to re-open /dev/sda1
e2fsck: io manager magic bad!

```

So I did the following to find the backup blocks for the superblock so I could attempt to rebuild it:

```

ubuntu@ubuntu:~$ sudo mke2fs -n -S /dev/sda1
mke2fs 1.39 (29-May-2006)
Filesystem label=
OS type: Linux
Block size=4096 (log=2)
Fragment size=4096 (log=2)
29884416 inodes, 59759784 blocks
2987989 blocks (5.00%) reserved for the super user
First data block=0
Maximum filesystem blocks=62914560
1824 block groups
32768 blocks per group, 32768 fragments per group
16384 inodes per group
Superblock backups stored on blocks: 
        32768, 98304, 163840, 229376, 294912, 819200, 884736, 1605632, 2654208, 
        4096000, 7962624, 11239424, 20480000, 23887872

```

I then proceeded to run e2fsck -b with the following results:

```

ubuntu@ubuntu:~$ sudo e2fsck -b 32768 /dev/sda1
e2fsck 1.39 (29-May-2006)
e2fsck: Bad magic number in super-block while trying to open /dev/sda1

The superblock could not be read or does not describe a correct ext2
filesystem.  If the device is valid and it really contains an ext2
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device>

```

As you can see it failed, so I tried the next backup block as follows:

```

ubuntu@ubuntu:~$ sudo e2fsck -b 98304 /dev/sda1
e2fsck 1.39 (29-May-2006)
e2fsck: Bad magic number in super-block while trying to open /dev/sda1

The superblock could not be read or does not describe a correct ext2
filesystem.  If the device is valid and it really contains an ext2
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device>

```

So I am starting to panic.  Do I need to pass anything to e2fsck to tell it I am checking an ext3 device?  According to the man pages e2fsck is supposed to work fine with ext3 file systems, but I don't understand why it keeps reporting incorrect ext2 filesystem??

I really need to recover this data, please help if you can.

Thanks

Paladine

---

### Post by Beamerboy on 2007-07-02
Bump

---

### Post by splintercellguy on 2007-07-02
dd your HDD asap, then work on the dd copy.

---

### Post by bodhi.zazen on 2007-07-02
First, unmount the partition. 

Second take a look at test disk : 

I think it is in the Ubunt repositories ;)

```
sudo apt-get install testdisk
```

[http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)

[http://www.cgsecurity.org/wiki/Running_TestDisk](http://www.cgsecurity.org/wiki/Running_TestDisk)

[http://www.cgsecurity.org/wiki/Advanced_Find_EXT2_EXT3_Backup_SuperBlock](http://www.cgsecurity.org/wiki/Advanced_Find_EXT2_EXT3_Backup_SuperBlock)

---

### Post by Beamerboy on 2007-07-02
> **splintercellguy said:**
> dd your HDD asap, then work on the dd copy.

Yeah I am running badblocks on my spare 250GB drive at the moment to prepare it for dd

After another reboot I was actually able to fix the superblock on the master drive with e2fsck -b but I don't understand why it failed the first couple of times, must have been an issue with the livecd environment at the time I guess.

Now the superblock is fixed I am confident I will be able to retrieve the data, it will take time but should be non-problematic now.

Paladine

---

### Post by Beamerboy on 2007-07-02
> **bodhi.zazen said:**
> First, unmount the partition. 

Second take a look at test disk : 

I think it is in the Ubunt repositories ;)

```
sudo apt-get install testdisk
```

[http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)

[http://www.cgsecurity.org/wiki/Running_TestDisk](http://www.cgsecurity.org/wiki/Running_TestDisk)

[http://www.cgsecurity.org/wiki/Advanced_Find_EXT2_EXT3_Backup_SuperBlock](http://www.cgsecurity.org/wiki/Advanced_Find_EXT2_EXT3_Backup_SuperBlock)

The partition was already unmounted, I would never run e2fsck on a mounted device.  If I can't manage to get it fixed using the standard tools, I will check out TestDisk but for now I will stick to tried and tested tools since I know exactly what they do.  Thanks anyway though.

Paladine

---

### Post by Beamerboy on 2007-07-03
Fixed and fully recovered.  Once I fixed the superblock issue everything else went smoothly.

Paladine

---

### Post by groovomata on 2007-07-03
> **splintercellguy said:**
> dd your HDD asap, then work on the dd copy.

I have a similar problem as Beamerboy. What does it mean to dd your HDD asap? I assume it means to copy but I'm not sure.
Thanks,
Erik.

---

### Post by bodhi.zazen on 2007-07-03
> **groovomata said:**
> I have a similar problem as Beamerboy. What does it mean to dd your HDD asap? I assume it means to copy but I'm not sure.
Thanks,
Erik.

Yes, dd is a way of copying your data/partition.

Here is a how to : [http://www.linuxquestions.org/linux/answers/Applications_GUI_Multimedia/How_To_Do_Eveything_With_DD](http://www.linuxquestions.org/linux/answers/Applications_GUI_Multimedia/How_To_Do_Eveything_With_DD)

And, I again suggest you look at those links of testdisk.

If you are not sure what you are doing, most important first step is to unmount the partition or repair it from a live CD. Then run testdisk to correct the problem.

---

