---
title: "Update failure; can not run Ubuntu now"
date: 2014-01-17
forum: General Help
---

### Post by Kymus on 2014-01-17
Last night before going to bed I started an update from 13.04 to 13.10. At some point in the night it decided to freeze up (the update, not the whole system itself). At this point the side bar and launcher weren't working and there were some artifacts elsewhere, so I did a REISUB. Now when loading Ubuntu, I get an error that the file system can not be mounted and I'm shoved to a terminal.

---

### Post by mansonfan78 on 2014-01-17
Have you tried updating from a live cd?  Also, did you happen to have any packages version-locked before the upgrade?

---

### Post by Kymus on 2014-01-19
> **mansonfan78 said:**
> Have you tried updating from a live cd?

Is this available within the GUI? It's been a while since I've touched a live disk. I'll have to format a memory card since my USB stick is not here presently (figures..)


> Also, did you happen to have any packages version-locked before the upgrade?

As far as I know, no. I assume such a thing would have to be manually initiated and I've done no such thing.

---

### Post by Bashing-om on 2014-01-19
Kymus; Maybe,

Let's try for an easy solution:
From that terminal, login and enter your password:
Now let's see what results from the file system check utility.
Terminal code:
```

sudo touch /forcefsck
sudo shutdown -r now

```
which will reboot the system and do a file system check when it returns.
What results ? Do you now boot to the GUI ?

[INDENT][INDENT]it is ubuntu
[INDENT][INDENT][INDENT]it is fixable
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by jeanjd63 on 2014-01-19
Hello
If you have a liveCD/USB, you boot with and do a :
**sudo  fsck  -f  -y  /dev/sdXY**  
Where XY are to change with the good value of your partition /

---

### Post by Kymus on 2014-01-23
I finally sat down with this.. 

This is the message I get:

> Filesystem check or mount failed.
A maintenance shell will now be started.
CONTROL-D will terminate this shell and continue booting after re-trying file systems.
Any further errors will be ignored.
root@Shaoxing:~$

There is no keyboard response at this terminal. I tried typing anything, and nothing. I tried REISUB, nothing. I tried CTRL+D, nothing.

---

### Post by Kymus on 2014-01-23
> **jeanjd63 said:**
> Hello
If you have a liveCD/USB, you boot with and do a :
**sudo  fsck  -f  -y  /dev/sdXY**  
Where XY are to change with the good value of your partition /

I got my usb back, so I can try this.

I forget how to check which SD is running what (I'm dual booting windows/ubuntu on separate drives). Can you give me a refresher?

---

### Post by mansonfan78 on 2014-01-23
You could try "sudo blkid" or launch gparted and see what it shows

---

### Post by Bashing-om on 2014-01-23
Kymus; Hey;

Hanging with you;
Terminal command:
```

sudo fdisk -lu

```
will out put your disk info.

[INDENT][INDENT]this should help
[/INDENT][/INDENT]

---

### Post by Kymus on 2014-01-24
Alright, I just popped in my USB and it booted to the (test) GUI.

Maybe I'm doing something wrong here, I'm not sure. Either way, here's the full terminal output. I've bolded the important stuff:

> **ubuntu@ubuntu:~$ sudo fdisk -lu **

Disk /dev/sda: 250.1 GB, 250059350016 bytes 
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors 
Units = sectors of 1 * 512 = 512 bytes 
Sector size (logical/physical): 512 bytes / 512 bytes 
I/O size (minimum/optimal): 512 bytes / 512 bytes 
Disk identifier: 0x27ea27e9 

   Device Boot      Start         End      Blocks   Id  System 
/dev/sda1   *          63   488375999   244187968+   7  HPFS/NTFS/exFAT 

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes 
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors 
Units = sectors of 1 * 512 = 512 bytes 
Sector size (logical/physical): 512 bytes / 512 bytes 
I/O size (minimum/optimal): 512 bytes / 512 bytes 
Disk identifier: 0x000a1743 

   Device Boot      Start         End      Blocks   Id  System 
/dev/sdb1   *        2048    11718655     5858304   82  Linux swap / Solaris 
/dev/sdb2        11720702  1953523711   970901505    5  Extended 
/dev/sdb5        11720704  1953523711   970901504   83  Linux 

Disk /dev/sde: 8086 MB, 8086618112 bytes 
249 heads, 62 sectors/track, 1023 cylinders, total 15794176 sectors 
Units = sectors of 1 * 512 = 512 bytes 
Sector size (logical/physical): 512 bytes / 512 bytes 
I/O size (minimum/optimal): 512 bytes / 512 bytes 
Disk identifier: 0x20ac7dda 

This doesn't look like a partition table 
Probably you selected the wrong device. 

   Device Boot      Start         End      Blocks   Id  System 
/dev/sde1   ?  3224498923  3657370039   216435558+   7  HPFS/NTFS/exFAT 
/dev/sde2   ?  3272020941   930513678   976730017   16  Hidden FAT16 
/dev/sde3   ?           0           0           0   6f  Unknown 
/dev/sde4        50200576   974536369   462167897    0  Empty 

Partition table entries are not in disk order 

Disk /dev/sdc: 32.0 GB, 32019111936 bytes 
255 heads, 63 sectors/track, 3892 cylinders, total 62537328 sectors 
Units = sectors of 1 * 512 = 512 bytes 
Sector size (logical/physical): 512 bytes / 512 bytes 
I/O size (minimum/optimal): 512 bytes / 512 bytes 
Disk identifier: 0x00000000 

   Device Boot      Start         End      Blocks   Id  System 
/dev/sdc1   *          63    62536319    31268128+   c  W95 FAT32 (LBA) 
[B]ubuntu@ubuntu:~$ sudo fsck -f -y /dev/sdb1 
fsck from util-linux 2.20.1 
fsck: fsck.swap: not found 
fsck: error 2 while executing fsck.swap for /dev/sdb1 [/B]

Should I be booting straight to a terminal instead? If so, how?

---

### Post by jeanjd63 on 2014-01-24
**sudo  fsck  -f  -y  /dev/sdb5**

---

### Post by Bashing-om on 2014-01-24
jeanjd63; Welp;

As you have discovered, sdb1 is a swap partition and ubuntu's file system check will not deal with it as swap is not a extX format.
Then you did check sdb5 - the ubuntu ext4 partition - BUT, did you do so from the liveUSB ? One can not check/repair the file system while it is mounted and thus in use. File system corruption is very likely.

Let's back up and try this:

From the liveUSB -> "try ubuntu" mode -> terminal:
```

sudo e2fsck -C0 -p -f -v /dev/sdb5

```
I expect there to be errors reported, so ->
```

sudo e2fsck -f -y -v /dev/sdb5

```
Where -y auto answers yes for fixes needing response ( error checks are much smarter than we are !)
Worthwhile to consult the manual for sure, see:
```

man e2fsck

```

OK, the file system now checks good, try and boot ubuntu.

In bios - UEFI in play as the sda is HPFS proprietary format ? - set to boot the second drive; and boot the operating system .

Can you boot ubuntu now ? 
NO ?

OK, then it is time to (RE-)install ubuntu's bootloader to that 2nd drive - sdb.

[INDENT][INDENT]sounds like a plan to me
[/INDENT][/INDENT]

---

### Post by Kymus on 2014-01-30
Here is the terminal output. AFAIK, there were no errors:

> ubuntu@ubuntu:~$ sudo e2fsck -C0 -p -f -v /dev/sdb5 
                                                                               
      669888 inodes used (1.10%, out of 60686336) 
        5549 non-contiguous files (0.8%) 
         864 non-contiguous directories (0.1%) 
             # of inodes with ind/dind/tind blocks: 0/0/0 
             Extent depth histogram: 616692/1098 
   128637124 blocks used (53.00%, out of 242725376) 
           0 bad blocks 
          24 large files 

      540774 regular files 
       59008 directories 
          57 character device files 
          25 block device files 
           4 fifos 
          19 links 
       70004 symbolic links (51997 fast symbolic links) 
           7 sockets 
------------ 
      669898 files 
ubuntu@ubuntu:~$ sudo e2fsck -f -y -v /dev/sdb5 
e2fsck 1.42.8 (20-Jun-2013) 
Pass 1: Checking inodes, blocks, and sizes 
Pass 2: Checking directory structure 
Pass 3: Checking directory connectivity 
Pass 4: Checking reference counts 
Pass 5: Checking group summary information 

      669888 inodes used (1.10%, out of 60686336) 
        5549 non-contiguous files (0.8%) 
         864 non-contiguous directories (0.1%) 
             # of inodes with ind/dind/tind blocks: 0/0/0 
             Extent depth histogram: 616692/1098 
   128637124 blocks used (53.00%, out of 242725376) 
           0 bad blocks 
          24 large files 

      540774 regular files 
       59008 directories 
          57 character device files 
          25 block device files 
           4 fifos 
          19 links 
       70004 symbolic links (51997 fast symbolic links) 
           7 sockets 
------------ 
      669898 files 

How do I go about reinstalling the boot loader? I assume this step is to allow me to get to a terminal on that partition?

---

### Post by Bashing-om on 2014-01-30
Kymus; Hekko;

Your attention is invited to your post #10,
Look at the output for sdb (ubuntu), see that sda1 is swap, that in it's self is unusual, generally swap is in that extended partition and generally is sda5, what I see though as  the major problem is that swap is also marked as the boot partition ( the star) !

The file system is intact as depicted by the file system checks - no errors. As to HOW in the world swap could have been marked as boot I can not imagine.
Presently I would be interested in seeing a screen shot of what GParted shows for the sdb drive,
and also post the output of terminal command:
```

sudo parted /dev/sdb unit s print

```
While I contemplate (RE-)installing grub onto the Master Boot Record of the sdb hard drive.
Maybe that would work, maybe not, in any event I really do not like swap as a primary partition as the 1st partition and marked as boot.

Honestly, at this point it may be simpler to (RE-)install the operating system than to rearrange the partitions.

But will not hurt to try and (re-)install grub, when we know what is, and see what results.

[INDENT][INDENT]strange things do happen
[/INDENT][/INDENT]

---

