---
title: "System Won't Boot or goes to Grub Rescue"
date: 2015-01-07
forum: General Help
---

### Post by sinisterstuntz on 2015-01-07
Hello all,
     
     So here's what i'm running:  Asus Mobo with 2.8Ghz Quad Core AMD Phenom X2
                                            6GB RAM
                                            1TB HDD
                                            XFX Radeon HD7750 Gfx Card

                                            OS: Triple boot with Backtrack 5 r3, Windows 7, Ubuntu 14.04LTS.
                                            GNU GRUB Version 1.98-1ubuntu13

And the problem:
     The other day i sat down at my computer to get some work done and when i woke it up from sleep mode, i had a black screen and no response from any key presses.  So i (without thinking) held the power button and shut it down the hard way.... When it booted back through the ASUS logo, i get this:
     error: hd0,5 out of disk.
     grub rescue>_

Sometimes when i boot it up, i get the GRUB recovery menu saying minimal BASH-like editing is allowed....dah dah dah dah.

What can i do to resolve this? I might even just get rid of the two and go back to using Windows 7 only on my main PC, idk yet.  I'm typing this on my Acer Aspire Netbook at the moment, since my computer isn't currently functioning very well.

---

### Post by Bashing-om on 2015-01-07
sinisterstuntz; Well,

Only one operating system can have control of the boot process.
In 14.04 the version of grub is:
> 
sysop@1404mini:~$ grub-install --version
grub-install (GRUB) 2.02~beta2-9ubuntu1
sysop@1404mini:~$


From this we can surmise that Backtrack is that controlling OS .. Maybe backtrack's grub is no longer compatible to that of ubuntu with " 2.02~beta2-9ubuntu1 " ?

In any event it would behoove you to run a file system check - From a liveDVD(USB) as the file system(s) must be in a UN-mounted state .

That is my thought, If you want to continue to troubleshoot this issue.
Provide the outputs of terminal commands:
```

sudo fdisk -lu
sudo parted -l

```
Then we know where to direct 'fsck' and where to install ubuntu's grub to - as there can only be 1 .

[INDENT][INDENT]ain't nothing but a thing
[/INDENT][/INDENT]

---

### Post by sinisterstuntz on 2015-01-07
Currently downloading Ubuntu 14.04.1 LTS to burn to my USB stick and get Live boot it to get you that info. I'll post it as soon as i can get that far.

---

### Post by sinisterstuntz on 2015-01-07
Ok, this is what i received from fdisk and parted:

ubuntu@ubuntu:~$ sudo fdisk -lu

Disk /dev/sda: 8036 MB, 8036285952 bytes
229 heads, 20 sectors/track, 3427 cylinders, total 15695871 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000a2b9f

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048    15693823     7845888    b  W95 FAT32

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xcb5bd2b2

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *        2048    29747199    14872576    b  W95 FAT32
/dev/sdb2        29747200  1758168030   864210415+   7  HPFS/NTFS/exFAT
/dev/sdb3      1758169086  1953523711    97677313    5  Extended
/dev/sdb5      1758169088  1945487359    93659136   83  Linux
/dev/sdb6      1945489408  1953523711     4017152   82  Linux swap / Solaris
ubuntu@ubuntu:~$ sudo parted -l
Model: SanDisk Cruzer (scsi)
Disk /dev/sda: 8036MB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type     File system  Flags
 1      1049kB  8035MB  8034MB  primary  fat32        boot


Model: ATA ST31000528AS (scsi)
Disk /dev/sdb: 1000GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type      File system     Flags
 1      1049kB  15.2GB  15.2GB  primary   ntfs            boot
 2      15.2GB  900GB   885GB   primary   ntfs
 3      900GB   1000GB  100GB   extended
 5      900GB   996GB   95.9GB  logical   ext4
 6      996GB   1000GB  4114MB  logical   linux-swap(v1)


ubuntu@ubuntu:~$ ^C

---

### Post by Bashing-om on 2015-01-07
sinisterstuntz' Un Good .

For what you had thought.

The 1st drive recognized is sda -> an 8 Gig USB thumb drive ? - NOT linux .

and the second drive, sdb, has a Windows partition(s) and ONLY one linux install ( sdb5).

I am considering some means to determine if that install on sdb5 is 'Backtrack' or ubuntu .
The kernel version will tell us (!) :
Mount that partition from the liveDVD:
```

sudo mkdir /mnt/look
sudo mount /dev/sdb5 /mnt/look
ls -al /mnt/look/boot

```
might indicate that it is or is not 14.04 ubuntu.
When done look'n in /look, UNmount it.
```

sudo umount /mnt/look

```

When you decide what you want to do in this situation, we will proceed to that end.

[INDENT][INDENT]the truth can sometimes bite real hard
[/INDENT][/INDENT]

---

### Post by sinisterstuntz on 2015-01-07
That's because i had to boot from my live usb, that's the device your seeing as the first device.

Here's the output of the Look command you gave me:

ubuntu@ubuntu:~$ sudo mkdir /mnt/look
ubuntu@ubuntu:~$ sudo mount /dev/sdb5 /mnt/look
ls -al /mnt/look/boot
ubuntu@ubuntu:~$ ls -al /mnt/look/boot
total 106672
drwxr-xr-x  3 root root     4096 Nov 21  2013 .
drwxr-xr-x 26 root root     4096 Nov 21  2013 ..
-rw-r--r--  1 root root   647426 Sep 11  2013 abi-2.6.32-52-generic
-rw-r--r--  1 root root   647491 Oct 23  2013 abi-2.6.32-53-generic
-rw-r--r--  1 root root   110589 Sep 11  2013 config-2.6.32-52-generic
-rw-r--r--  1 root root   110589 Oct 23  2013 config-2.6.32-53-generic
-rw-r--r--  1 root root   136777 Feb 17  2012 config-3.2.6
drwxr-xr-x  3 root root     4096 Sep 16 16:40 grub
-rw-r--r--  1 root root 18644401 Jul 11  2012 initrdf.img-3.2.6
-rw-r--r--  1 root root 16375565 Nov  5  2013 initrd.img-2.6.32-52-generic
-rw-r--r--  1 root root 16377170 Nov 21  2013 initrd.img-2.6.32-53-generic
-rw-r--r--  1 root root 17622182 Oct 21  2013 initrd.img-3.2.6
-rw-r--r--  1 root root 18645379 Jul 11  2012 initrds.img-3.2.6
-rw-r--r--  1 root root   160280 Mar 23  2010 memtest86+.bin
-rw-r--r--  1 root root  2162905 Sep 11  2013 System.map-2.6.32-52-generic
-rw-r--r--  1 root root  2162905 Oct 23  2013 System.map-2.6.32-53-generic
-rw-r--r--  1 root root  2420596 Feb 17  2012 System.map-3.2.6
-rw-r--r--  1 root root     1336 Sep 11  2013 vmcoreinfo-2.6.32-52-generic
-rw-r--r--  1 root root     1336 Oct 23  2013 vmcoreinfo-2.6.32-53-generic
-rw-r--r--  1 root root  4070976 Sep 11  2013 vmlinuz-2.6.32-52-generic
-rw-r--r--  1 root root  4068928 Oct 23  2013 vmlinuz-2.6.32-53-generic
-rw-r--r--  1 root root  4808816 Aug  8  2012 vmlinuz-3.2.6
ubuntu@ubuntu:~$

---

### Post by Bashing-om on 2015-01-07
sinisterstuntz; Ho Kay ..

That is the 'Backtrack' install .. there is no ubuntu installed on that system:
If it were 14.04 ubuntu the kernel would be in the 3.13 series as in :
```

sysop@1404mini:~$ ls /boot
abi-3.13.0-40-generic         memtest86+.bin
abi-3.13.0-43-generic         memtest86+.elf
config-3.13.0-40-generic      memtest86+_multiboot.bin
config-3.13.0-43-generic      System.map-3.13.0-40-generic
grub                          System.map-3.13.0-43-generic
grub_backup                   vmlinuz-3.13.0-40-generic
initrd.img-3.13.0-40-generic  vmlinuz-3.13.0-43-generic
initrd.img-3.13.0-43-generic
sysop@1404mini:~$ 

```

So what now do you want to do ? 

a screen shot of GParted at this time would help, IF you want to also install ubuntu 14.04 . Will have to make room for ubuntu somewhere, some how.

[INDENT][INDENT]it is what it is
[/INDENT][/INDENT]

---

### Post by sinisterstuntz on 2015-01-07
So is Backtrack's version of Grub the culprit of my issue then?  I'm open to completely erasing Backtrack and just having Ubuntu 14.04.1 LTS and my Windows 7 OS's.  I know i had Ubuntu on there somewhere, maybe i was incorrect on which version i had. Might've been 12.04. I do see two series on that list. 3.2.6 and 2.6.32.

GParted screenshots attached.

[IMG]http://i61.tinypic.com/11kz9dc.png[/IMG]

---

### Post by westie457 on 2015-01-07
Hopefully the suspicion going through my mind at the moment will be proved wrong. Could you while booted into the Live USB Desktop go to here and use the 2nd option to download install and run Boot Repair. Just take the option to create a Boot report without attempting any repairs. [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

The best tool available to repair a NTFS file system is Windows 'chkdsk /f' which occassionally starts automatically when Windows boots and a partition is corrupted.


Oops, forgot to ask for the generated link to be posted here.

---

### Post by sinisterstuntz on 2015-01-07
> **westie457 said:**
> Hopefully the suspicion going through my mind at the moment will be proved wrong. Could you while booted into the Live USB Desktop go to here and use the 2nd option to download install and run Boot Repair. Just take the option to create a Boot report without attempting any repairs. [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

The best tool available to repair a NTFS file system is Windows 'chkdsk /f' which occassionally starts automatically when Windows boots and a partition is corrupted.


Oops, forgot to ask for the generated link to be posted here.

I tried the boot repair but it only gave me the boot info option.  Here's the URL it put out:  [http://paste.ubuntu.com/9690428/](http://paste.ubuntu.com/9690428/)

---

### Post by Bashing-om on 2015-01-07
westie457; sinisterstuntz ... Don't look good for the home team.

Boot-repair's output:
westie, what think you ? Time for 'smartctl' and see where we go from there ?

[INDENT][INDENT]I hate when that happens,
[INDENT][INDENT][INDENT]nothing last forever
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by sinisterstuntz on 2015-01-07
On a side note, i see you're from AR.  I grew up in Rogers, AR. What're the odds. haha

---

### Post by westie457 on 2015-01-07
Yikes! Was not expecting a corrupted partition table and all those errors. Tbh was expecting to see something like 'wubildr' in the output.

Unless Bashing-om has any other suggestions or better ideas it might be a good idea to use 'testdisk' from the repos to find all of the partitions and allow it to rewrite the table.
For testdisk to find the partitions allow somewhere in the region of 6 hours for a one TB drive to be scanned properly.

See here for tutorials on testdisk. [http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)

---

### Post by westie457 on 2015-01-07
> **Bashing-om said:**
> westie457; sinisterstuntz ... Don't look good for the home team.

Boot-repair's output:
westie, what think you ? Time for 'smartctl' and see where we go from there ?
[INDENT][INDENT]I hate when that happens,[INDENT][INDENT][INDENT]nothing last forever
[/INDENT]
[/INDENT]
[/INDENT]
[/INDENT]
[/INDENT]


'smartctl' won't hurt, it may confirm the drive is 100% fine or 100% broken.

Badblocks might be another way to show if the MBR area of the drive is borked, it will certainly take less time than testdisk.
```
sudo badblocks -s /dev/sdb
```
Errors will be shown immediately when found. Allow the same amount of time as for testdisk for a full drive scan or abort after 30 seconds (Ctrl+C).

---

### Post by Bashing-om on 2015-01-07
westie457; sinisterstuntz' Yeaya ...

That thought that a WUBI install for that 3rd operating system had occurred to me also .. But but ,,
This turn of events takes priority.
I can not say which is better, I was think'n to see what the full "SMART" would reveal, see then if 'testdisk' would be of effect.
Would running 'testdisk' 1st be the better course ? At some point data recovery will have to be considered.

On the lighter side:
> 
On a side note, i see you're from AR. I grew up in Rogers, AR. What're the odds. haha

For a fact, I be a true Arkansa(w) Ridge Runner. You being raised in Rodgers, well you too might qualify . I had a transplant at an early age. The opportunity to garner some computer skills before I returned.
Now I am truly amazed at how small the world has gotten. alla the times - "I knew you when" in this age of communications. Ain't it wonderful ?
------------------------
[INDENT][INDENT]that age old question
[INDENT][INDENT][INDENT][INDENT]what to do, Oh what to do [/INDENT][/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by sinisterstuntz on 2015-01-07
For testdisk, what type of partition table do i select? The two that seem applicable are INTEL and EFI GPT.  I know my chipset is AMD, that's the only reason i was skeptical on choosing Intel.  Wasn't sure if that made a difference or not.

---

### Post by sinisterstuntz on 2015-01-07
Disk /dev/sdb - 1000 GB / 931 GiB - ATA ST31000528AS

Please select the partition table type, press Enter when done.
>[Intel  ] Intel/PC partition
 [EFI GPT] EFI GPT partition map (Mac i386, some x86_64...)
 [Humax  ] Humax partition table
 [Mac    ] Apple partition map
 [None   ] Non partitioned media
 [Sun    ] Sun Solaris partition
 [XBox   ] XBox partition
 [Return ] Return to disk selection




Note: Do NOT select 'None' for media with only a single partition. It's very
rare for a drive to be 'Non-partitioned'.

---

### Post by Bashing-om on 2015-01-07
sinisterstuntz; OK !


confirmation:
> 
TestDisk asks you select the type of partition table to search for. In most cases (ext2/3, NTFS, FAT32, etc.) you should select Intel and press Enter.

see:
[http://www.howtogeek.com/howto/15761/recover-data-like-a-forensics-expert-using-an-ubuntu-live-cd/](http://www.howtogeek.com/howto/15761/recover-data-like-a-forensics-expert-using-an-ubuntu-live-cd/)

as testdisk turns

---

### Post by sinisterstuntz on 2015-01-07
TestDisk 6.14, Data Recovery Utility, July 2013
Christophe GRENIER <grenier@cgsecurity.org>
[http://www.cgsecurity.org](http://www.cgsecurity.org)

Disk /dev/sdb - 1000 GB / 931 GiB - CHS 121601 255 63

     Partition                  Start        End    Size in sectors


No partition found or selected for recovery

---

### Post by Bashing-om on 2015-01-07
sinisterstuntz; Welp;

We know that it is not true that there are no partitions; so " selected for recovery " ->
Backup and regroup .. follow the simple directions from the provided link:
[http://www.howtogeek.com/howto/15761/recover-data-like-a-forensics-expert-using-an-ubuntu-live-cd/](http://www.howtogeek.com/howto/15761/recover-data-like-a-forensics-expert-using-an-ubuntu-live-cd/)

see then if you have any results.

[INDENT][INDENT]'Eliminate all other factors, and the one which remains must be the truth.'

Sherlock Holmes Quote

[/INDENT][/INDENT]

---

### Post by westie457 on 2015-01-08
The quick search function of testdisk will only show the current state of the hard drive.

To find all partitions you must use the Deeper Search option, as stated earlier this will take about 6 hours in a 1TB drive. Also you must let the whole drive be scanned.
You might get a list of non-existant partitions included in with the list of valid partitions. Check each one that is not marked 'deleted',those cannot be recovered. As you check each one 'testdisk' will say either "ok" or "structure bad" for each option (Primary.Bootable and Logical).

---

### Post by sinisterstuntz on 2015-01-08
Ok, something isn't right then because even the deeper search won't show any results. Do I need to do anything special in terminal? Like mounting anything...

And the deep search only lasts about 5mins. I made sure that I selected the correct hard drive too.

---

### Post by westie457 on 2015-01-09
Very strange, have never known testdisk to behave like that.
We know from your boot report that your internal drive is designated as /dev/sdb could you run the badblocks command posted earlier in this thread please.
If you get a list quite early in the scan post the list here.
Badblocks will show where on the drive the bad blocks are.
Waiting for information.

---

### Post by sinisterstuntz on 2015-01-11
> **westie457 said:**
> Very strange, have never known testdisk to behave like that. We know from your boot report that your internal drive is designated as /dev/sdb could you run the badblocks command posted earlier in this thread please. If you get a list quite early in the scan post the list here. Badblocks will show where on the drive the bad blocks are. Waiting for information.  I ran badblocks as you requested and it just counted clear up to 976762583 and said "done". when i scroll up, it doesn't really show much. Just a lot of numbers, no messages or alerts or anything.  But then again, terminal only lets me scroll up as far as 976762074.

---

### Post by sinisterstuntz on 2015-01-11
Update: Instead of selecting Intel, i selected the second option labeled [EFI GPT] and now it's going uber slow like you were saying it should.  Hopefully this one will return some results.

---

### Post by westie457 on 2015-01-12
Just reviewed this thread to refresh my grey cells.
The 'EFIGPT' search option of testdisk will (should) not find anything useful, you have 'MBR' patitiioning. This conclusion has been reached because the 'fdisk' command lets you know with **'Warning: GPT table detected, use gdisk instead'**. This info is missing in your output.
If testdisk shows no partitions at it usually means the first few sectors (partition-table area) of the hard drive are damaged and cannot be read properly. This is sometimes fixable; definitely not fixable if that area of the drive cannot be written to.

Now onto badblocks.
The command I posted is supposed to list all of the bad sectors found, one per line. 
If you have a very long list of numbers it is not looking good for the future of the hard drive, it might be failing.

Now onto a possible way to get any or all of your OSes to boot. Get another usb stick and create a 'supergrub2' disk from here. [http://www.supergrubdisk.org/super-grub2-disk/](http://www.supergrubdisk.org/super-grub2-disk/)

Let us know what happens. If successful at booting anything we might be able to rescue everything. We will need Bashing-om's excellent knowledge to finish this.

---

### Post by Bashing-om on 2015-01-12
sinisterstuntz; westie457; Hey; Hang'n in here with yall .

That " Bashing-om's excellent knowledge" sometimes runs real skimpy . But we get a valid partition table in place, we will get this fingered out.

If 'testdisk' continues to be perverse, we will need to check the SMART status of that hard drive.

[INDENT][INDENT]all in a day's work
[/INDENT][/INDENT]

---

### Post by sinisterstuntz on 2015-01-12
> **Bashing-om said:**
> sinisterstuntz; westie457; Hey; Hang'n in here with yall .

That " Bashing-om's excellent knowledge" sometimes runs real skimpy . But we get a valid partition table in place, we will get this fingered out.

If 'testdisk' continues to be perverse, we will need to check the SMART status of that hard drive.

[INDENT][INDENT]all in a day's work
[/INDENT][/INDENT]

Ok, assuming testdisk keeps doing the same thing, which I'm sure it will. How do I go about checking the "Smart" status? Aside from asking my hdd what the square root of pi is... ;)

---

### Post by Bashing-om on 2015-01-12
sinisterstuntz; Well.

All we can do is try, and see what options we can come up with.

From the liveDVD, so file systems are not mounted and in use:
```

sudo smartctl -t long /dev/sda

```
[http://ubuntuforums.org/showthread.php?t=2192335](http://ubuntuforums.org/showthread.php?t=2192335) <-How to read output of smartctl?

[INDENT][INDENT]hoping for the best
[/INDENT][/INDENT]

---

### Post by sinisterstuntz on 2015-01-12
> **Bashing-om said:**
> sinisterstuntz; Well.

All we can do is try, and see what options we can come up with.

From the liveDVD, so file systems are not mounted and in use:
```

sudo smartctl -t long /dev/sda

```
[http://ubuntuforums.org/showthread.php?t=2192335](http://ubuntuforums.org/showthread.php?t=2192335) <-How to read output of smartctl?

[INDENT][INDENT]hoping for the best
[/INDENT][/INDENT]

Ok, I'll try that as soon as I get home. I'm currently at work. Thank you both for all your help and patience.

---

### Post by sinisterstuntz on 2015-01-12
[QUOTE=Bashing-om;13206152]sinisterstuntz; Well.  All we can do is try, and see what options we can come up with.  From the liveDVD, so file systems are not mounted and in use: ```
 sudo smartctl -t long /dev/sda 
``` [http://ubuntuforums.org/showthread.php?t=2192335](http://ubuntuforums.org/showthread.php?t=2192335)

---

### Post by sinisterstuntz on 2015-01-12
> **sinisterstuntz said:**
> [QUOTE=Bashing-om;13206152]sinisterstuntz; Well.  All we can do is try, and see what options we can come up with.  From the liveDVD, so file systems are not mounted and in use: ```
 sudo smartctl -t long /dev/sda 
``` [http://ubuntuforums.org/showthread.php?t=2192335](http://ubuntuforums.org/showthread.php?t=2192335)  Ok so, this isn't what i expected to get... Do i need to install something for this to work?  ```
 ubuntu@ubuntu:~$ sudo smartctl -t /dev/sda sudo: smartctl: command not found ubuntu@ubuntu:~$ sudo smartctl -t /dev/sdb sudo: smartctl: command not found ubuntu@ubuntu:~$  
```

---

### Post by Bashing-om on 2015-01-12
sinisterstuntz; Shucks, 

Not what I had anticipated .. but, what is, is ->
```

sudo apt-get install smartmontools

```

Now I bet that sucker will run .

[INDENT][INDENT][INDENT]when we 1st practice 
[/INDENT][/INDENT][/INDENT]

---

### Post by sinisterstuntz on 2015-01-12
> **Bashing-om said:**
> sinisterstuntz; Shucks, 

Not what I had anticipated .. but, what is, is ->
```

sudo apt-get install smartmontools

```

Now I bet that sucker will run .

[INDENT][INDENT][INDENT]when we 1st practice 
[/INDENT][/INDENT][/INDENT]

I did some quick searching and found that command to get it but it came back with a "bad address" error. So I downloaded the tar.gz file and tried extracting it but the tar zxvf command didn't work either.

---

### Post by Bashing-om on 2015-01-12
sinisterstuntz; Yuk;

Something stinks real bad !

Are you on a known good liveDVD ?
As the tool is there:
```

sysop@1404mini:~$ apt-cache show smartmontools
Package: smartmontools
Priority: optional
Section: utils
Installed-Size: 1611
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Original-Maintainer: Giuseppe Iuculano <iuculano@debian.org>
Architecture: amd64
Version: 6.2+svn3841-1.2
Depends: libc6 (>= 2.17), libcap-ng0, libgcc1 (>= 1:4.1.1), libselinux1 (>= 1.32), libstdc++6 (>= 4.1.1), debianutils (>= 2.2), lsb-base (>= 3.2-14)
Recommends: mailx | mailutils
Suggests: gsmartcontrol, smart-notifier
Conflicts: smartsuite, ucsc-smartsuite
Filename: pool/main/s/smartmontools/smartmontools_6.2+svn3841-1.2_amd64.deb
Size: 445284
MD5sum: d03f917eac4a51f138ea47e1bdfc10d5
>snip>

```

soooo .... What's not going on here ?

[INDENT][INDENT]when it rains
[INDENT][INDENT][INDENT]it pours
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by sinisterstuntz on 2015-01-13
> **Bashing-om said:**
> sinisterstuntz; Yuk;

Something stinks real bad !

Are you on a known good liveDVD ?
As the tool is there:
```

sysop@1404mini:~$ apt-cache show smartmontools
Package: smartmontools
Priority: optional
Section: utils
Installed-Size: 1611
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Original-Maintainer: Giuseppe Iuculano <iuculano@debian.org>
Architecture: amd64
Version: 6.2+svn3841-1.2
Depends: libc6 (>= 2.17), libcap-ng0, libgcc1 (>= 1:4.1.1), libselinux1 (>= 1.32), libstdc++6 (>= 4.1.1), debianutils (>= 2.2), lsb-base (>= 3.2-14)
Recommends: mailx | mailutils
Suggests: gsmartcontrol, smart-notifier
Conflicts: smartsuite, ucsc-smartsuite
Filename: pool/main/s/smartmontools/smartmontools_6.2+svn3841-1.2_amd64.deb
Size: 445284
MD5sum: d03f917eac4a51f138ea47e1bdfc10d5
>snip>

```

soooo .... What's not going on here ?

[INDENT][INDENT]when it rains
[INDENT][INDENT][INDENT]it pours
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

I'm using a Live USB with 14.04.1 from Ubuntu's website.

---

### Post by Bashing-om on 2015-01-13
sinisterstuntz; Welp ..

So why are you not able to talk to the default mirror site ?
What results ?
```

ping -c3 canonical.com
ping -c3 ubuntuforums.org
host us.archive.ubuntu.com

```

As the mirror is there, the package is there; must be a networking issue - somewhere:

do:
```

apt-get moo

```

Maybe
[INDENT][INDENT][INDENT]our mood will improve
[/INDENT][/INDENT][/INDENT]

---

### Post by sinisterstuntz on 2015-01-13
> **Bashing-om said:**
> sinisterstuntz; Welp ..  So why are you not able to talk to the default mirror site ? What results ? ```
 ping -c3 canonical.com ping -c3 ubuntuforums.org host us.archive.ubuntu.com 
```  As the mirror is there, the package is there; must be a networking issue - somewhere:  do: ```
 apt-get moo 
```  Maybe [INDENT][INDENT][INDENT]our mood will improve [/INDENT][/INDENT][/INDENT]  Results: ```
 ubuntu@ubuntu:~$ ping -c3 canonical.com PING canonical.com (91.189.94.156) 56(84) bytes of data. 64 bytes from vostok.canonical.com (91.189.94.156): icmp_seq=1 ttl=47 time=161 ms 64 bytes from vostok.canonical.com (91.189.94.156): icmp_seq=2 ttl=47 time=229 ms 64 bytes from vostok.canonical.com (91.189.94.156): icmp_seq=3 ttl=47 time=406 ms  --- canonical.com ping statistics --- 3 packets transmitted, 3 received, 0% packet loss, time 2003ms rtt min/avg/max/mdev = 161.197/265.935/406.701/103.413 ms ubuntu@ubuntu:~$ ping -c3 ubuntuforums.org PING ubuntuforums.org (91.189.94.12) 56(84) bytes of data. 64 bytes from feijoa.canonical.com (91.189.94.12): icmp_seq=1 ttl=47 time=226 ms 64 bytes from feijoa.canonical.com (91.189.94.12): icmp_seq=2 ttl=47 time=225 ms 64 bytes from feijoa.canonical.com (91.189.94.12): icmp_seq=3 ttl=47 time=162 ms  --- ubuntuforums.org ping statistics --- 3 packets transmitted, 3 received, 0% packet loss, time 2002ms rtt min/avg/max/mdev = 162.998/205.028/226.721/29.727 ms ubuntu@ubuntu:~$ host us.archive.ubuntu.com us.archive.ubuntu.com has address 91.189.91.13 us.archive.ubuntu.com has address 91.189.91.24 us.archive.ubuntu.com has address 91.189.91.15 us.archive.ubuntu.com has address 91.189.91.23 us.archive.ubuntu.com has IPv6 address 2001:67c:1562::13 us.archive.ubuntu.com has IPv6 address 2001:67c:1562::17 us.archive.ubuntu.com has IPv6 address 2001:67c:1562::16 us.archive.ubuntu.com has IPv6 address 2001:67c:1562::15 ubuntu@ubuntu:~$ apt-get moo                  (__)                   (oo)             /------\/            / |    ||             *  /\---/\              ~~   ~~    ..."Have you mooed today?"... ubuntu@ubuntu:~$ LOL 
```

---

### Post by Bashing-om on 2015-01-13
sinisterstuntz; Well ............

That says there is no problem !
Try again :
```

sudo apt-get install smartmontools

```
IF it comes back "smartmontools is already the newest version" ; then:
we try once more:
```

sudo smartctl -t long /dev/sda

```

As you are working from the liveDVD .. any thing installed will not persist past a reboot - can not write again to that DVD. That live environment is running in what was wrote to ram.

[INDENT][INDENT]if I knew better
[INDENT][INDENT][INDENT]I would say so
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by sinisterstuntz on 2015-01-13
ubuntu@ubuntu:~$ sudo apt-get install smartmontools Reading package lists... Error! E: Read error - read (14: Bad address) E: The package lists or status file could not be parsed or opened. ubuntu@ubuntu:~$

---

### Post by Bashing-om on 2015-01-13
sinisterstuntz; Welp:

I read :
> 
 E: The package lists or status file could not be parsed or opened. 

a) as a bad burn on the DVD
b) bad ram chips
as that file exists initially on a non-alterable medium that is copied into ram. Running with the liveDVD that is the only causes I can come up with.

Burn a new liveDVD
try again .. if still with problems ->
run the memory test that is available on that liveDVD's grub boot menu ( boot the liveDVD, soon as bios screen clears depress and hold the right -shift key -> language screen, escape key to accept defaults -> boot options screen)
let the memory test run overnight for the best results.

[INDENT][INDENT]I could be wrong,
[INDENT][INDENT][INDENT]but I do doubt it
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by Bashing-om on 2015-01-13
sinisterstuntz;Hey !

If this live environment is from a USB drive .. we might be able to fix that file - IF persistence is enabled on the file system -

[INDENT][INDENT]just another thought
[/INDENT][/INDENT]

---

### Post by sinisterstuntz on 2015-01-13
> **Bashing-om said:**
> sinisterstuntz;Hey !

If this live environment is from a USB drive .. we might be able to fix that file - IF persistence is enabled on the file system -

[INDENT][INDENT]just another thought
[/INDENT][/INDENT]

It is. How do I check persistence? If it's not enabled, how do I enable it?

---

### Post by Bashing-om on 2015-01-13
sinisterstuntz; Sheesshhh ..

caught short on knowing how to verify persistence on a USB .. 

But, try:
Boot the liveUSB to terminal:
```

sudo rm -fr /var/lib/apt/lists
sudo mkdir -pv /var/lib/apt/lists/partial
sudo apt-get update
sudo apt-get -f install
sudo apt-get upgrade

```

Now lets see if we can install:
```

sudo apt-get install smartmontools

```

[INDENT][INDENT][INDENT]maybe yes
[/INDENT][/INDENT][/INDENT]

---

### Post by sinisterstuntz on 2015-01-14
ubuntu@ubuntu:~$ sudo smartctl -t long /dev/sda smartctl 6.2 2013-07-26 r3841 [x86_64-linux-3.13.0-32-generic] (local build) Copyright (C) 2002-13, Bruce Allen, Christian Franke, [www.smartmontools.org](www.smartmontools.org)  /dev/sda: Unknown USB bridge [0x0781:0x5530 (0x200)] Please specify device type with the -d option.  Use smartctl -h to get a usage summary  ubuntu@ubuntu:~$ sudo smartctl -t long /dev/sdb smartctl 6.2 2013-07-26 r3841 [x86_64-linux-3.13.0-32-generic] (local build) Copyright (C) 2002-13, Bruce Allen, Christian Franke, [www.smartmontools.org](www.smartmontools.org)  Extended Background Self Test has begun scsiModePageOffset: response length too short, resp_len=47 offset=50 bd_len=46 Use smartctl -X to abort test ubuntu@ubuntu:~$

---

### Post by sinisterstuntz on 2015-01-14
Here's what i got:
```

ubuntu@ubuntu:~$ sudo smartctl -t long /dev/sda
smartctl 6.2 2013-07-26 r3841 [x86_64-linux-3.13.0-32-generic] (local build)
Copyright (C) 2002-13, Bruce Allen, Christian Franke, www.smartmontools.org

/dev/sda: Unknown USB bridge [0x0781:0x5530 (0x200)]
Please specify device type with the -d option.

Use smartctl -h to get a usage summary

ubuntu@ubuntu:~$ sudo smartctl -t long /dev/sdb
smartctl 6.2 2013-07-26 r3841 [x86_64-linux-3.13.0-32-generic] (local build)
Copyright (C) 2002-13, Bruce Allen, Christian Franke, www.smartmontools.org

Extended Background Self Test has begun
scsiModePageOffset: response length too short, resp_len=47 offset=50 bd_len=46
Use smartctl -X to abort test
ubuntu@ubuntu:~$ 

```

---

### Post by Bashing-om on 2015-01-14
sinisterstuntz; Yuk //

Still not looking good for the home team ..

Does 'fdisk' see the hard drive ?
```

sudo fdisk -lu

```

[INDENT][INDENT]what to do, what to do
[/INDENT][/INDENT]

---

### Post by sinisterstuntz on 2015-01-14
I would guess no:

```

ubuntu@ubuntu:~$ sudo fdisk -lu

Disk /dev/sda: 8036 MB, 8036285952 bytes
229 heads, 20 sectors/track, 3427 cylinders, total 15695871 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000a2b9f

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048    15693823     7845888    b  W95 FAT32
ubuntu@ubuntu:~$ 


```

---

### Post by Bashing-om on 2015-01-14
sinisterstuntz; Yepper, 

that do appear to be the case .. that drive is not seen.

OK, we got a bad cable ?
swap the sata cable out or swap around ?

Is there power to the drive ?
Got a volt meter handy ?

Is the bus controller good ?
Swap in a known good drive and cables and power cord
Maybe see what results 1st by hooking up to another port 

Biggy !
Is the device enabled in bios ?

[INDENT]see'n as how we do not have an o 'scope handy
[INDENT][INDENT][INDENT]make do with what we have to work with
[/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by sinisterstuntz on 2015-01-14
> **Bashing-om said:**
> sinisterstuntz; Yepper, 

that do appear to be the case .. that drive is not seen.

OK, we got a bad cable ?
swap the sata cable out or swap around ?

Is there power to the drive ?
Got a volt meter handy ?

Is the bus controller good ?
Swap in a known good drive and cables and power cord
Maybe see what results 1st by hooking up to another port 

Biggy !
Is the device enabled in bios ?

[INDENT]see'n as how we do not have an o 'scope handy
[INDENT][INDENT][INDENT]make do with what we have to work with
[/INDENT][/INDENT][/INDENT][/INDENT]

One thing that concerns me is that when we originally ran fdisk it showed the drive. Like on page one of this thread, but I'll double check everything. Maybe the cable came loose somehow.

Edit: After rebooting the system, I was able to get a result from fdisk on /dev/sdb and also able to start testdisk on that drive. Should it be ran on the windows partition, or a different one?

---

### Post by westie457 on 2015-01-14
> **sinisterstuntz said:**
> One thing that concerns me is that when we originally ran fdisk it showed the drive. Like on page one of this thread, but I'll double check everything. Maybe the cable came loose somehow.

Edit: After rebooting the system, I was able to get a result from fdisk on /dev/sdb and also able to start testdisk on that drive. Should it be ran on the windows partition, or a different one?

Hi am still here watching the thread.
Are you saying that testdisk can now see the partitions on the hard drive? How many partitions did it see after you selected the drive to look at? Also how many after the 'Quick Search' option?
Testdisk does not usually work on a partition, it was designed to work on a whole drive for various recovery operations.
If you could post a few screenshots or post the terminal output (between ```
 tags) it would be helpful.

Can you supply another [code]sudo fdisk -lu
``` please.

Tip: in the terminal highlight the text the paste between the tags.

Waiting to start the next steps. Have you made a 'SuperGrub2disk' yet, either CD or USB?

---

### Post by sinisterstuntz on 2015-01-14
> **westie457 said:**
> Hi am still here watching the thread.
Are you saying that testdisk can now see the partitions on the hard drive? How many partitions did it see after you selected the drive to look at? Also how many after the 'Quick Search' option?
Testdisk does not usually work on a partition, it was designed to work on a whole drive for various recovery operations.
If you could post a few screenshots or post the terminal output (between ```
 tags) it would be helpful.

Can you supply another [code]sudo fdisk -lu
``` please.

Tip: in the terminal highlight the text the paste between the tags.

Waiting to start the next steps. Have you made a 'SuperGrub2disk' yet, either CD or USB?

Right now I'm using my only available USB Stick for the LiveUSB. I have others but they're less than 256MB.
I'll insert screenshots I took with my phone of the partitions found. My live USB is running real sluggish right now, so this is the best I've got at the moment.

---

### Post by westie457 on 2015-01-15
@ sinisterstuntz, thanks for the photos. They both show the current partition scheme as it is now. They are showing the same partitions that were shown in your Gparted screenshot earlier in this thread, ATM there is no Ubuntu partition visible just the Backtrack one. In the second one the 'Deeper Search' option is highlighted waiting to search the whole drive for all partitions that have ever been created and wiped from the drive. Please run the Deeper Search and post the results.

---

### Post by sinisterstuntz on 2015-01-15
> **westie457 said:**
> @ sinisterstuntz, thanks for the photos. They both show the current partition scheme as it is now. They are showing the same partitions that were shown in your Gparted screenshot earlier in this thread, ATM there is no Ubuntu partition visible just the Backtrack one. In the second one the 'Deeper Search' option is highlighted waiting to search the whole drive for all partitions that have ever been created and wiped from the drive. Please run the Deeper Search and post the results.

I'm gonna assume we're at a conclusion. I tried rebooting back to the live USB and during the bios post message i got an error stating that the S.M.A.R.T. status = Bad...  I'm guessing that means the HDD's failing. If this is the case, is there a way to get my info off of the HDD? Like Windows 7?  That's all i really care about. The majority of all of my stuff was saved in that OS. I'll have to purchase a new HDD, which i wasn't looking forward to doing....but oh well, i guess.

---

### Post by westie457 on 2015-01-19
Apologies for the late reply.
Definitely not a conclusion we like. When you have your new hard drive there is several ways to hopefully get your files off the old one, in the meantime stop using the old one to minimise any data loss.

---

