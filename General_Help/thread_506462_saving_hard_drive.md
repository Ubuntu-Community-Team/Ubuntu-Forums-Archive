---
title: "saving hard drive"
date: 2007-07-21
forum: General Help
---

### Post by mkljun on 2007-07-21
I have screwed my hard drive today. Don't even ask me how because its almost an unbelievable story. Now I'm running the live CD.

I have a hard drive divided in three parts (system - hda1, data - hda2, swap - hda3). And hda2 is a problem.

When I check hda with fdisk it finds hda2

```
$ sudo fdisk -l /dev/hda

Disk /dev/hda: 122.9 GB, 122942324736 bytes
255 heads, 63 sectors/track, 14946 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1               1        1147     9213246   83  Linux
/dev/hda2            1292       14946   109683787+  83  Linux
/dev/hda3            1148        1291     1156680   82  Linux swap / Solaris

Partition table entries are not in disk order
```

But I can't find it between devices so I can't run fsck or mount or whatever to save my data. 

```
$ ls -la /dev/hda*
brw-rw---- 1 root disk 3, 0 2007-07-21 15:37 /dev/hda
brw-rw---- 1 root disk 3, 1 2007-07-21 15:57 /dev/hda1
brw-rw---- 1 root disk 3, 3 2007-07-21 15:37 /dev/hda3
```

How it is possible that fdisk sees the partition and it is not between devices? How can I get it there?

Anyone?

---

### Post by taurus on 2007-07-21
What is the error message when you try to mount it?

```
sudo mkdir /media/hda2
sudo mount -t ext3 /dev/hda2 /media/hda2
```
Otherwise, run gparted (install it if you don't have it on your system, System -> Administration) and see what does the program say about /dev/hda2.

---

### Post by mkljun on 2007-07-22
> **taurus said:**
> What is the error message when you try to mount it?
Otherwise, run gparted (install it if you don't have it on your system, System -> Administration) and see what does the program say about /dev/hda2.

I already tried to mount yesterday it but since it does not exist in /dev/ it says 

```
$ sudo mount -t ext3 /dev/hda2 /mnt/hda2
mount: special device /dev/hda2 does not exist
```

Qparted on the other hand can't determine the file system of the partition.

[IMG]http://www.menola.org/~mkljun/Screenshot.png[/IMG]

While fdisk states that it has ext3 file system on it. I know I damaged the file
system but I don't know how to restore it :(.

---

### Post by mkljun on 2007-07-22
Hmm ... when I boot a PC from a hard drive (hda1 with Ubuntu 6.10), I can find hda2 in /dev. When I boot from a CD hda2 doesn't show up in /dev. Booting up in either way gave a lot of these errors:

```
ide: failed opcode was: unknown
end_request: I/O error, dev hda sector ....
hda: dma_intr: status 0x51 {drive ready seekcomplete error}
hda: dma_intr: error 0x40, {uncorectableerror} lba sector ...., sector ....
```

and then a lot of 

```
Buffer I/O error on device hda2, logical block ....
```

When I run fsck it gave me this error

```
$ fsck /dev/hda2
Buffer I/O error on device hda2, logical block ...
....{above line repeated}....

fsck.ext3: Attempt to read block from filesystem resulted in short read while trying to open /dev/hda2. 

Couldn't find a valid filesystem superblock.
```

Similar result with tune2fs

```
$ tune2fs /dev/hda2
Buffer I/O error on device hda2, logical block ...
....{above line repeated}....

fsck.ext3: Attempt to read block from filesystem resulted in short read while trying to open /dev/hda2. 

Could this be a zero-lenght partiton?
```

Is this of any help?

lp mk

---

