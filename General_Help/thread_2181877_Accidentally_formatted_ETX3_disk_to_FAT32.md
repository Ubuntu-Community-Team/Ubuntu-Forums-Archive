---
title: "Accidentally formatted ETX3 disk to FAT32"
date: 2013-10-19
forum: General Help
---

### Post by Meneer Jansen on 2013-10-19
I accidentally formatted my external hard drive from etx3 to fat32 (instead of an USB thumb stick). I hear that TestDisk can repair the file system. I ran that program but I really do not understand what to do in that program. Does anybody here have experience w/ accidental formatting?

---

### Post by oldfred on 2013-10-19
So does it show the old ext3 partition with a d for deleted? Then you may be able to undo the change to FAT32.

 Instructions
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)
[http://www.cgsecurity.org/wiki/Menu_Analyse](http://www.cgsecurity.org/wiki/Menu_Analyse)

---

### Post by Meneer Jansen on 2013-10-19
> **oldfred said:**
> So does it show the old ext3 partition with a d for deleted? Then you may be able to undo the change to FAT32.

 Instructions
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)
[http://www.cgsecurity.org/wiki/Menu_Analyse](http://www.cgsecurity.org/wiki/Menu_Analyse)
Thank you for your fast reply. The 1TB external disk is very slow. So I created a test SD card with an ext3 partition. I then "accidentally" formatted it to fat32. When I run TestDisk then:
[LIST=1]
[*]Partition not recognized, it says: "Non partitioned media" (?)
[*]I choose "Intel/PC partition"
[*]Analyse
[*]No partition is bootable
[*]Quick search
[*]Nothing shows up...
[*]Deeper search
[*]Nothing shows up
[*]Structure: OK. Enter to continue
[*]I press <<Enter>>
[*]Then I can only quit.
[/LIST]

I am currently backing up the disk. I might try the Search function on the orig. disk after that.

---

### Post by Meneer Jansen on 2013-10-19
I appears that in my reply above I typed in:
```

testdisk /dv/sdb1

```
Instead of:
```

testdisk /deb/sdb

```
Notice the omission of the "1". No I get the following output of testdisk after a deep search:
```

Warning: the current number of heads per cylinder is 61
but the correct value may be 255.
You can use the Geometry menu to change this value.
It's something to try if
- some partitions are not found by TestDisk
- or the partition table can not be written because partitions overlaps.

```
I press Enter and then I get:
```

TestDisk 6.11, Data Recovery Utility, April 2009
Christophe GRENIER <grenier@cgsecurity.org>
http://www.cgsecurity.org


Disk /dev/sdb - 1978 MB / 1887 MiB - CHS 1022 61 62 (RO)
     Partition               Start        End    Size in sectors
D FAT32                    0   0 33  1021  17 52    3862496 [UNSOL_RESPO]
D FAT32                    0  33  3  1021  17 52    3860480 [fattest]







Structure: Ok.  Use Up/Down Arrow keys to select partition.
Use Left/Right Arrow keys to CHANGE partition characteristics:
*=Primary bootable  P=Primary  L=Logical  E=Extended  D=Deleted
Keys A: add partition, L: load backup, T: change type, P: list files,
     Enter: to continue
FAT32, 1977 MB / 1885 MiB

```

So no EXT3 partition shows up with a "D" for "deleted" in front of it. I called my EXT3 partition "ext3test" and gave the label "fattest" for the "accidental" format to FAT32 of said partition.

---

### Post by oldfred on 2013-10-19
Is that the correct drive, as it says it is only 2GB? Or is it the flash drive you were testing?

---

### Post by Meneer Jansen on 2013-10-19
> **oldfred said:**
> Is that the correct drive, as it says it is only 2GB? Or is it the flash drive you were testing?
Yes, that's my test drive.

---

### Post by oldfred on 2013-10-19
How far do you want to try? Do you have backups.
First backup partition table, use your drive for sdX or sda, sdb etc.
 sudo sfdisk -d /dev/sdX > parts.txt

    
Lets first see if you can just change it to ext3. Use Disk Utility or Disks and change type to ext3, not Format, just type.
then post this:
       sudo fdisk -lu /dev/sda
sudo parted /dev/sda unit s print
sudo sfdisk -l -uS

    
If the end sector is not end of drive we proably want to change it.

---

### Post by Meneer Jansen on 2013-10-20
> **oldfred said:**
> How far do you want to try? Do you have backups.
First backup partition table, use your drive for sdX or sda, sdb etc.
 sudo sfdisk -d /dev/sdX > parts.txt

I'd like to go as far as I can w/ my "exercise" SD card/USB stick that I created to practice saving EXT3 info that was accidentally formatted to fat32. Then, if I really, really, know what I'm doing, I'm going to do the same w/ the actual 1 TB disk. I might buy yet another 1 TB disk for a 'ddrescue' bit-by-bit backup. The ddrescue backup takes 5.6 days (= 5.6 x 24 hours!) in my current setup, however!  

I already used the non-destructive program 'Photorec' to recover what was on the actual 1 TB disk to another 1 TB (external) disk. That's not a whole lot (about 50%) and all my files are cut into little fragments. No file is "whole" and movies cannot be fast forwarded because they are corrupt etc. Some movies for example are cut into 5 parts. It's a mess and a disaster....                                                       

> **oldfred said:**
> 
Lets first see if you can just change it to ext3. Use Disk Utility or Disks and change type to ext3, not Format, just type.

I take it that you do not mean a program called 'Disk Utility'?

> **oldfred said:**
> 
then post this:
       sudo fdisk -lu /dev/sda
sudo parted /dev/sda unit s print
sudo sfdisk -l -uS

If the end sector is not end of drive we proably want to change it.


Here's the output of those commands on my "practice SD card":
```

mistaker@linux:~$ sudo fdisk -lu /dev/sdb


Disk /dev/sdb: 1977 MB, 1977614336 bytes
4 heads, 32 sectors/track, 30176 cylinders, total 3862528 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00003638


   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1            2048     3862527     1930240   83  Linux

```


```

mistaker@linux:~$ sudo parted /dev/sdb unit s print
Backtrace has 14 calls on stack:
  14: /lib/libparted.so.0(ped_assert+0x2a) [0xc39f0a]
  13: /lib/libparted.so.0(+0x42617) [0xc71617]
  12: /lib/libparted.so.0(+0x43427) [0xc72427]
  11: /lib/libparted.so.0(+0x4471c) [0xc7371c]
  10: /lib/libparted.so.0(+0xf7b1) [0xc3e7b1]
  9: /lib/libparted.so.0(ped_disk_add_partition+0x262) [0xc42032]
  8: /lib/libparted.so.0(+0x460b3) [0xc750b3]
  7: /lib/libparted.so.0(+0x462af) [0xc752af]
  6: /lib/libparted.so.0(ped_disk_new+0x75) [0xc42e15]
  5: parted() [0x804e389]
  4: parted(non_interactive_mode+0x85) [0x8054b95]
  3: parted(main+0x6d) [0x8052f9d]
  2: /lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xe6) [0x68dbd6]
  1: parted() [0x804c3f1]
                                                                          


You found a bug in GNU Parted! Here's what you have to do:


Don't panic! The bug has most likely not affected any of your data.
Help us to fix this bug by doing the following:


Check whether the bug has already been fixed by checking
the last version of GNU Parted that you can find at:


    http://ftp.gnu.org/gnu/parted/


Please check this version prior to bug reporting.


If this has not been fixed yet or if you don't know how to check,
please visit the GNU Parted website:


    http://www.gnu.org/software/parted


for further information.


Your report should contain the version of this release (2.2)
along with the error message below, the output of


    parted DEVICE unit co print unit s print


and the following history of commands you entered.
Also include any additional information about your setup you
consider important.


Assertion (head_size <= 63) at ../../../libparted/labels/dos.c:659 in function probe_partition_for_geom() failed.


Aborted

```



```

mistaker@linux:~$ sudo sfdisk -l -uS


Disk /dev/sda: 19457 cylinders, 255 heads, 63 sectors/track
Units = sectors of 512 bytes, counting from 0


   Device Boot    Start       End   #sectors  Id  System
/dev/sda1   *      2048 310546431  310544384  83  Linux
/dev/sda2     310546432 312580095    2033664  82  Linux swap / Solaris
/dev/sda3             0         -          0   0  Empty
/dev/sda4             0         -          0   0  Empty


Disk /dev/sdb: 1021 cylinders, 61 heads, 62 sectors/track
Warning: The partition table looks like it was made
  for C/H/S=*/4/32 (instead of 1021/61/62).
For this listing I'll assume that geometry.
Units = sectors of 512 bytes, counting from 0


   Device Boot    Start       End   #sectors  Id  System
/dev/sdb1          2048   3862527    3860480  83  Linux
        end: (c,h,s) expected (1023,3,32) found (479,3,32)
/dev/sdb2             0         -          0   0  Empty
/dev/sdb3             0         -          0   0  Empty
/dev/sdb4             0         -          0   0  Empty

```

---

### Post by oldfred on 2013-10-20
I am not sure why parted, errored out. Must not be able to handle your errors.
It looks like partition changed, but size is still wrong.

Again any of these changes may make it worse, so best to have as must recovered as you can before hand.
First what does testdisk not see, still a small partition?

I might try fsck.

       #From liveCD so everything is unmounted,swap off if necessary, change example shown with partition sdb1 to your partition(s)
#e2fsck is used to check the ext2/ext3/ext4 family of file systems. -p trys fixes where response not required
sudo e2fsck -C0 -p -f -v /dev/sdb1
#if errors: -y auto answers yes for fixes needing response, also see man e2fsck
sudo e2fsck -f -y -v /dev/sdb1

Parted has a repair mode and I was hoping it might help, but if it cannot even show partition it cannot find old one either.

---

### Post by Meneer Jansen on 2013-10-20
I think tools like parted fail because they expect a readable file allocation table or something like that to be there. They are not tools meant to rescue data, like TestDisk and Photorec. Problem is not that *some* file system info that might be recreated (from my old ext3 file system) has been gone, but that almost *everything* is gone. And, to make matters worse, it has been replaced with info from *another* sort of file system (i.e. fat32). 

By the way, I tried to run 'fsck' on my "exercise/test" disk and it completely destroyed my SD card's info!! **NEVER EVER** run fsck on a disk that was accidentally formatted to another file system! You'll loose even more data!

Will the old ext3 super block be of any use? Because some tools are able to find backups of it.  

P.S. The program Testdisk flashes some info from the old file system (i.e. the volume name "ext3_old") during the (deeper) search. But after the search nothing of the old ext3 file system can be seen though...

---

### Post by SeijiSensei on 2013-10-20
I actually did a very similar thing the other day when I thought I was talking to the machine on my desktop but was actually logged into my server!  I ran fdisk and set the partition to FAT32.  Linux didn't seem to care much about that, but I simply umounted the partitions and re-ran fdisk telling it to set the partition type back to 83 (Linux) then rebooted.  Problem fixed.

Now if the OP means he or she actually overwrote the file system with something like "fsck -t vfat /dev/sdb1" then recovery from that may be much more difficult.

---

### Post by Meneer Jansen on 2013-10-21
> **SeijiSensei said:**
> I actually did a very similar thing the other day when I thought I was talking to the machine on my desktop but was actually logged into my server!  I ran fdisk and set the partition to FAT32.  Linux didn't seem to care much about that, but I simply umounted the partitions and re-ran fdisk telling it to set the partition type back to 83 (Linux) then rebooted.  Problem fixed.

Now if the OP means he or she actually overwrote the file system with something like "fsck -t vfat /dev/sdb1" then recovery from that may be much more difficult.

What I did might not be as similar as you think. I think that you accidentally used *fdisk* to set your EXT3 (Linux) partition to FAT32. In my case, *fdisk* still thinks that I have an EXTX3 disk because I did not use *fdisk*, but *mkfs* (*mkfs.vfat* actuallly) to format my ETX3 disk to FAT32.

That's probably the reason why *fsck* won't work in my case, but it did in yours.

---

### Post by oldfred on 2013-10-21
I have not done any advanced repairs. But some links to suggestions.

 [http://linuxexpresso.wordpress.com/2010/03/31/repair-a-broken-ext4-superblock-in-ubuntu/](http://linuxexpresso.wordpress.com/2010/03/31/repair-a-broken-ext4-superblock-in-ubuntu/)
Remove first inode to use alternative superblock:
[http://ubuntuforums.org/showthread.php?t=1682038](http://ubuntuforums.org/showthread.php?t=1682038)
Using alternative superblock to check ext3
[http://planet.admon.org/using-alternative-superblock-to-check-ext3/](http://planet.admon.org/using-alternative-superblock-to-check-ext3/)
List backup superblocks:
sudo dumpe2fs /dev/sda5 | grep -i backup
then use backup superblock, 32768 just an example, try several
sudo fsck -b 32768 /dev/sda5

      
 Technical details of files, innodes & details of recovery, partial drive recovery details
[http://linux.sys-con.com/node/117909?page=0,0](http://linux.sys-con.com/node/117909?page=0,0)

   Last ditch redo superblocks:
[http://ubuntuforums.org/showthread.php?t=1681972&page=5](http://ubuntuforums.org/showthread.php?t=1681972&page=5)
Worked for this user:
[http://ubuntuforums.org/showthread.php?t=2033778](http://ubuntuforums.org/showthread.php?t=2033778)
[http://ubuntuforums.org/showthread.php?t=1684746](http://ubuntuforums.org/showthread.php?t=1684746)
Some additional advanced ways:
[http://animeshdas.wordpress.com/2009/11/18/data-recovery-from-corrupted-ext2ext3-filesystem-having-bad-superblock/](http://animeshdas.wordpress.com/2009/11/18/data-recovery-from-corrupted-ext2ext3-filesystem-having-bad-superblock/)

---

### Post by SeijiSensei on 2013-10-22
> **Meneer Jansen said:**
> That's probably the reason why *fsck* won't work in my case, but it did in yours.

Right. As I wrote, if you actually reformatted the file system, fdisk won't help.

---

