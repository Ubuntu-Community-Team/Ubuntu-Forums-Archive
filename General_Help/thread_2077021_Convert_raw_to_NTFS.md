---
title: "Convert raw to NTFS"
date: 2012-10-27
forum: General Help
---

### Post by AAEIV on 2012-10-27
Hello to everyone!

A few days ago my Seagate 2TB went to raw all of a sudden. At that point I was running Vista. I typed at a cmd

```
chkdsk F: /i
```

and I got the information that my files are not NTFS but raw.
I tried to mount the HDD on my Ubuntu 10.04 system in case it works. However I got the following message

[http://i.imgur.com/GNzA9.png](http://i.imgur.com/GNzA9.png)

I then tried to fix this issue using testdisk.
The log from my first attempt is the following

```


Fri Oct 26 14:10:57 2012
Command line: TestDisk

TestDisk 6.11, Data Recovery Utility, April 2009
Christophe GRENIER <grenier@cgsecurity.org>
http://www.cgsecurity.org
OS: Linux, kernel 2.6.32-43-generic (#97-Ubuntu SMP Wed Sep 5 16:42:26 UTC 2012)
Compiler: GCC 4.4 - Jun 23 2009 17:48:38
ext2fs lib: 1.41.11, ntfs lib: 10:0:0, reiserfs lib: none, ewf lib: none
/dev/sda: LBA, HPA, LBA48, DCO support
/dev/sda: size       488281250 sectors
/dev/sda: user_max   488281250 sectors
/dev/sda: native_max 488281250 sectors
/dev/sda: dco        488281250 sectors
/dev/sdb: LBA, HPA, LBA48, DCO support
/dev/sdb: size       488281250 sectors
/dev/sdb: user_max   488281250 sectors
/dev/sdb: native_max 488281250 sectors
/dev/sdb: dco        488281250 sectors
Warning: can't get size for Disk /dev/mapper/control - 0 B - CHS 1 1 1, sector size=512
Hard disk list
Disk /dev/sda - 250 GB / 232 GiB - CHS 30394 255 63, sector size=512 - ATA WDC WD2500AAJS-7
Disk /dev/sdb - 250 GB / 232 GiB - CHS 30394 255 63, sector size=512 - ATA WDC WD2500AAJS-7


TestDisk exited normally.
```

I unmounted it and mounted again while initialising testdisk. At that point I was able to see my HDD on the list.
I pressed enter and then selected "Intel" in the "Partition Table Type". Next I pressed "Advanced" but there was a statement "No partition available". So I got back and selected "Analyse". A message was there stating that "Partition Read Error". Despite that I selected "Quick search". So something started to happening. 

I should mention that my HDD is 2000Gb while the total cylinders that testdisk could access were ~250Gb...

When this ended there was a message saying "Strucrure OK" so I selected for a "Deeper search". When this came to an end another message was stating that "No partition found or selected for recovery".

The log from this procedure is bery big ~3GB and I cannot copy it because while loading it kills itself.

I tried another time with "Advanced". At that point I saw one partition. I entered using "list" and I saw only one folder of all. The log from the previous procedure is

```

Sat Oct 27 10:51:01 2012
Command line: TestDisk

TestDisk 6.11, Data Recovery Utility, April 2009
Christophe GRENIER <grenier@cgsecurity.org>
http://www.cgsecurity.org
OS: Linux, kernel 2.6.32-42-generic (#95-Ubuntu SMP Wed Jul 25 15:56:09 UTC 2012)
Compiler: GCC 4.4 - Jun 23 2009 17:48:38
ext2fs lib: 1.41.11, ntfs lib: 10:0:0, reiserfs lib: none, ewf lib: none
/dev/sda: LBA, HPA, LBA48, DCO support
/dev/sda: size       488397168 sectors
/dev/sda: user_max   488397168 sectors
/dev/sda: native_max 488397168 sectors
/dev/sda: dco        488397168 sectors
Warning: can't get size for Disk /dev/mapper/control - 0 B - CHS 1 1 1, sector size=512
Hard disk list
Disk /dev/sda - 250 GB / 232 GiB - CHS 30401 255 63, sector size=512 - ATA WDC WD2500BEVS-2
Disk /dev/sdd - 4009 MB / 3824 MiB - CHS 1018 124 62, sector size=512 - FLASH Drive SM_USB20
Disk /dev/sde - 2000 GB / 1863 GiB - CHS 243201 255 63, sector size=512 - Seagate Desktop

Partition table type (auto): Intel
Disk /dev/sde - 2000 GB / 1863 GiB - Seagate Desktop
Partition table type: Intel

Interface Advanced
Geometry from i386 MBR: head=255 sector=63
NTFS at 0/1/1
get_geometry_from_list_part_aux head=255 nbr=2
get_geometry_from_list_part_aux head=8 nbr=1
get_geometry_from_list_part_aux head=16 nbr=1
get_geometry_from_list_part_aux head=32 nbr=1
get_geometry_from_list_part_aux head=64 nbr=1
get_geometry_from_list_part_aux head=128 nbr=1
get_geometry_from_list_part_aux head=240 nbr=1
get_geometry_from_list_part_aux head=255 nbr=2
1 P HPFS - NTFS              0   1  1 243200 254 63 3907024002 [Expansion Drive]
     NTFS, 2000 GB / 1863 GiB

ntfs_boot_sector
1 P HPFS - NTFS              0   1  1 243200 254 63 3907024002 [Expansion Drive]
     NTFS, 2000 GB / 1863 GiB
NTFS at 0/1/1
file_pread(6,16,buffer,3907024064(243200/254/63)) read err: Input/output error
filesystem size           3907024002 1
sectors_per_cluster       8 0
mft_lcn                   786432 0
mftmirr_lcn               244189000 0
clusters_per_mft_record   -10 0
clusters_per_index_record 1 0
Boot sector
Status: OK

Backup boot sector
ntfs_boot_sector: Can't read backup boot sector.
Status: Bad

Sectors are not identical.

A valid NTFS Boot sector must be present in order to access
any data; even if the partition is not bootable.
Failed to read $MFTMirr: Input/output error.
Failed to read index block: Input/output error.
Failed to read index block: Input/output error.
Failed to read index block: Input/output error.
Failed to read index block: Input/output error.
Failed to read index block: Input/output error.
Failed to read index block: Input/output error.
Failed to read index block: Input/output error.
Failed to read index block: Input/output error.
Failed to read index block: Input/output error.
Failed to read index block: Input/output error.
Failed to read index block: Input/output error.
Failed to read index block: Input/output error.
Failed to read index block: Input/output error.
ntfs_device_testdisk_io_ioctl() unimplemented
file_pread(6,8,buffer,1953512063(121600/127/63)) read err: Input/output error
ntfs_device_testdisk_io_ioctl() unimplemented
NTFS filesystem need to be repaired.

file_pread(6,8,buffer,1953512143(121600/129/17)) read err: Input/output error
ntfs_readdir failed
Directory /
       5 dr-xr-xr-x     0      0         0 25-May-2011 23:32 .
       5 dr-xr-xr-x     0      0         0 25-May-2011 23:32 ..
      62 dr-xr-xr-x     0      0         0  5-Aug-2011 22:16 ElectroMagnetism
file_pread(6,8,buffer,660335(41/26/33)) read err: Input/output error
ntfs_readdir failed
Directory /ElectroMagnetism
      62 dr-xr-xr-x     0      0         0  5-Aug-2011 22:16 .
       5 dr-xr-xr-x     0      0         0 25-May-2011 23:32 ..
ntfs_readdir failed
Directory /
       5 dr-xr-xr-x     0      0         0 25-May-2011 23:32 .
       5 dr-xr-xr-x     0      0         0 25-May-2011 23:32 ..
      62 dr-xr-xr-x     0      0         0  5-Aug-2011 22:16 ElectroMagnetism
ntfs_readdir failed
Directory /ElectroMagnetism
      62 dr-xr-xr-x     0      0         0  5-Aug-2011 22:16 .
       5 dr-xr-xr-x     0      0         0 25-May-2011 23:32 ..
ntfs_readdir failed
Directory /
       5 dr-xr-xr-x     0      0         0 25-May-2011 23:32 .
       5 dr-xr-xr-x     0      0         0 25-May-2011 23:32 ..
      62 dr-xr-xr-x     0      0         0  5-Aug-2011 22:16 ElectroMagnetism
ntfs_readdir failed
Directory /ElectroMagnetism
      62 dr-xr-xr-x     0      0         0  5-Aug-2011 22:16 .
       5 dr-xr-xr-x     0      0         0 25-May-2011 23:32 ..
ntfs_readdir failed
Directory /
       5 dr-xr-xr-x     0      0         0 25-May-2011 23:32 .
       5 dr-xr-xr-x     0      0         0 25-May-2011 23:32 ..
      62 dr-xr-xr-x     0      0         0  5-Aug-2011 22:16 ElectroMagnetism
ntfs_readdir failed
Directory /ElectroMagnetism
      62 dr-xr-xr-x     0      0         0  5-Aug-2011 22:16 .
       5 dr-xr-xr-x     0      0         0 25-May-2011 23:32 ..
ntfs_readdir failed
Directory /
       5 dr-xr-xr-x     0      0         0 25-May-2011 23:32 .
       5 dr-xr-xr-x     0      0         0 25-May-2011 23:32 ..
      62 dr-xr-xr-x     0      0         0  5-Aug-2011 22:16 ElectroMagnetism
ntfs_readdir failed
Directory /ElectroMagnetism
      62 dr-xr-xr-x     0      0         0  5-Aug-2011 22:16 .
       5 dr-xr-xr-x     0      0         0 25-May-2011 23:32 ..
ntfs_readdir failed
Directory /
       5 dr-xr-xr-x     0      0         0 25-May-2011 23:32 .
       5 dr-xr-xr-x     0      0         0 25-May-2011 23:32 ..
      62 dr-xr-xr-x     0      0         0  5-Aug-2011 22:16 ElectroMagnetism
ntfs_readdir failed
Directory /ElectroMagnetism
      62 dr-xr-xr-x     0      0         0  5-Aug-2011 22:16 .
       5 dr-xr-xr-x     0      0         0 25-May-2011 23:32 ..
ntfs_readdir failed
Directory /
       5 dr-xr-xr-x     0      0         0 25-May-2011 23:32 .
       5 dr-xr-xr-x     0      0         0 25-May-2011 23:32 ..
      62 dr-xr-xr-x     0      0         0  5-Aug-2011 22:16 ElectroMagnetism

ntfs_boot_sector
1 P HPFS - NTFS              0   1  1 243200 254 63 3907024002 [Expansion Drive]
     NTFS, 2000 GB / 1863 GiB
NTFS at 0/1/1
filesystem size           3907024002 1
sectors_per_cluster       8 0
mft_lcn                   786432 0
mftmirr_lcn               244189000 0
clusters_per_mft_record   -10 0
clusters_per_index_record 1 0
Boot sector
Status: OK

Backup boot sector
ntfs_boot_sector: Can't read backup boot sector.
Status: Bad

Sectors are not identical.

A valid NTFS Boot sector must be present in order to access
any data; even if the partition is not bootable.
Failed to read $MFTMirr: Input/output error.
```

I also wanted to try with foremost but while searching I saw that it needs to transfer "corrupted" files to another media. The thing is that my external HDD is my back-up so I don't have enough space to transfer my data...

Is it possible to access my data again?

Thank you in advance!

---

### Post by oldfred on 2012-10-27
Did you from Windows run chkdsk with the /p or /r options?

chkdsk C: /r
chkdsk /f c: 
Option 3: Adding the Windows Recovery Console as a startup option
but replace "C:" by the drive letter of your Vista partition.

You can use the following options:
/p Does an exhaustive check of the drive and corrects any errors.
/r Locates bad sectors and recovers readable information.

[http://www.microsoft.com/resources/documentation/windows/xp/all/proddocs/en-us/chkdsk.mspx?mfr=true](http://www.microsoft.com/resources/documentation/windows/xp/all/proddocs/en-us/chkdsk.mspx?mfr=true)

---

### Post by AAEIV on 2012-10-27
Thank you very much for your answer!
The problem is that the drive is raw.

When I try to use chkdsk I get the error 

`The type of the filesystem is RAW.
CHKDSK is not available for RAW drives.`

---

### Post by oldfred on 2012-10-27
In Windows RAW means it is not formated. Of course if you reformat it you lose all your data.

NTFS partitions have a backup PBR - partition boot sector. Does testdisk say the backup is damaged also?

These instructions are for those who accidentally wrote grub2's boot loader to the PBR of a NTFS partition. It uses testdisk to restore the backup PBR. so you can follow the same instrucions.

Fix for most, a few have other issues, better than windows fix in many cases as it also fixes other parameters:
If win7 use small 'system reserved' NTFS partition instead of the partition where windows was installed for win7
This has instructions on using testdisk to repair the install of grub to the boot sector for windows from Ubuntu or Linux LiveCD.
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector)
You want to get to this screen:
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step#NTFS_Boot_sector_recovery](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step#NTFS_Boot_sector_recovery)

OR:
[HowTo] Repair the bootsector of a Windows partition  - YannBuntu
[https://help.ubuntu.com/community/BootSectorFix](https://help.ubuntu.com/community/BootSectorFix)
[http://ubuntuforums.org/showthread.php?t=1926510](http://ubuntuforums.org/showthread.php?t=1926510)

Testdisk also has a function that will rebuild a basic NTFS boot sector - Rebuild BS. It is a XP type and needs to be converted to Windows Vista/7 type. But Windows Vista or 7 will not update if not already seen as NTFS as you have found out.

How to use the Bootrec.exe tool in the Windows Recovery Environment to troubleshoot and repair startup issues in Windows
[http://support.microsoft.com/kb/927392](http://support.microsoft.com/kb/927392)
[http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html](http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html)
Use bootsect.exe to repair XP & older or Vista/7 bootsectors - Use diskpart, then list volumes to see which drive to use 
bootsect.exe /nt52 c:  *compatible* with operating systems older (XP) than Windows Vista.
bootsect.exe /nt60 c:  *compatible* with Windows Vista, Windows Server 2008 or later

---

### Post by AAEIV on 2012-10-27
Thank you for your time and answer!
When I try to apply "Advanced" on testdisk I get that

No partition available

so I cannot apply a "Backup BS":(

---

### Post by oldfred on 2012-10-27
And testdisk is not showing any partitions to recover? :sad:

Then the only option may be photorec. I used photorec on a smaller drive to find a couple of missing folders (not partitions) where I saved a lot of text files. Since partition was not very full, photorec found every old deleted copy of the text files, my backup was 6 months old and it took photo 6 hours to run on my drive. Then I had a huge number of files to sort thru as it only recovers extensions not full file names. It took me weeks to compare all the text files to my backup and sync data & I never was sure I ever found last saved version. (Oldfred backs up a lot more often.)

[http://www.cgsecurity.org/wiki/PhotoRec](http://www.cgsecurity.org/wiki/PhotoRec)
[http://www.psychocats.net/ubuntucat/recoverdeletedfiles/](http://www.psychocats.net/ubuntucat/recoverdeletedfiles/)
[http://ubuntu4beginners.blogspot.com/2011/01/recover-deleted-data-using-photorec-in.html](http://ubuntu4beginners.blogspot.com/2011/01/recover-deleted-data-using-photorec-in.html)

Use scripts to help sort and rename files:
[http://www.cgsecurity.org/wiki/After_Using_PhotoRec](http://www.cgsecurity.org/wiki/After_Using_PhotoRec)
use flac tags to rename files 
[http://lglinux.blogspot.com/2008/10/use-flac-tags-to-rename-files.html](http://lglinux.blogspot.com/2008/10/use-flac-tags-to-rename-files.html)
[http://system-tricks.com/index.php/datarecovery/sort-testdisk-photorec-data-recovery-results/](http://system-tricks.com/index.php/datarecovery/sort-testdisk-photorec-data-recovery-results/)
Best GUI Indexing/Search Tool for Local Files? 
[http://ubuntuforums.org/showthread.php?t=1739701](http://ubuntuforums.org/showthread.php?t=1739701)

---

### Post by AAEIV on 2012-10-28
This could be a good idea!
As soon as I borrow a HDD I will try it and I will let you know.
Thank's!!!

---

### Post by AAEIV on 2012-11-19
I am back:guitar:

I just borrowed a HDD(sb borrowed me his laptop actually) and run photorec.

But there are no good news...:(
After some passes there are no files recovered.
The report from the procedure is the following

```
<?xml version='1.0' encoding='UTF-8'?>
<dfxml xmloutputversion='1.0'>
  <metadata 
  xmlns='http://www.forensicswiki.org/wiki/Category:Digital_Forensics_XML' 
  xmlns:xsi='http://www.w3.org/2001/XMLSchema-instance' 
  xmlns:dc='http://purl.org/dc/elements/1.1/'>
    <dc:type>Carve Report</dc:type>
  </metadata>
  <creator>
    <package>PhotoRec</package>
    <version>6.13</version>
    <build_environment>
      <compiler>GCC 4.6</compiler>
      <compilation_date>2012-02-05T07:15:52</compilation_date>
      <library name='libext2fs' version='1.42'/>
      <library name='libewf' version='none'/>
      <library name='libjpeg' version='80'/>
      <library name='libntfs' version='10:0:0'/>
    </build_environment>
    <execution_environment>
      <os_sysname>Linux</os_sysname>
      <os_release>3.2.0-33-generic</os_release>
      <os_version>#52-Ubuntu SMP Thu Oct 18 16:29:15 UTC 2012</os_version>
      <host>MITsMag</host>
      <arch>x86_64</arch>
      <uid>0</uid>
      <start_time>2012-11-19T19:04:17+0200</start_time>
    </execution_environment>
  </creator>
  <source>
    <image_filename>/dev/sdb</image_filename>
    <sectorsize>512</sectorsize>
    <device_model>Seagate Desktop</device_model>
    <image_size>2000398934016</image_size>
    <volume>
      <byte_runs>
        <byte_run offset='0' img_offset='32256' len='2000396289024'/>
      </byte_runs>
    </volume>
  </source>
  <configuration>
  </configuration>
</dfxml>
```

I don't know what else to try...

---

### Post by oldfred on 2012-11-19
Did you point it to the correct drive? It looks like it was looking at sdb?

---

### Post by AAEIV on 2012-11-20
The laptop I run photorec has only one HDD with one partition,sda that is...

I also tried foremost using

```
sudo foremost -o /home/mitsmag/Rescue -t all -i /dev/sdb
```

but it is stack at the beginning stating that

```
Processing: stdin
|
```

I took the address **/dev/sdb** as it was shown in disk utility.

---

### Post by zero2xiii on 2012-11-20
Hay,

At this point I suggest making a image of the 'bad' drive before continuing.

Throw a dd if= of= at it. As an example:
/dev/sda > Bad drive
/dev/sdb > good drive with enough space

```

sudo -i
mkdir /mount/good_drive
mount /dev/sdb1 /mount/good_drive
dd if=/dev/sda of=/mount/good_drive/bad_drive.img
```

This will take some hours to complete. Now you can continue to bang the bad drive to see if anything is still available so salvage. All the techniques I would have recommended you already tried. However there are some more advanced techniques.

Do a search for hiren's boot DVD. And get yourself a copy. I personally feel every person should have a copy handy in case of disaster. It has got some drive recovery tools on it that are brilliant! As the name states. It's a boot image. So burn to DVD, disconnect ALL drives except for DVD drive and 'bad' harddrive and throw some of those tools at it. Read all instructions very carefully. They are clear.

I would go as far as to say if you cannot get the drive to live again after trying all the extensive tools on Hiren's dvd, that the drive is unrecoverable.

Good luck :)

---

### Post by AAEIV on 2012-11-20
Thank you very much for your advice and suggestion.
The problem is that ubuntu cannot really mount the drive.

When it is plugged in from time to time there is an error message coming stating that drive cannot be mounted.

There are times that testdisk and photorec are able to see that it's mounted and others the just don't.

Maybe this is the reason that foremost is stucked...

---

### Post by Rebelli0us on 2012-11-20
Have you tried plugging/unplugging the drive, change cable, plug in different SATA port, connect to a different computer?

---

### Post by dannyboy79 on 2012-11-20
the drive doesn't have to be mounted to run dd_rescue. As long as it shows up within sudo fdisk -l, you should be able to use dd_rescue to create a giant image of the drive. COrrect me if I am wrong. Then you could mount the img and see if anything is restrievable.

---

### Post by AAEIV on 2012-11-21
I used 

```
sudo fdisk -l
```

and I got the output 

```
Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x000d2090

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048   617426943   308712448   83  Linux
/dev/sda2       617428990   625141759     3856385    5  Extended
Partition 2 does not start on physical sector boundary.
/dev/sda5       617428992   625141759     3856384   82  Linux swap / Solaris
```

I assume that Partition 2 is my corrupted disk...

I also used

```
>sudo -i
>root@MITsMag:~# mkdir /mount/dev/sda
```

where sda is my healthy drive but it doesn't seem to be working. I receive the message

```
mkdir: cannot create directory `/mount/dev/sda': No such file or directory
```

Am I doing something completely stupid here?:(

---

### Post by dannyboy79 on 2012-11-21
ok, not sure what you are trying to do anymore. You first were talking about a 2TB hard drive being converted from NTFS to RAW. Now you're talking about a 320GB hard drive. Can you please speicify what your goal is?

---

### Post by oldfred on 2012-11-21
There is no 2TB drive shown. Does BIOS show another drive. 

The sda2 partition is the extended partition. The extended partition is a container for logical partitions. Your extended currently only has one logical partition swap inside it. 

I am now very confused on what drives you have. Vista would only run from an internal drive not an external. And you are showing only one drive with 320GB and only a Linux install.

Did you totally overwrite your Vista install with Ubuntu? If testdisk cannot find old NTFS partition and photorec does not run, there is not much else that can be done that I know of. 
Others may have something else to try.

---

### Post by AAEIV on 2012-11-21
You guys are absolutely right.
Let's start over.
My external HDD crushed while I was on Vista. My laptop is dual booted into Vista and ubuntu 10.04.
I booted in ubuntu where I tried with testdisk to recover it.
Since this didn't work I wanted to try photorec and foremost.
Both require a space which is larger than the total size of data in the HDD. I didn't have such space so a friend lent me his laptop running only ubuntu 12.04 with a HDD of 320GB.

So i run ```
fdisk
``` from my friend's laptop.

**Note:**I have just found out that the OS is forever trying to mount the external HDD. every 10 min there is a message stating that "unable to mount drive".

I hope now it became a bit clear.
I am so sorry for any inconvinience...:(

---

### Post by AAEIV on 2012-11-21
I tried to run photorec again and the report remains the same as mentioned in a previous post.

After 2 passes the result is that

```
Disk /dev/sdc - 2000 GB / 1863 GiB (RO) - Seagate Desktop
     Partition                  Start        End    Size in sectors
     No partition             0   0  1 243201  80 63 3907029168 [Whole disk]


0 files saved in /home/mitsmag/recup_dir directory.
Recovery completed.
```

What is surprising to me is that while photorec was running the same message came that "unable to mount volume". You can see that the address of my HDD is sdc while the Disk utility shows sdd.
Why is this happening?

**Edit:**I tried to use disk utility just to make an action. I choose Benchmark so as to see the read rate but I get the following error message

> Error benchmarking: helper exited with exit code 1: Error opening /dev/sdd: No such device or address

---

### Post by oldfred on 2012-11-21
Did testdisk's deeper search show anything?

And photorec on a 2TB drive may take days.

---

### Post by AAEIV on 2012-11-21
At first, I pressed "Advanced" but there was a statement 

> "No partition available".

So I got back and selected "Analyse". A message was there stating that 
> "Partition Read Error".

Despite that. I selected "Quick search". So something started to happening. 

I should mention that my HDD is 2000Gb while the total cylinders that testdisk could access were ~250Gb...

When this ended there was a message saying 

> "Strucrure OK" 
so I selected for a "Deeper search". When this came to an end another message was stating that 
> "No partition found or selected for recovery".

**Edit:**Photorec just took about an hour to complete the proccess...There is somthing wrong happening...

---

### Post by dannyboy79 on 2012-11-21
based on re-reading your testdisk logs on page 1 of this thread is appears like your data is unretrievable but I could be wrong. All I know is that I can't help any further. Good luck

---

### Post by AAEIV on 2012-11-21
> **dannyboy79 said:**
> based on re-reading your testdisk logs on page 1 of this thread is appears like your data is unretrievable but I could be wrong. All I know is that I can't help any further. Good luck

That is a hit directly to the heart...
I hate to think that my files cannot be retreived...
This is my fortune we are talking about...

Anyway, thank you very much for your time and advice.

Fare well my friend...

---

### Post by oldfred on 2012-11-21
I am running out of ideas also.

Is the difference in size because this is a new 4K drive and it is being seen as 512 byte sectors?

       First, understand that most partitioning tools have moved to a policy of aligning partitions on 1 MiB (2048-sector) boundaries as a way of improving performance with some types of arrays and some types of new hard disks (those with 4096-byte physical sectors). See article by srs5694:
[http://www.ibm.com/developerworks/linux/library/l-4kb-sector-disks/](http://www.ibm.com/developerworks/linux/library/l-4kb-sector-disks/)
Post on 8-sector boundaries alignment by srs5694
[http://ubuntuforums.org/showthread.php?t=1685666](http://ubuntuforums.org/showthread.php?t=1685666)

---

### Post by AAEIV on 2012-11-21
It is a Seagate 2TB Expansion external HDD. I bought it 1.5 years ago. It's not a hi-tech drive;it needs extra power supply.

Things are getting worse if a 20k bean expert is running out of ideas...

I believe I am doomed...

---

### Post by oldfred on 2012-11-21
I just do not like one large partition on a drive, as it makes users forget to backup as they have too much data. And NTFS needs chkdsk  from a Windows install occasionally. Ubuntu often runs fsck on 40 or 60 reboots on various partitions (depends on settings). 

You can try Windows forums as they may know more about NTFS??

Will testdisk let you run a RebuildBS or rebuild the boot sector of the partition? That at best creates a default NTFS boot sector. That is a menu choice at the same screen as recover BS from backup screen.

I do not know if this does anything different than testdisk.

       GParted's partition-recovery tool.
Device -> Attempt Data Rescue in GParted

    
Back at the beginning you had this, have you never been able to get back to it?

> Disk /dev/sde - 2000 GB / 1863 GiB - CHS 243201 255 63, sector size=512 - Seagate Desktop



---

### Post by zero2xiii on 2012-11-23
> **AAEIV said:**
> It is a Seagate 2TB Expansion external HDD. I bought it 1.5 years ago. It's not a hi-tech drive;it needs extra power supply.



Yep, you might doomed.

Seagate 2TB drives suffer a VERY rare bug.. They tend to get stuck in the 'bsy' state. And is basicly bricked. It DOES affect other drives, but for some strange reason 2TB are most effected. All 7200.11 firmwares have the bug.

See these for details:
[https://sites.google.com/site/seagatefix/](https://sites.google.com/site/seagatefix/)
[http://mybroadband.co.za/vb/archive/index.php/t-220040.html](http://mybroadband.co.za/vb/archive/index.php/t-220040.html)

In short. If the drive doesn't show up in BIOS, it is basicly bricked and you wont be able to "fix" it. I have fixed drives in a busy state before. But I do have access to some high end electrical engineering equiptment and some rs232TTL converters and such.

You might try a computer shop or data recovery centre. They usualy dont charge you if they can't recover your data.

Sorry.. :(

---

### Post by AAEIV on 2012-12-27
> **zero2xiii said:**
> Yep, you might doomed.

Thank you very much:p

> **zero2xiii said:**
> If the drive doesn't show up in BIOS, it is basicly bricked and you wont be able to "fix" it.

How can I see if my drive shows up in BIOS?

I tried another action...

I've tried with the bootable CD Partition Magic but it couldn't recognise my HDD.

At first I thought of running a disk health. My device was named "Unknown" and I got the message

```
\dev/sdb failed: No such device
```

Then I tried with GParted but it couldn't find my HDD.

Finally I tried to mount it from a "mount utility" or sth like that but it couldn't be mounted.

The first time I tried I got an error

```
Run: Mount /dev/sdb
Status: Finished with error(exit status 1)
udevil: error 64: unable to determine device fstype specify with -t
```

After that there was a list of all my drives. When I selected the external one I got the error message

```
Run: Mount /dev/sdb1
Status: Finished with error(exit status 18)
Failed to write lock '/dev/sdb1' : Resource temporalily unavailable
Error opening '/dev/sdb1':Resource temporalily unavailable
Failed to mount :Resource temporalily unavailable
```

The second time I tried to mount it I got a new error message

```
Run: Mount /dev/sdb
Status: Finished with error(exit status 1)
udevil: error 57: Cannot stat /dev/sdb: No such file or directory
```

Any ideas on what's going on?

---

### Post by oldfred on 2012-12-27
I do not think you can mount a drive sda, just the partition sda1. 

Did you try the Rebuild BS from testdisk? That creates a default (XP type) NTFS partition boot sector (BS or PBR).

I have Dump highligted as I was comparing backup to current PBRs. Next to that is the Rebuild BS command.

---

### Post by AAEIV on 2012-12-28
I was trying to find how to do the " Rebuild BS" in testdisk and I thought of doing something...

After disk selection, when I should choose "type" usually I was using default "Intel".

I chose "No Type" and started a search.
It is now running but I think it is slow.
After an hour, 1% has been searched.

This means that I will need ~2.5 days to finish the whole procedure. Is this all right?
I remember when choosing "Intel" type I needed about half an hour for a search...

How long is it supposed to last in a 2TB HDD?

---

### Post by oldfred on 2012-12-28
I am sure you now are doing a low level scan, something like what photorec does. I used photorec on a much smaller drive and it took overnight to complete, so it may take that long. 

We have seen one or two users who did not partition drives and just started storing data to them. It works more as an old floppy drive, but without partitions none of the normal system tools work. Did you have partition?

Intel would normally be correct if partitioned with MBR(msdos). I have a couple of gpt partitioned drives and use the second entry for UEFI/gpt even though I do not have UEFI for those drives.

Very large drives over 2TB would normally use gpt. Ubuntu installs to empty drives over 1TB with gpt partitions. Ubuntu will boot from either gpt or MBR with either BIOS or UEFI.
But Windows only uses MBR with BIOS mode unless booting with UEFI, then only works with gpt partitioning regardless of drive size.

---

### Post by AAEIV on 2012-12-29
> **oldfred said:**
> I am sure you now are doing a low level scan, something like what photorec does. I used photorec on a much smaller drive and it took overnight to complete, so it may take that long.

So ii is typical! Relieved to hear it! 

> **oldfred said:**
> We have seen one or two users who did not partition drives and just started storing data to them. It works more as an old floppy drive, but without partitions none of the normal system tools work. Did you have partition?

No I don't... This drive is actually new. I have only used it 3 or 4 times. It was on schedule but I never partitioned it... But I believe partition is for precaution reasons, isn't that right?

> **oldfred said:**
> Intel would normally be correct if partitioned with MBR(msdos).

How can I check that?
The thing is, that when I was running testdisk, I was getting the message that there is no partition, so I thought of choosing  "no type" instead of "intel" in case there was an issue with tpye...

> **oldfred said:**
> I have a couple of gpt partitioned drives and use the second entry for UEFI/gpt even though I do not have UEFI for those drives.

Unknown words, sorry...
_GPT_ is a specific(GUID) partition table. I suppose that my HDD has the aforementioned partition table. But to be honest I don't know how to check that.

What do you mean _second entry_? 

_UEFI_ is an interface which actually controls the HDD? I thought that I control my hardware from the OS. The only interface I have for my HDD is a seagate's utility called "Seagate Dashboard" which is actually a tool for creating back up etc. I don't thing it is that sophisticated to make a partition table with that...

> **oldfred said:**
> Very large drives over 2TB would normally use gpt. Ubuntu installs to empty drives over 1TB with gpt partitions. Ubuntu will boot from either gpt or MBR with either BIOS or UEFI.
But Windows only uses MBR with BIOS mode unless booting with UEFI, then only works with gpt partitioning regardless of drive size.

This is nice info! Probably I miss something there... How can this help me? Are you implying to bot from my external HDD in order to check something?\


Sorry for my ignorance:cry::(

---

### Post by oldfred on 2012-12-29
I was trying to explain the various ways drive could be partitioned - no partitions, MBR(msdos) or gpt(GUID).

It sound like if it is a new drive and you did not specifically partition it with gparted or Windows tools, it does not have either MBR or gpt partitioning, but nothing and that eventually leads to issues as you have found. It then intially behaves somewhat like an old floppy drive which was not partitioned.

MBR(msdos) only has the one partition table in the MBR. One advantage of the new gpt partitioning is that it has two, a primary and a backup partition table. The backup is usually at the end of the drive. Gpt also has one one type of partition essentially all primary, so no 4 primary partition limit.

---

### Post by AAEIV on 2012-12-30
I wasn't aware that I should have created a partition table when I bought my drive...

Apart from what I am doing now(the low level scan) is there anything to be done? Can I for instance partition it?
Or perhaps to format it?

I cannot format it from disk utility because whenever I try to I get a message

[IMG]http://i.imgur.com/JOSMR.png[/IMG]

---

### Post by oldfred on 2012-12-30
I have seen users have issues with large drives using either Disk Utility or Windows. Best to use gparted or parted. 

Or if you want the newer gpt, use gparted and select under device, advanced and change to gpt. With gpt you can also use gdisk which is the fdisk for gpt drives. fdisk does not work on gpt partitioned drives. gdisk is in the repository. 

       gparted & fdisk instructions:
[https://help.ubuntu.com/community/InstallingANewHardDrive](https://help.ubuntu.com/community/InstallingANewHardDrive)
[https://help.ubuntu.com/community/HowtoPartition/OperatingSystemsAndPartitions](https://help.ubuntu.com/community/HowtoPartition/OperatingSystemsAndPartitions)

    
       GParted partitioning software - Full tutorial 
[http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html)
Screenshots of using gparted
[http://www.howtoforge.com/partitioning_with_gparted](http://www.howtoforge.com/partitioning_with_gparted)

---

### Post by AAEIV on 2012-12-30
The thing is that gparted cannot see the HDD.
Only disk utility can and I don't know why...

---

### Post by oldfred on 2012-12-30
With MBR the very first sector is the boot code & the partition table. If you wrote some data into the MBR all partition tools may have issues. 

If you have backed up all data, you can zero out the MBR.

I rarely suggest dd as its other nickname is Data Destroyer. Any typo and you may erase the wrong thing and there is no way to recover. Boot code is in first 440, entire boot sector including partition table is 512.

Confirm drive is sdb, as wrong drive erases partition table. if= is from, of= is to, do not ever mix them up.
```
sudo fdisk -lu
```       Zero out MBR only of sda Use 440 if windows as serial number is between 440 & 446. Use 512 to include entire sector:
```
dd if=/dev/zero of=/dev/sdb bs=512 count=1
```

Some of info above is for reference in case someone else reads thread later.
       Powerful command, but often misused and then nicknamed "dd" Data Destroyer
[http://www.linuxquestions.org/questions/linux-newbie-8/learn-the-dd-command-362506/](http://www.linuxquestions.org/questions/linux-newbie-8/learn-the-dd-command-362506/)

---

### Post by AAEIV on 2012-12-30
[QUOTE="oldfred"]If you have backed up all data, you can zero out the MBR.[/QUOTE]

Well, this problematic drive is my back up! That's what I've been trying to do in the first place. To gain my data back!
I suppose I shouldn't run dd because I will officially lose my data...

What can I do though?

---

### Post by AAEIV on 2012-12-30
I probably forgot to mention that an MBR does exist.

Secondly I would like to mention that probably my HDD while is plugged in, its address keeps changing all the time.

This image shows sdg, which means that there was a sdb, sdc,sdd,sde before! Why is this happening>

[IMG]http://i.imgur.com/vH0GD.png[/IMG]

---

### Post by oldfred on 2012-12-30
That drive is configured for MBR should mean the first sector is the MBR, but then the partition table is empty or that part of partition table is corrupt.
Do not know enough about details that if you just start writing to drive if sector 0 is written into or if reserved for MBR. It may be just opening Disk Utility or gparted is assuming MBR because you have not specified otherwise and that is default.

If it is a USB connection everytime you unmount it and mount another drive it gets a new device. It does not know it is the same device. So be sure of drive.

Change sda to whatever your current drive is.
sudo hdparm --read-sector  0 /dev/sda

Last line should end with aa55 which says it is the end of the MBR 
From my sda:
ffff fe0b ffff ce4b 06df 1676 0271 aa55

If you run this command with your drive in place of sda does it output anything? Post contents of PTsda.txt
       sudo sfdisk -d /dev/sda > PTsda.txt

---

### Post by AAEIV on 2012-12-31
> **oldfred said:**
> sudo hdparm --read-sector  0 /dev/sda

I did what you suggested but there were some issues...
First of all, it takes some time until I can see it either on disk utility or gparted. 

```
thanos@thanos-laptop:~$ sudo hdparm --read-sector 0 /dev/sdc

/dev/sdc:
reading sector 0: FAILED: Invalid exchange
```

It took some time until I got this result...

Before I do that I run fdisk. While my sda's partitions showed up instantly it took some time for the sdc, with a read error though...

```
thanos@thanos-laptop:~$ sudo fdisk -l

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xbb762c7e

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        1274    10233373+  12  Compaq diagnostics
/dev/sda2   *        1275       15855   117116928    6  FAT16
/dev/sda3           15855       29978   113445889    5  Extended
/dev/sda4           29978       30402     3399680   12  Compaq diagnostics
/dev/sda5           23150       25581    19529728   83  Linux
/dev/sda6           25581       26553     7811072   82  Linux swap / Solaris
/dev/sda7           26554       29978    27509760   83  Linux
/dev/sda8           15856       23149    58589023+   7  HPFS/NTFS

Partition table entries are not in disk order

Unable to read /dev/sdc
```

I also tried to make a partition table from gparted, but I got an error. From what I can understand, when my HDD is plugged in a USB, it takes some time until it is read, it stays there for short time and then disappears. In order to read it again I should unplug it and then plug it again...


> **oldfred said:**
> sudo sfdisk -d /dev/sda > PTsda.txt

I run this, but I got no output...

```
thanos@thanos-laptop:~$ sudo sfdisk -d /dev/sdc > PTsdc.txt
/dev/sdc: No such file or directory

sfdisk: cannot open /dev/sdc for reading
```

**EDIT:**I unpluged/pluged it and in "disk utility" the HDD showed up as free unallocated space.

I run "fdisk" and now I could see my drive!

```
thanos@thanos-laptop:~$ sudo fdisk -l

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xbb762c7e

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        1274    10233373+  12  Compaq diagnostics
/dev/sda2   *        1275       15855   117116928    6  FAT16
/dev/sda3           15855       29978   113445889    5  Extended
/dev/sda4           29978       30402     3399680   12  Compaq diagnostics
/dev/sda5           23150       25581    19529728   83  Linux
/dev/sda6           25581       26553     7811072   82  Linux swap / Solaris
/dev/sda7           26554       29978    27509760   83  Linux
/dev/sda8           15856       23149    58589023+   7  HPFS/NTFS

Partition table entries are not in disk order

Disk /dev/sdc: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x79882793

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1      243201  1953512001    7  HPFS/NTFS
```

I run again what you suggested but I got something similar

```
thanos@thanos-laptop:~$ sudo hdparm --read-sector 0 /dev/sdc
/dev/sdc: No such device or address
thanos@thanos-laptop:~$ sudo sfdisk -d /dev/sdc > PTsdc.txt
/dev/sdc: No such device or address

sfdisk: cannot open /dev/sdc for reading

```

I tried to format it in NTFS from "disk utility" but now I got a different error

```
Daemon is inhibited
```

What is this?

Before that I run

```
thanos@thanos-laptop:~$ sudo smartctl -a /dev/sdc
smartctl version 5.38 [x86_64-unknown-linux-gnu] Copyright (C) 2002-8 Bruce Allen
Home page is http://smartmontools.sourceforge.net/

Standard Inquiry (36 bytes) failed [No such device]
Retrying with a 64 byte Standard Inquiry
Standard Inquiry (64 bytes) failed [No such device]
A mandatory SMART command failed: exiting. To continue, add one or more '-T permissive' options.

```

Any idea on what's going on here, whatsoever...?

---

### Post by AAEIV on 2012-12-31
I tried some stuff in "disk utility"

[LIST=1]
[*]Start read/write benchmark
   Error message

   *A partition table was detected - write benchmarking requires the disk to be completely empty*


[*]Start Read-Only Benchmark
   Error message

   *Error benchmarking: helper exited with exit code 1: Error opening /dev/sdc: No such device or address*


[*]Safe removal
   Error message

[I]Error detaching: helper exited with exit code 1: Detaching device /dev/sdc
USB device: /sys/devices/pci0000:00/0000:00:1d.7/usb2/2-1)
Cannot open /dev/sdc: No such device or address
[/I]


[*]Mount Volume
   Error Message

[I]Error mounting: mount exited with exit code 17: Error opening '/dev/sdc1': No such device or address
Failed to mount '/dev/sdc1': No such device or address[/I]


[*]Format to ntfs
   Error message

*Error creating file system: helper exited with exit code 1: cannot open /dev/sdc1: No such device or address*


[*]Format Drive in Master Boot Record
   Error message

*Error creating partition table: helper exited with exit code 1: cannot open /dev/sdc: No such device or address*
[/LIST]

Any ideas or suggestions?

---

### Post by oldfred on 2012-12-31
IF you now do not have any data to rescue then run the dd command to totally erase MBR.

The one time you did see a partition table, did you see your data? I wish it was sudo fdisk -lu as that is to the sector detail that we could use with sfdisk to rebuild a partition table.

---

### Post by AAEIV on 2012-12-31
> **oldfred said:**
> IF you now do not have any data to rescue then run the dd command to totally erase MBR.

Unfortunately I still have data in.
Those I am trying/want to recover...

> **oldfred said:**
> The one time you did see a partition table, did you see your data?

Only this error message mentioned that there is a partition table. Whenever I try to mount my HDD, I always get an error message...

> **oldfred said:**
> I wish it was sudo fdisk -lu as that is to the sector detail that we could use with sfdisk to rebuild a partition table.

With some luck I've managed to run "fdisk -lu":p

```
thanos@thanos-laptop:~$ sudo fdisk -lu

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xbb762c7e

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1              63    20466809    10233373+  12  Compaq diagnostics
/dev/sda2   *    20467712   254701567   117116928    6  FAT16
/dev/sda3       254703614   481595391   113445889    5  Extended
/dev/sda4       481595392   488394751     3399680   12  Compaq diagnostics
/dev/sda5       371890176   410949631    19529728   83  Linux
/dev/sda6       410951680   426573823     7811072   82  Linux swap / Solaris
/dev/sda7       426575872   481595391    27509760   83  Linux
/dev/sda8       254710638   371888684    58589023+   7  HPFS/NTFS

Partition table entries are not in disk order

Disk /dev/sdc: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders, total 3907029168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x79882793

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1              63  3907024064  1953512001    7  HPFS/NTFS

```

---

### Post by oldfred on 2012-12-31
That looks like a valid partition table entry. If Windows can see that then you should be able to run chkdsk from a Windows repairCD.

New partition tools since Vista with Windows and the last couple of years of Linux gparted have started at sector 2048, XP and older version did start at sector 63. 
New 4K drives needed the 2048, but yours is not being reported as a 4K drive. Maybe that also is part of the issue?

---

### Post by AAEIV on 2012-12-31
> **oldfred said:**
> That looks like a valid partition table entry. If Windows can see that then you should be able to run chkdsk from a Windows repairCD.

The thing is that windows cannot actually see that drive...
Actually ubuntu, see it for a while and then they can't.
It looks like it's not probably inaccessible. Even if it is, this access only lasts for a while... 

Windows repair CD? I thought that this was used when a restore point needed to be brought back...

> **oldfred said:**
> New partition tools since Vista with Windows and the last couple of years of Linux gparted have started at sector 2048, XP and older version did start at sector 63. 
New 4K drives needed the 2048, but yours is not being reported as a 4K drive. Maybe that also is part of the issue?

Which of the above is best? I don't know if this is part of the issue? What's the reason for selecting a specific sector to start?

---

### Post by oldfred on 2012-12-31
If not a new 4K drive or SSD, it is not critical. But if a new drive with the 4K partitions it will be slow as it will have to open two sectors for a one sector normal write.

Does testdisk now see drive? Even if partition table says NTFS, partition boot sector needs to be also NTFS and testdisk will create the NTFS boot sector if it is still raw.

       Since drives became over 8GB CHS cylinders, heads, sectors has been obsolete and LBA is how drive is configured. For more compatibility with newer drives, 4k drives, SSDs and better configuration, partitions now start at sector 2048 rather than rounding to cylinders. With 512 bytes per sector that is 1MB at the beginning of the drive.
[http://en.wikipedia.org/wiki/Cylinder-head-sector](http://en.wikipedia.org/wiki/Cylinder-head-sector)

   First, understand that most partitioning tools have moved to a policy of aligning partitions on 1 MiB (2048-sector) boundaries as a way of improving performance with some types of arrays and some types of new hard disks (those with 4096-byte physical sectors). See article by srs5694:
[http://www.ibm.com/developerworks/linux/library/l-4kb-sector-disks/](http://www.ibm.com/developerworks/linux/library/l-4kb-sector-disks/)
Post on 8-sector boundaries alignment by srs5694
[http://ubuntuforums.org/showthread.php?tit](http://ubuntuforums.org/showthread.php?tit)'s 8-sector (4096-byte) alignment - post 8

---

### Post by AAEIV on 2013-01-01
> **oldfred said:**
> If not a new 4K drive or SSD, it is not critical. But if a new drive with the 4K partitions it will be slow as it will have to open two sectors for a one sector normal write.

I assume it's not a 4K drive. It's Seagate's expansion external HDD, which are not new in technology.

> **oldfred said:**
> Does testdisk now see drive? Even if partition table says NTFS, partition boot sector needs to be also NTFS and testdisk will create the NTFS boot sector if it is still raw.

Testdisk's behaviour is the same... It can see the HDD only if I run it while I disk starts to spin, after it has just been plugged in.

Could the problem be case's controller? I can't explain how my drive is accessible for a minute and then becomes inaccessible...

How can I figure out what's going on?

**Happy new year!:guitar:**

---

### Post by oldfred on 2013-01-01
That does now start to sound like some sort of hardware issue. Connections may be loose or drive just may be defective. A few drives do fail even when new.

---

### Post by AAEIV on 2013-01-02
> **oldfred said:**
> That does now start to sound like some sort of hardware issue. Connections may be loose or drive just may be defective. A few drives do fail even when new.

You think so?
Do you think that I should try to fix it by myself?
I've seen some tutorial on fixing seagate 7200.11 series, but I don't what exactly is my problem...

Any ideas on how to see what's going on?

---

### Post by oldfred on 2013-01-02
First test or replace cables, it may just be a loose connection with cable. Several users with internal drives solved issues just with new cables. 
Beyond that I really do not know.

---

### Post by AAEIV on 2013-01-02
You are referring to the USB cable, which connects the HDD with the laptop?

I tried to see what BIOS says about that...
When I go to the boot menu, the entry for the USB HDD is empty, something like that

```
1.USB HDD:     
```

Could that mean that it's a BSY error?

---

### Post by oldfred on 2013-01-02
If BIOS does not see it then it still is connection issue or drive issue.  And without BIOS seeing no system will see it. 
Do you have another system you can test with, or friend, neighbour, co-worker? Just to see if it works there.

---

### Post by AAEIV on 2013-01-04
So this empty entry really means that it's probably a hardware issue.
It could also be a firmware issue.
Searching the web, I saw that 7200.11 seagate series have a firmware issue.
I am tempted to fix it, but I will ask Seagate to do it for me.

The weird thing is that disk utility can actually see it;it cannot do any opperations though...

---

### Post by AAEIV on 2013-01-21
I contacted Seagate Recovery Service so as to advice me on what to do. The told me that in case it's a firmware issue their service will bee free of charge due to the running warranty.

Unfortunately they told me that there is a problem with the heads...

[https://dl.dropbox.com/u/19828093/Quote_489646-1.htm](https://dl.dropbox.com/u/19828093/Quote_489646-1.htm)

But they asked me 720€, which is a price I cannot afford in any way...

At least now I know what's going on...
Is there a way to fix it by my self?
Where can I find heads for my drive?

Or should I realise that my data are gone forever, which leaves me no other option than to ask for a new drive?

---

### Post by oldfred on 2013-01-21
That seems like a lot, but I believe they manually rebuild a new drive in a clean room with your old platters assuming heads have not damaged platters.

I did see a blog a few years ago where he bought an identical drive and manually rebuilt it himself. The assumption was that without clean room, both drives were going to be unusable but the goal was just to get one read to copy data before dust & dirt killed rebuilt drive. Not sure that can be done anymore by a user.

---

### Post by AAEIV on 2013-01-21
I have never thought of that...
It sounds interesting!!!

The thing is that I may have access to a clean room at my university...
You thing that I should give it a try?

Is it possible to find heads-set for my drive without having to buy a new hdd?

---

### Post by alphaamanitin on 2013-01-21
I doubt you will have luck finding head-sets without buying a drive.  Pretty cool your university has a clean room, but it doesn't really matter.  Your goal is not to rebuild the drive and getting it permanently working again, but to just get the data copied.  If you ask me, unless you have data you have to have, just take the loss.  That is what I had to do, it sucked, but I couldn't afford the 2100 dollars (US) to recover the data.  Keep the drive around though if it has data that you might want.  If you keep the drive nice and safe you may be able to recover data down the road when/if you have the money to do so.

AlphaA

---

### Post by AAEIV on 2013-01-21
I really need that data, that's true.
But I can't afford the 720€... at least at the moment...
I am not sure if I can buy this drive because it's an old model...
It's not available in my country anymore.

After replacing the heads, should I do something concerning the firmware?

---

### Post by oldfred on 2013-01-21
I think this is what I was remembering:
[http://hardware.slashdot.org/story/12/07/28/134201/can-a-regular-person-repair-a-damaged-hard-drive](http://hardware.slashdot.org/story/12/07/28/134201/can-a-regular-person-repair-a-damaged-hard-drive)

---

### Post by alphaamanitin on 2013-01-21
> **AAEIV said:**
> I really need that data, that's true.
But I can't afford the 720€... at least at the moment...
I am not sure if I can buy this drive because it's an old model...
It's not available in my country anymore.

After replacing the heads, should I do something concerning the firmware?

I sent mine to Drive Savers, they pay for the overnight shipping to them, will review it for free and shoot you a price, and offer payment plans.  The payment plans suck, only spread out over three months.  However, if you are a student they might be willing to give you a discount, they offered me one but it was still too expensive for my poor grad student butt.  If you chose not to, they will overnight the drive back to you for free (or at least in the USA I should say for shipping).  They were nice and professional.  

AlphaA

---

### Post by AAEIV on 2013-01-22
I really doubt if this can apply to me...becuase it's going to be an oversea shipping from USA to Greece.

My contact person to seagate actually offered me a discount...
Starting price was 940€ and he provided me a 140€ discount, meaning 800€ plus 10% morew meaning 720€.

He also told me to split the price into 4 parts with no additional interest and if I cannot pay every month he offered me a time range of 6 months...

But still it's too much for me.

Just to give you a hint, I need about two weeks to find the shipping price, which is 40€...

---

### Post by AAEIV on 2013-01-22
Just for the record, Seagate reports

[QUOTE="Seagate"]We have finished examining all physical and logical components of your storage media. The main cause of damage is bad blocks which are present on the media, as well as media surface damage which prevents the read write heads from locating the data stored on the platters.
For the recovery process we need to analyze and repair these bad blocks, read out all data on a sector level, and reconstruct the complete file system. Afterwards we will mount the data onto an offline server in order to check the integrity of your data(partitions, directories and the different file types).

Evaluation report:

Drive very unstable Heads#5 very unstable Present many media errors, heads unstable read. Probably later need explant new heads.[/QUOTE]

---

### Post by oldfred on 2013-01-22
If the heads are working you can do most of that yourself. It just is how bad is drive? Once mechanically so bad then there is nothing you can do. 

You can do an image back up, and run e2fsck to clear bad blocks or chkdsk if NTFS. You may be able to run photorec and recover a lot of data also.

       [https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)
[http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)

    
Several of the tools shown in DataRecovery link are identical or similar to the tools they use.

---

### Post by AAEIV on 2013-01-23
The thing is that this drive couldn't be accessed.
As a result no operation could be applied there...

Seagate claimed that this issue could be fixed by **analyzing and repairing these bad blocks, reading out all data on a sector level, and reconstructing the complete file system.**

How can this be done?

---

### Post by oldfred on 2013-01-23
Perhaps it was like some of the links where just a new PC board was required. Maybe a bad PC board caused some of the damage.

Did you try any of the old last thing to try like freezing, thumping or others that may temporarily let you read something?

---

### Post by CharlesA on 2013-01-23
> **AAEIV said:**
> I really need that data, that's true.
But I can't afford the 720€... at least at the moment...


If you have valuable data, keep regular backups of it. I've lost data before and data recovery was going to cost several thousand dollars, so I just used it as a learning experience.

> **AAEIV said:**
> The thing is that this drive couldn't be accessed.
As a result no operation could be applied there...

If it is detected by the BIOS, you might be able to use ddrescue to copy it to another drive, but if the data is unreadable, you are probably still going to be stuck.

Personally, I would do the data recovery if the data is that important, even though it costs a ton.

---

### Post by alphaamanitin on 2013-01-23
> **CharlesA said:**
> If you have valuable data, keep regular backups of it. I've lost data before and data recovery was going to cost several thousand dollars, so I just used it as a learning experience.



If it is detected by the BIOS, you might be able to use ddrescue to copy it to another drive, but if the data is unreadable, you are probably still going to be stuck.

Personally, I would do the data recovery if the data is that important, even though it costs a ton.

He doesn't have the funds, period.  He said earlier that it would take him two weeks to work up the 40 euro shipping fee.  He is simply, SOL.  Per the quote sent by Seagate, "physical damage to the surface" is part of the problem.  I don't think he will be able to recover anything, even using ddrescue.  Nevertheless, as he simply doesn't have the money it may be worth trying ddrescue even if it destroys the drive while doing it.  It does seem that he will not be able to pay to recover data, and unless the data can wait years for recovery...

AlphaA

---

### Post by AAEIV on 2013-01-24
> **oldfred said:**
> Perhaps it was like some of the links where just a new PC board was required. Maybe a bad PC board caused some of the damage.

Did you try any of the old last thing to try like freezing, thumping or others that may temporarily let you read something?

To be honest I didn't try freezing or thumbing(I believe you mean pusing down the drive with my hand).
Two day ago I saw a video of a woman putting her hdd to the freezer for an hour and this method worked!!! 
I will try it as soon as I get the drive back.



> **CharlesA said:**
> If you have valuable data, keep regular backups of it. I've lost data before and data recovery was going to cost several thousand dollars, so I just used it as a learning experience.



If it is detected by the BIOS, you might be able to use ddrescue to copy it to another drive, but if the data is unreadable, you are probably still going to be stuck.

Personally, I would do the data recovery if the data is that important, even though it costs a ton.

The thing is that I learned a lot during this period because of this issue...
TO run ddrescue the hdd has to be in the list when running "sudo fdisk -l", which is not the case right here...
It really costs a ton;I will have to wait ~2years to find that money...


> **alphaamanitin said:**
> He doesn't have the funds, period.  He said earlier that it would take him two weeks to work up the 40 euro shipping fee.  He is simply, SOL.  Per the quote sent by Seagate, "physical damage to the surface" is part of the problem.  I don't think he will be able to recover anything, even using ddrescue.  Nevertheless, as he simply doesn't have the money it may be worth trying ddrescue even if it destroys the drive while doing it.  It does seem that he will not be able to pay to recover data, and unless the data can wait years for recovery...

AlphaA

What is a SOL?
Can ddrescue destroy the drive?How?

---

### Post by CharlesA on 2013-01-24
> **AAEIV said:**
> To be honest I didn't try freezing or What is a SOL?
Can ddrescue destroy the drive?How?

It means "Out of luck" with a few extra words.

If you don't see the drive in fdisk, I don't think ddrescue will work.

At least you have gotten a lesson on why keeping backups of your data is a good idea. ;)

---

### Post by AAEIV on 2013-01-25
> **CharlesA said:**
> At least you have gotten a lesson on why keeping backups of your data is a good idea. ;)

Yes but that's a hard lesson...

---

### Post by CharlesA on 2013-01-25
> **AAEIV said:**
> Yes but that's a hard lesson...
True, but I bet you will never forget it now. ;)

I'm sure everyone has lost data at one time or another. I know I have and that is why I am super critical about having my data backed up. :)

---

### Post by AAEIV on 2013-01-26
I tried yesterday to dissasemble  an already damaged drive.
I noticed something weird...

I was pusshing down the heand, intentially...
The weird thing is that the head could only touch the platters if I push it in the very edge...

Also the dissmantle proccess wasn't that sensitive...
Just some screws, and some elementary attention...
Nothing more...

---

### Post by oldfred on 2013-01-26
Heads never touch platter. If they do then it damages platter and destroys drive. One of the major failure modes. They are called flying heads and read the magnetic bits while flying over them.

Only when parked outside the read area may the heads settle.

[http://en.wikipedia.org/wiki/Disk_read-and-write_head](http://en.wikipedia.org/wiki/Disk_read-and-write_head)

---

