---
title: "Recovering files from RAID array after crash after inconsistent filesystem warning"
date: 2014-01-10
forum: General Help
---

### Post by insanity54 on 2014-01-10
Hey peeps.
 
I've got an office samba fileserver running ubuntu. It's got filesystem issues and I'm trying to fix them with fsck. I'm not trying to restore ubuntu, at this point I'm just trying to recover files then start over from scratch. The fileserver has a total of four 1TB HDDs. There are two mdadm RAID1 arrays, (each array has two disks) which is complicating the file recovery. I'm looking for some guidance because I'm not confident I'm taking the right steps to saving the files.


**Here's what I've done so far:**

The filesystem went read-only, probably because of the ext4 filesystem inconstencies that dmesg reported:

```
[1039664.515086] EXT4-fs error (device md0): ext4_lookup: deleted inode referenced: 31203443
```

Whenever I tried to write to anywhere …

```
$ touch ~/taco
```

I got this error:

```
touch: cannot touch `test': Read-only file system
```


(/dev/md0 is a RAID1 array made up of sda2 and sdd2 and is mounted at ’/’)

So there’s something wrong with the filesystem on md0. I wondered if it’s something raid related:

```
$ cat /proc/mdstat
```

```
Personalities : [raid1] [linear] [multipath] [raid0] [raid6] [raid5] [raid4] [raid10]
md0 : active raid1 sda2[1] sdd2[0]
    972855232 blocks [2/2] [UU]

md1 : active raid1 sda1[1] sdd1[0]
    3905472 blocks [2/2] [UU]

unused devices: <none>
```

I thought a quick fsck on all filesystems would be nice.

```
# fsck -A -M
```

It found lots of errors but I didn’t attempt to fix any of them. I ended up escaping (^C) the process. I wanted to be sure my data was safe before I did any repairing.

I went to the store and bought a 2TB external HDD. Hooked it up to the machine and tried to make a mountpoint for the HDD.

```
# mkdir /media/rescue
mkdir: cannot create directory `/media/rescue': Read-only file system
```

...right, there’s that whole issue. CRAP! I ended up using a dir that was already there, /dev/floppy0 as my mountpoint. With the external hdd mounted to /dev/floppy0, I used dd to make an image of the unmounted /dev/sdd on the external HDD, /dev/sde.

```
# dd if=/dev/sdd conv=sync,noerror bs=64K | gzip -c  >/media/floppy0/sdd.img.gz
```

Overnight, during the process, then the system crashed due to an unrelated problem that has been going on for four months where the system unexpectedly halts every other Thursday... Queue the "shame on you" comments!

I booted the machine again and it kernel panicked:

```
run-init: /sbin/init: No such file or directory
Kernel panic - not syncing: <something here I forgot to take note of>
```

So I put in a xubuntu live cd and booted that.

I restarted the dd process and 18 some hours later, it completed. Now I want to re-assemble the raid array (on just 1 of the disks in the array so incase I mess something up I still have a backup) so I do:

```
# mdadm --create --level=1 --force --raid-devices=1 /dev/md5 /dev/sdd2
```

then I try to mount it

```
# mount -t ext4 /dev/md5 /media/test
```

... I got a bunch of errors. in the mount output and dmesg, all of which I didn't take note of (oops.) Things like ext2 not found (this is an ext4 partition, why is it looking for ext2??)

I tried fsck.

```
fsck.ext4 /dev/md5
```

More errors about the superblock not being found, and "Bad magic number in super-block while trying to open /dev/md5"

I tried using backup superblocks as detailed on a [blog post]("http://tenabletechtips.com/2013/05/28/repair-a-broken-ext3-superblock/"). but had no success using any of the backup superblocks.



I found a [thread]("http://forums.opensuse.org/showthread.php/393098-fixing-superblock-running-e2fsck-on-a-mounted-filesystem") on another forum of a similar situation.

In said thread, a suggestion was given to re-create the filesystem. That seemed like a good idea so I did it:
```
mke2fs -S -b 4096 -v /dev/md5
```

it took awhile then exited cleanly. next step: 
```
e2fsck -y -f -v -C 0 /dev/md5
```

took several hours, reporting and fixing seemingly millions of errors, then exited with a showstopping error:
```
Error storing directory block information (inode=7718975, block=0, num=5946778): Memory allocation failed
e2fsck: aborted
```

Poopy. I wonder if I can mount the array anyway...
```
mount -t ext4 /dev/md5 /media/test
```

```
mount: wrong fs type, bad option, bad superblock on /dev/md5,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

```

dmesg output:

```
[90571.857406] md5: detected capacity change from 996202635264 to 0
[90571.857413] md: md5 stopped.
[90571.857419] md: unbind<sdd2>
[90571.877604] md: export_rdev(sdd2)
[90664.946271] md: bind<sdd2>
[90664.948382] md/raid1:md5: active with 1 out of 1 mirrors
[90664.948398] md5: detected capacity change from 0 to 996202635264
[90664.948880]  md5: unknown partition table
[105570.762539] EXT4-fs (md5): ext4_check_descriptors: Block bitmap for group 1 not in group (block 0)!
[105570.762545] EXT4-fs (md5): group descriptors corrupted!
```

I'm stuck and stumped now because my plan to rebuild the filesystem failed because e2fsck couldn't allocate memory. Just looking for some guidance, anybody throw me a bone?

---

### Post by insanity54 on 2014-01-13
Am I on the right track? Did I do something wrong?

---

