---
title: "can't access folder"
date: 2007-06-29
forum: General Help
---

### Post by groovomata on 2007-06-29
Hi All, I think I've managed to corrupt a folder or file in my Linux partition. I edited some MSWord documents while booted into Windows. I have the ext2 plugin installed. It's never given me problems before, however now I cannot access the folder where those documents are/or were located, in Linux, using nautilus or the terminal. If possible I'd like to recover what I can from that folder. I was also wondering if it could be a hardware issue. Does anyone have any ideas on how to troubleshoot this issue?
Feisty, kernel 2.6.20-16 generic.
Thanks,
Erik.

---

### Post by Xs1t0ry on 2007-06-29
So you're running a Dual-boot? You know NTFS files are read-only, right? And that your Ubuntu might not have a Word Processor capable of opening a *.doc or *.rtf file?

---

### Post by groovomata on 2007-06-30
> **Xs1t0ry said:**
> So you're running a Dual-boot? You know NTFS files are read-only, right? And that your Ubuntu might not have a Word Processor capable of opening a *.doc or *.rtf file?
Correct, I am running a dual boot system. There is a tool called ntfs-config (search synaptic for it) which gives read and write access to ntfs drives. There is also a 'kernel mode file system driver' that gives read and write access to the ext2 Linux file system ([http://www.fs-driver.org/](http://www.fs-driver.org/)) from windows. Open Office is perfectly capable of reading and writing to the .doc files I make. However obviously something went horribly wrong when I was using Windows XP and MSOffice to edit and make some files in that folder using the ext2 driver for Windows. When booted into Linux, if I try to use Nautilus to view that folder it locks up and I have to force quit it, as well I cannot launch Nautilus again as it fails. I then need to use the System Monitor to kill the processess. Which then means that I can no longer launch nautilus until I restart the xserver by pressing <ctrl><alt><backspace> - which is a drag. 
Thanks for responding!
Erik.

---

### Post by groovomata on 2007-07-02
I rebooted using the live cd and ran fsck with this result:
```

fsck 1.40-WIP (14-Nov-2006)
fsck.ext2: Is a directory while trying to open /dev/disk

The superblock could not be read or does not describe a correct ext2
filesystem.  If the device is valid and it really contains an ext2
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device>

```
Any advice would be greatly appreciated,
Thanks!
Erik.

---

### Post by groovomata on 2007-07-03
I visited this thread [http://ubuntuforums.org/showthread.php?t=490683&highlight=superblock](http://ubuntuforums.org/showthread.php?t=490683&highlight=superblock) and solved my problem by booting up into the live cd and doing this. Now I can access my folder and edit my files!
```

ubuntu@ubuntu:~$ sudo e2fsck -c /dev/hda2
e2fsck 1.40-WIP (14-Nov-2006)
Checking for bad blocks (read-only test): done                                
Pass 1: Checking inodes, blocks, and sizes
HTREE directory inode 1933695 has an invalid root node. 
Clear HTree index<y>? yes

Pass 2: Checking directory structure
Pass 3: Checking directory connectivity
Pass 3A: Optimizing directories
Pass 4: Checking reference counts
Pass 5: Checking group summary information 

/dev/hda2: ***** FILE SYSTEM WAS MODIFIED *****
/dev/hda2: 209574/4882432 files (1.7% non-contiguous), 5643669/9759487 blocks
ubuntu@ubuntu:~$ 

```

---

