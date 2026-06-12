---
title: "Multi Boot with Multiple Persistent Partitions"
date: 2016-11-18
forum: General Help
---

### Post by C.S.Cameron on 2016-11-18
What I want - A flashdrive that can boot multiple versions of Ubuntu, (from iso files), each with it's own persistent partition.

Sundar Ima, gives a hint at a solution in MultiBootUSB V8, adding "persistent-path=/(folderx)/" after "persistent" in the grub2 menuentry. This allows the use of multiple casper-rw files on the same disk.

For example:

```
menuentry "ubuntu1.iso" {
set root=(hd0,1)
loopback loop /isos/ubuntu1.iso
linux (loop)/casper/vmlinuz.efi boot=casper persistent persistent-path=/casper1/ iso-scan/filename=/isos/ubuntu1.iso noeject noprompt --
initrd (loop)/casper/initrd.lz
}

menuentry "ubuntu2.iso" {
set root=(hd0,1)
loopback loop /isos/ubuntu2.iso
linux (loop)/casper/vmlinuz.efi boot=casper persistent persistent-path=/casper2/ iso-scan/filename=/isos/ubuntu2.iso noeject noprompt --
initrd (loop)/casper/initrd.lz
}
```

The first menuentry boots an iso named "ubuntu1.iso" located in the folder named "isos" using the casper-rw file located in the folder named "casper1".
The second menuentry boots an iso named "ubuntu2.iso" located in the folder named "isos" using the casper-rw file located in the folder named "casper2".

The problem is that the size of the casper-rw files is still limited to 4GB.

Having a limited understanding of grub2, I think the solution to multiple persistent partitions is to use "persistent-path=" to point to the desired casper-rw partition for each iso's grub menuentry, but how?

---

### Post by sudodus on 2016-11-18
Interesting problem. I have also tried to find a solution to this problem.

Would it be possible to store the {iso, casper-rw, home-rw} files in a file system that can manage huge files (for example an ext file system)? It should work to boot in BIOS mode, and maybe it would be possible also in UEFI mode with a separate EFI partition, which I think must have a FAT file system.

---

### Post by C.S.Cameron on 2016-11-18
I was trying to use a NTFS partition for iso's and persistence this morning.
The iso's would boot OK but the casper-rw files would not work.
Never been able to use one on anything but FAT32.
I have been trying persistent partitions with both EFI and msdos partitions.
I was quite sure I had it for a while but then I woke up.

I tried:

Persistent persistent-path=(hd0,5), Persistent persistent-path=(sdb5), I was goiing to try using UUID's but that takes too much typing.

I am not a grub guy, I was hoping either you or oldfred would have the answer.

---

### Post by sudodus on 2016-11-18
Using UUIDs can be done automatically with the help of a script (or a function in a script).

I do something similar in mkusb and dus in order to check which drives are involved in fstab (to avoid overwriting those drives).

---

### Post by C.S.Cameron on 2016-11-21
I tried it with UUID's but no joy there.
It seems like Ubuntu uses the first casper-rw it encounters, (HDD partition, flash drive partition), unless it is a casper-rw file.
But I am not giving up yet.

---

### Post by yancek on 2016-11-22
> It seems like Ubuntu uses the first casper-rw it encounters, (HDD  partition, flash drive partition), unless it is a casper-rw file.

I had a similar experience when I tried this some time ago.  Created a flash with persistence and then created a casper-rw partition on the hard drive and only one casper-rw was used, I think the flash drive but both were seen.   

I was unaware of the persistent-pathe= command so haven't tried that.  In the situation described by the OP, I would think it would work if it points to the casper-rw file in the correct location.  Might try it later. 

The original problem mentioned is the size of the casper-rw file which is due to using FAT32, no file larger than 4GB possible.  Nothing to do with Ubuntu, Linux or Grub.  From what I understand of casper-rw, if you want larger than 4GB you need a partition and that needs to be a Linux filesystem.

---

### Post by C.S.Cameron on 2016-11-22
> **yancek said:**
> 
I was unaware of the persistent-pathe= command so haven't tried that. In the situation described by the OP, I would think it would work if it points to the casper-rw file in the correct location. Might try it later.


It works very nicely with casper-rw files in different folders, Sundar Ima uses this method in MultiBootUSB V8.

Some people have suggested putting the casper-rw folders on a non FAT partition, so the file size could be larger than 4GB, but I have never had luck with persistence files on anything but FAT.

---

### Post by HermanAB on 2016-11-22
Howdy,

In my experience the 'persistent ISO' thing doesn't work particularly well.

You would probably have better luck by purchasing a bunch of cheap 32GB USB memory sticks and doing a regular install on each of them.

---

### Post by C.S.Cameron on 2016-11-23
Hi Herman, your posts on flash drive installs have been an inspiration.
The question is a little bit academic but:
I'm still using a 4GB flash drive I built back in 2010 using MultiBootUSB, I have gparted and clonezilla on it that I use regularly.
I also use it for preliminary testing new Ubuntu builds and daily builds.
I use a casper-rw partition for Ubuntu which can be handy for various reasons
For each new Ubuntu install, I delete an old iso, drop on the new iso and delete the data on the casper-rw partition.
This has always worked well for me, even with 16.04, (which will not work with syslinux boot, persistent partitions). 
I also had a home-rw persistent partition on it, but deleted it for the extra space.
With the size of flash drives growing rapidly I think multi boot / multi persistence would be handy technology, (but perhaps not mass market).
I'm afraid your solution would not work for me, I'm an old coot, and can never remember what is on which flash drive and I only have 7 or 8.

---

### Post by yancek on 2016-11-23
> Some people have suggested putting the casper-rw folders on a non FAT  partition, so the file size could be larger than 4GB, but I have never  had luck with persistence files on anything but FAT. 				

I've never used casper-rw 'files' on a Linux partition but have never had a problem with a casper-rw 'partition' on a Linux filesystem.

---

### Post by C.S.Cameron on 2016-11-23
Same here Yancek, I haven't been able to use casper-rw files on NTFS either.
I have not had luck using casper-rw partitions with recent Ubuntu versions, (>14.04), with syslinux installs, (SDC, UNetbootin, Rufus), but they still work great with grub2 installs like mkusb.

---

### Post by sudodus on 2016-11-26
I tried a casper-rw file on a Linux partition. The system boots well but the mechanism for persistence was *not* activated (the system remained live-only). This is an old system that I made 2013, that I grabbed for a quick test. It did not help with a current version of Lubuntu, as described at the end of the post.

```
lubuntu@lubuntu:~$ sudo lsblk -fm
NAME   FSTYPE   LABEL              MOUNTPOINT NAME     SIZE OWNER GROUP MODE
sda                                           sda      7.5G root  disk  brw-rw----
&#9492;&#9472;[COLOR="#0000FF"]**sda1 ext2     LubuGrubIso1GB     /isodevice &#9492;&#9472;sda1   7.5G root  disk  brw-rw----**[/COLOR]
sr0                                           sr0     1024M root  cdrom brw-rw----
loop0  iso9660  Lubuntu 13.10 i386 /cdrom     loop0    696M root  disk  brw-rw----
loop1  squashfs                    /rofs      loop1  637.9M root  disk  brw-rw----
zram0  swap                        [SWAP]     zram0  489.4M root  disk  brw-rw----
zram1  swap                        [SWAP]     zram1  489.4M root  disk  brw-rw----
zram2  swap                        [SWAP]     zram2  489.4M root  disk  brw-rw----
zram3  swap                        [SWAP]     zram3  489.4M root  disk  brw-rw----
lubuntu@lubuntu:~$ df -h
Filesystem      Size  Used Avail Use% Mounted on
[COLOR="#FF0000"]**/cow            2.0G   31M  1.9G   2% /**[/COLOR]
udev            2.0G  4.0K  2.0G   1% /dev
tmpfs           392M  1.1M  391M   1% /run
/dev/sda1       7.4G  6.7G  343M  96% /isodevice
/dev/loop0      696M  696M     0 100% /cdrom
/dev/loop1      638M  638M     0 100% /rofs
none            4.0K     0  4.0K   0% /sys/fs/cgroup
tmpfs           2.0G  4.0K  2.0G   1% /tmp
none            5.0M     0  5.0M   0% /run/lock
none            2.0G     0  2.0G   0% /run/shm
none            100M   16K  100M   1% /run/user
lubuntu@lubuntu:~$ ls -lh /isodevice/
total 6.7G
drwxr-xr-x 3 root root 4.0K May  2  2013 boot
[COLOR="#0000FF"]**-rw-r--r-- 1 root root 6.0G Nov 25 22:55 casper-rw**[/COLOR]
drwx------ 2 root root  16K May  2  2013 lost+found
-rw------- 1 1000 1000 696M Oct 16  2013 lubuntu.iso
lubuntu@lubuntu:~$ 
```

Yes, I remembered to create a file system in the file, as you can see from the following command line dialogue.

```
lubuntu@lubuntu:~$ sudo mount -o loop /isodevice/casper-rw /mnt
lubuntu@lubuntu:~$ df -h /mnt
Filesystem      Size  Used Avail Use% Mounted on
/dev/loop2      5.8G   12M  5.5G   1% /mnt
lubuntu@lubuntu:~$ sudo parted /dev/loop2 print
Model: Loopback device (loop)
Disk /dev/loop2: 6442MB
Sector size (logical/physical): 512B/512B
Partition Table: loop

Number  Start  End     Size    File system  Flags
 1      0.00B  6442MB  6442MB  ext4

lubuntu@lubuntu:~$ 
```

***Edit:*** I replaced the old Lubuntu from 2013 with the current one, ***16.04.1 LTS***, lubuntu-16.04.1-desktop-i386.iso, but still, it cannot use the casper-rw file in the ext2 file system.

---

### Post by sudodus on 2016-11-26
The maximum work space for persistence is 8 GiB (not 4 GiB). The casper-rw file is maximum 4 GiB and the home-rw file is also maximum 4 GB. But there are restrictions, max 4 GiB for the system (installed programs) and max 4 GiB for tweaks and personal files. 

It is possible to have an extra **data** partition for huge files like video clips, so maybe these 8 GiB will be enough for many users, who want multibooting with persistence for more than one of the systems.

---

### Post by C.S.Cameron on 2016-11-29
Thanks Sudodus, I gotta try sticking both casper-rw and home-rw files in multiple folders, for many people I would think having 8GB of persistence for each of their clients would be enough.

---

### Post by C.S.Cameron on 2016-11-29
If I type "dus" in Unity I don't see it, 
I got to launch it from nautilus.

---

### Post by sudodus on 2016-11-29
I checked in a live-only Ubuntu 16.04.1 LTS system, that it still works after the updates.

***guidus*** is the front end with a desktop file, which makes it work from Unity's dash or the menu of other desktop environments. The following commands,

```
sudo add-apt-repository universe
sudo add-apt-repository ppa:mkusb/unstable
sudo apt-get update
sudo apt-get install guidus
```

will install guidus and it will bring dus and the 'necessary' program packages. The **usb-pack-efi** package may be installed separately.

---

### Post by C.S.Cameron on 2016-11-30
Placing both casper-rw and home-rw persistence files in each of multiple directories, (folders), works and technically provides more that 4GB persistence for each. 

The directories must be on FAT32 partition(s) and each folder must have a unique name.
Partition names, (sdb5) can not be used in the persistent-path, only the unique folder name.
The O/S images can be iso images, (as produced by mkusb / dus), iso files or extracted files.
The path to root, (location of vmlinuz and initrd files), must be given in the grub menuentry.
See post 1 for example.
It does not seem like using this method, for persistent partitions, will work for Ubuntu, (at least not with both casper-rw and home-rw partitions ), as persistent path can not refer to partitions.

---

### Post by sudodus on 2016-12-01
Congratulations to a great solution by combining your own ideas with ideas and methods from several different people :KS

Please click on **Thread Tools** at the top of the page and mark this thread as SOLVED

---

