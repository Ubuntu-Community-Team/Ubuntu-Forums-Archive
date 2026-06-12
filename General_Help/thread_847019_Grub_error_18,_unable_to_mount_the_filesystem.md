---
title: "Grub error 18, unable to mount the filesystem"
date: 2008-07-02
forum: General Help
---

### Post by pooyaplus on 2008-07-02
](*,)

Hey guys,
I have been trying to boot a P4 2.40 PC after a power problem. The grub returns error 18 in its 1.5 loading stage.

I have also tried to recover the grub and recover the data on the HD with either a live disk and system rescue cd with no success. As I could not mount the EXT3 file system.

The HD had been managed this way:
75G ext3 as boot (sda1)
1.5G swap (sda2)


Here is the warning of the gparted with system rescue cd:

```

e2label: Attempt to read block from filesystem resulted in 
         short read while trying to open /dev/sda1
         Couldn't find valid filesystem superblock.

dumpe2fs: Couldn't find valid filesystem superblock.
          Unable to read contents of this filesystem!
          Because of this some operations maybe unavailable.

```

I really need to recover the filesystem to get the data back.
Any helps would be appreciated.

---

### Post by logos34 on 2008-07-03
try filesystem check with backup superblock option:

sudo fsck -b 8193 /dev/sda1

---

### Post by pooyaplus on 2008-07-03
Will Check and let you know.

---

### Post by pooyaplus on 2008-07-05
> **logos34 said:**
> try filesystem check with backup superblock option:

sudo fsck -b 8193 /dev/sda1

It says: 
```

root@0[parsix]# fsck -b 8193 /dev/sda1
fsck 1.40.8 (13-Mar-2008)
e2fsck 1.40.8 (13-Mar-2008)
fsck.ext3: Device or resource busy while trying to open /dev/sda1
Filesystem mounted or opened exclusively by another program?

```
But the file system is not mounted!
Any ideas?

---

### Post by pooyaplus on 2008-07-05
And here is the outcome of the fdisk -l from a live disk:
```

root@1[parsix]# fdisk -l -u 

Disk /dev/sda: 81.9 GB, 81964302336 bytes
255 heads, 63 sectors/track, 9964 cylinders, total 160086528 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x09260925

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   157067504    78533721   83  Linux
/dev/sda2       157067505   160071659     1502077+   5  Extended
/dev/sda5       157067568   160071659     1502046   82  Linux swap / Solaris

```

---

### Post by pooyaplus on 2008-07-05
And here is the df command ouput:

```

root@2[parsix]# df
df: no file systems processed

```

I'm not sure if I should do a filesystem check and repair with fsck as it is said in this Archived Thread:
[http://ubuntuforums.org/showthread.php?t=740441&highlight=Device+resource+fsck.ext3%3A+busy+open+%2Fdev%2Fsda1]("http://ubuntuforums.org/showthread.php?t=740441&highlight=Device+resource+fsck.ext3%3A+busy+open+%2Fdev%2Fsda1")

Any helps would be appreciated.

---

### Post by mempman on 2008-07-05
> **pooyaplus said:**
> It says: 
```

root@0[parsix]# fsck -b 8193 /dev/sda1
fsck 1.40.8 (13-Mar-2008)
e2fsck 1.40.8 (13-Mar-2008)
fsck.ext3: Device or resource busy while trying to open /dev/sda1
Filesystem mounted or opened exclusively by another program?

```
But the file system is not mounted!
Any ideas?

Try the following: 
```

sudo fuser -vm /dev/sda1

```


This will tell u what processes are accessing /dev/sda1...after it tells u the processes, kill them all, and then try the fsck command from above again.

---

### Post by pooyaplus on 2008-07-05
fuser -vm does not provide any process that has access to /dev/sda1.
And the fsck again, gives the same output.

---

### Post by pooyaplus on 2008-07-05
Well. I did the fsck.ext3 -f /dev/sda1

```

root@2[parsix]# fsck.ext3 -f /dev/sda1
e2fsck 1.40.8 (13-Mar-2008)
fsck.ext3: Attempt to read block from filesystem resulted in short read while trying to open /dev/sda1
Could this be a zero-length partition?

```

---

### Post by pooyaplus on 2008-07-05
Guys need help asap. I need to get data back.](*,)

---

### Post by shipp on 2011-01-15
Hey, sorry I can't help, having pretty much the same problem.  If anyone knows how to solve this error, it would be rad. for me its slightly different though.  I am trying to install Windows 7 in a Oracle virtual box and I cannot mount the USB drive I have that has windows seven on it.  I get the same error involving the same /dev/sdb1 .  It says read only file system and failed to mount /dev/sdb1.  So, am i screwed or is there a way to mount it so that i can get it in a virtual machine.  Any help would rock.

Thanks

---

### Post by Copperblade on 2011-01-15
The first thing I would do is run a smart check to see if the drive has failed or not:

smartctl -a /dev/sda

If you need to rescue data from a problematic disk, you will need to have another disk or partition available for storing the data.  If the data is critical and you can't even do a dump, I guess it'll be time to try dd.

---

