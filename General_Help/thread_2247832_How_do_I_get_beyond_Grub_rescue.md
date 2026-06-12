---
title: "How do I get beyond Grub rescue"
date: 2014-10-10
forum: General Help
---

### Post by parcdulas on 2014-10-10
Hello,

I am trying to set up a new system with 14.04 and Windows XP as dual boot. There is a 256Gb solid state disk with both operating systems on it and a 1 Tb hard disk currently formatted NTFS as storage under Windows XP. Everything was working fine until I installed the supplied software for an HP scanjet 4850 scanner under Windows. After the mandatory reboot all I get is 

"error:  no such device: 48d5b87a-2adb-43e6-8493-8c462a3e65ab
 entering rescue mode
Grub rescue>"

All on a black screen. Any suggestions? I'm having to post this using the live 14.04 disk as otherwise I can't get past the above  prompt.

Thanks,

Martin

---

### Post by parcdulas on 2014-10-10
Still using the live disk I got this from sudo parted -l

ubuntu@ubuntu:~$ sudo parted -l
Model: ATA SanDisk SDSSDHP2 (scsi)
Disk /dev/sda: 256GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End    Size   Type     File system  Flags
 1      32.3kB  256GB  256GB  primary  ntfs         boot


Model: ATA Hitachi HDS72101 (scsi)
Disk /dev/sdb: 1000GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type      File system  Flags
 1      32.3kB  996GB   996GB   primary   ntfs
 2      996GB   1000GB  4257MB  extended


Warning: Unable to open /dev/sr0 read-write (Read-only file system).  /dev/sr0
has been opened read-only.
Error: Can't have a partition outside the disk!                           

ubuntu@ubuntu:~$ 

dont know if this helps

---

### Post by Bashing-om on 2014-10-10
parcdulas; Hi !

There is but the one Windows partition on that 256 Gig SSD :
> 
ubuntu@ubuntu:~$ sudo parted -l
Model: ATA SanDisk SDSSDHP2 (scsi)
Disk /dev/sda: 256GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number Start End Size Type File system Flags
1 32.3kB 256GB 256GB primary ntfs boot


If there is an ubuntu system on the disk, it must be as a 'WIBI' - virtual file system installed inside of Windows.

Now, WUBI is no longer supported, it is recommended that you do a true dual boot to have an ubuntu operating system on this SSD along with Windows.

[INDENT][INDENT]just the way I see it
[/INDENT][/INDENT]

---

### Post by yancek on 2014-10-10
It doesn't make much sense that installing printer/scanner software or drivers would affect the booting as that is totally unrelated. Something else must be happening here.   Also, since you have no Linux partitions as pointed out and the problem was on your windows system installing windows software, you might have more success with your problem at a windows forum.  I've never used wubi so I'm not even sure how it is accessed.

---

### Post by Impavidus on 2014-10-10
If this is wubi, where does the grub rescue prompt come from? Because, if I am correct ([https://help.ubuntu.com/community/Wubi](https://help.ubuntu.com/community/Wubi)), wubi uses the Windows boot loader. Seems to me a partition went missing somehow.

Also remarkable, there is a 4GB extended partition on the 1TB drive, but there's nothing inside.

---

### Post by yancek on 2014-10-10
> wubi uses the Windows boot loader

That's my understanding also, but I've never actually used wubi so...?  Maybe the bootinfoscript would help if the OP comes back.  I don't see how installing software for a printer/scanner is going to affect the bootloader.  Something is missing here.

---

### Post by hakuna_matata on 2014-10-11
> **Impavidus said:**
>  wubi uses the Windows boot loader.
You are right, but Wubi uses multiple boot loaders. The default boot loader sequence is something like this: "Windows Boot Loader" -> "GRUB4DOS" -> "GRUB2"

But if GRUB2 is the first boot loader in sequence, it seems to be a dual boot with discarded linux partitions...

---

### Post by parcdulas on 2014-10-25
Thanks to all who replied. Wiped the sds and started from scratch now ok

---

### Post by Bashing-om on 2014-10-25
parcdulas; Great !

You do good .

Please mark this thread solved;
aides others seeking the solution,
helps keep the forum clean and
precludes others miss-directing efforts to aid.
[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

[INDENT][INDENT]Happy trails to you
[/INDENT][/INDENT]

---

