---
title: "UNEXPECTED INCONSISTENCY - run fsck manually"
date: 2017-08-08
forum: General Help
---

### Post by oygle on 2017-08-08
Today I booted up Kubuntu 16.04.2 LTS and it just hung. So, booted to 4.4.0.89 recovery mode; quite a few message about the hard drive.

```

dev/sda1/ UNEXPECTED INCONSISTENCY; RUN fsck MANUALLY
fsck excited with status code 4
Failure: File system check of the root filesystem failed
The root filesystem on /dev/sda1 requires a manual fsck

```

I was able to use a USB .iso and can boot to that okay. Can browse the hard drives. I do have smartmon installed; not sure if that helps.

What fsck command do I use please ?

Edit: extra info - I got the computer in 2008, so the main HDD is at least that old (plus ram and other hardware), and the 2nd HDD is way beyond that. Possibly 12 years or more.

---

### Post by oygle on 2017-08-08
This answer at [https://askubuntu.com/questions/812614/error-unexpected-inconsistency-run-fsck-manually](https://askubuntu.com/questions/812614/error-unexpected-inconsistency-run-fsck-manually)  indicates it should be done with a Live CD (or a USB I assume) :

> 


To avoid data loss due to disk failure, this command should be given from a live Ubuntu session. Follow these steps:

    You should burn a live Ubuntu CD.
    Insert the live CD and try Ubuntu without installing.

    Open a terminal and type the following command:

    sudo fsck /dev/sda1  

    When prompted, type y to fix the errors.

That should be all. Your system will boot normally once this fix has been applied.

Source: [https://askubuntu.com/users/158442/muru](https://askubuntu.com/users/158442/muru)


Is it safer to do it from another boot media ? (CD , USB)

---

### Post by Bashing-om on 2017-08-09
oygle; Hey;

The purpose is that the target for fsck is static . Thus from a alternate install ( DVD/USB/partition).
The target must not be mounted .


So long as the target is UNmounted, does not matter where fsck is run from.

[INDENT][INDENT]hope this helps
[/INDENT][/INDENT]

---

### Post by oygle on 2017-08-09
> **Bashing-om said:**
> oygle; Hey;

The purpose is that the target for fsck is static . Thus from a alternate install ( DVD/USB/partition).
The target must not be mounted .


So long as the target is UNmounted, does not matter where fsck is run from.

[INDENT][INDENT]hope this helps
[/INDENT][/INDENT]

Thanks 'Bashing-om'. I booted from the USB, then unmounted and ran fsck. Hundreds of errors; I should have set the 'yes' option.  lol

Anyway, it eventually finished and said there were no errors. So I unmounted 2 other partitions and ran fsck on them, but there were reported 'clean'. I guess the good thing about the partition that had errors is that it is /root and only has software on it, so it would seem all my data is okay. I then rebotted, Kubuntu taking a very long time, and I see the keyboard lights flashing. Did some searching and a few posts suggest it is hardware failure. Some posts said to run memtest, so am running that now. After about 5 mins though, memtest has found one bad address.

I got the computer in 2008, so the main HDD is at least that old (plus ram and other hardware), and the 2nd HDD is way beyond that. Possibly 12 years or more.

Hmmm, ....

---

### Post by oygle on 2017-08-09
I cancelled the memtest after it found 1 error. Booted into recovery mode and the lights are flashing (3 lights) and it just hangs ..

> Kernel panic - not synching: Attempted to kill init: exitcode=0x00007f00

I guess it's time to get a new computer.  lol  :)

---

### Post by Bashing-om on 2017-08-09
oygle; Maybe ;

End of that box .
But ram is cheap and hard drive too .

What do you get from:
```

sudo e2fsck -f -y -v /dev/sdXY

```
where X is the drive (a,b or c) and Y is the partition number ( 1, 2 4 ....)

[INDENT][INDENT]no quit in us
[/INDENT][/INDENT]

---

### Post by oygle on 2017-08-09
> **Bashing-om said:**
> oygle; Maybe ;

End of that box .
But ram is cheap and hard drive too .

What do you get from:
```

sudo e2fsck -f -y -v /dev/sdXY

```
where X is the drive (a,b or c) and Y is the partition number ( 1, 2 4 ....)



Thanks for that command; I'll try it tomorrow. Probably best ti unmount first as this article states - [http://linux.101hacks.com/unix/e2fsck/](http://linux.101hacks.com/unix/e2fsck/) . The computer was very powerful when I bought it, and I have had no problems with it at all, an Asus P5QL PRO - [https://www.asus.com/Motherboards/P5QL_PRO/specifications/](https://www.asus.com/Motherboards/P5QL_PRO/specifications/)

Seems ram would only be $40 for 4 new sticks of 1Gb each, and there are 1TB drives for about $70. Not sure if the motherboard will be able to map properly with anything over 500 Gb though ?? I can check on the asus forums possibly.  Thanks  :)

---

### Post by Bashing-om on 2017-08-09
oygle; Well.

Single processor - will struggle for a heavy desk top but I would expect a lighter distro to run just fine . say lubuntu or xubuntu. 
2 500 Gig drives rather than a single drive that will also at some point fail such that there is an onboard backup when the drive fails . All hard drives will fail, just a matter of time .
As the main board supports raid I bet you can get an SSD functional ! Now an SSD will get ya a huge performance increase .

[INDENT][INDENT]just some thoughts
[/INDENT][/INDENT]

---

### Post by oygle on 2017-08-09
> **Bashing-om said:**
> 
Single processor - will struggle for a heavy desk top but I would expect a lighter distro to run just fine . say lubuntu or xubuntu. 

Sorry I supplied the wrong mobo, it is an ASUS P5QL PRO - [https://www.asus.com/Motherboards/P5QL_PRO/specifications/](https://www.asus.com/Motherboards/P5QL_PRO/specifications/) , but not sure if that is still a single processor.  Yes, have plans to wipe Kubuntu and install lubuntu, as you say.  :)

> **Bashing-om said:**
> 
2 500 Gig drives rather than a single drive that will also at some point fail such that there is an onboard backup when the drive fails . All hard drives will fail, just a matter of time .
As the main board supports raid I bet you can get an SSD functional ! Now an SSD will get ya a huge performance increase .

Yes it does RAID, but I'm mindful of power consumption. Although I see from this article ( [http://www.tomshardware.com/forum/267776-32-hard-drive-power-consumption](http://www.tomshardware.com/forum/267776-32-hard-drive-power-consumption) ), that (say) 10 watts is all a HDD will consume. My thinking was replace 2 old HDD's with a new 1TB and say 8 to 10 watts. :)

---

### Post by Bashing-om on 2017-08-09
oygle; Hey ..

that ^ motherboard is not too shabby - can run what ever you want on it .
I am sold on the performance increase that a SSD provides . and I am a believer in backups and redundancy . 2 drives !
> 
4 x DIMM, Max. 16 GB,

If you are going to maintain this box for the foreseeable future - give it the love it wants and install 16 Gigs of ram ! I have never ever encountered too much ram :)

With a bit of love that system will be functionable for a while yet !

[INDENT][INDENT]what works, works
[/INDENT][/INDENT]

---

### Post by oygle on 2017-08-09
> **Bashing-om said:**
> 
What do you get from:
```

sudo e2fsck -f -y -v /dev/sdXY

```
where X is the drive (a,b or c) and Y is the partition number ( 1, 2 4 ....)


```

$ sudo e2fsck -f -y -v /dev/sda1
e2fsck 1.42.13 (17-May-2015)
Pass 1: Checking inodes, blocks, and sizes
Pass 2: Checking directory structure
Pass 3: Checking directory connectivity
Pass 4: Checking reference counts
Pass 5: Checking group summary information

      498491 inodes used (37.96%, out of 1313280)
          70 non-contiguous files (0.0%)
         425 non-contiguous directories (0.1%)
             # of inodes with ind/dind/tind blocks: 0/0/0
             Extent depth histogram: 464041/51
     2414898 blocks used (46.06%, out of 5242880)
           0 bad blocks                                                                                                                                                            
           1 large file                                                                                                                                                            
                                                                                                                                                                                   
      381946 regular files                                                                                                                                                         
       77266 directories                                                                                                                                                           
          55 character device files                                                                                                                                                
          25 block device files                                                                                                                                                    
           0 fifos                                                                                                                                                                 
          21 links                                                                                                                                                                 
       39184 symbolic links (34305 fast symbolic links)                                                                                                                            
           6 sockets                                                                                                                                                               
------------                                                                                                                                                                       
      498503 files                                                                                                                                                                 
kubuntu@kubuntu:~$
```

I'm not convinced it is a ram problem, as the same message appears with different ram sticks. It is the "kernel panic" that needs to be addressed. That msg only started to appear after the fsck was done. Now possibly there are files that are part of the kernel that need repairing ??

---

### Post by vasa1 on 2017-08-09
> **oygle said:**
> ...
I got the computer in 2008, so the main HDD is at least that old (plus ram and other hardware), and the 2nd HDD is way beyond that. Possibly 12 years or more.
...
If you like, you could add this information to the very first post in the thread. I think it would help having it there.

---

### Post by oygle on 2017-08-09
> **vasa1 said:**
> If you like, you could add this information to the very first post in the thread. I think it would help having it there.

Thanks, ..done.  :)

---

### Post by Bashing-om on 2017-08-09
oygle; Well;

> 
 It is the "kernel panic" that needs to be addressed. 

what results booting up other kernels ?
What about booting a liveDVD(USB) ?

[INDENT]fault isolation
[INDENT][INDENT][INDENT]spare it off
[/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by oygle on 2017-08-09
> **Bashing-om said:**
> 
what results booting up other kernels ?
What about booting a liveDVD(USB) ?


Other kernels, same problem, same messages. Live USB boots just fine, I can browse both of those HDD's.

---

### Post by Bashing-om on 2017-08-09
oygle; Humm;

> 
Other kernels, same problem, same messages. 

says not a kernel issue

> 
 Live USB boots just fine, 

says a hard drive/hardware issue .

What are we working with ?
post back:
```

sudo fdisk -lu
sudo parted -l
sudo blkid
cat /etc/fstab
cat /etc/default/grub

```
[INDENT][INDENT]poke at it long enough, hard enough
[INDENT][INDENT][INDENT]will find the cause
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

Were me

---

### Post by oygle on 2017-08-09
The results from those commands ..

```

$ **sudo fdisk -lu** 
Disk /dev/ram0: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes

Disk /dev/ram1: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes

Disk /dev/ram2: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes

Disk /dev/ram3: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes

Disk /dev/ram4: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes

Disk /dev/ram5: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes

Disk /dev/ram6: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes

Disk /dev/ram7: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes

Disk /dev/ram8: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes

Disk /dev/ram9: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes

Disk /dev/ram10: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes

Disk /dev/ram11: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes

Disk /dev/ram12: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes

Disk /dev/ram13: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes

Disk /dev/ram14: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes

Disk /dev/ram15: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes

Disk /dev/loop0: 1.4 GiB, 1485787136 bytes, 2901928 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes

Disk /dev/sda: 465.8 GiB, 500107862016 bytes, 976773168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0x0009cba2

Device     Boot    Start       End   Sectors   Size Id Type
/dev/sda1  *          63  41945714  41945652    20G 83 Linux
/dev/sda2       41945715  50347709   8401995     4G 82 Linux swap / Solaris
/dev/sda3       50347710 976768064 926420355 441.8G 83 Linux

Disk /dev/sdb: 232.9 GiB, 250059350016 bytes, 488397168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0x0b410b41

Device     Boot Start       End   Sectors   Size Id Type
/dev/sdb1  *       63 488392064 488392002 232.9G 83 Linux

Disk /dev/sdc: 3.7 GiB, 4005560320 bytes, 7823360 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0x17d962b7

Device     Boot   Start     End Sectors  Size Id Type
/dev/sdc1  *          0 3002879 3002880  1.4G  0 Empty
/dev/sdc2       2982352 2987087    4736  2.3M ef EFI (FAT-12/16/32)

Disk /dev/sde: 29 GiB, 31104958464 bytes, 60751872 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0x00000000

Device     Boot Start      End  Sectors Size Id Type
/dev/sde1       21920 60751871 60729952  29G  c W95 FAT32 (LBA)

$ **sudo parted -l **             
Model: ATA ST3500320AS (scsi)
Disk /dev/sda: 500GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos
Disk Flags: 

Number  Start   End     Size    Type     File system     Flags
 1      32.3kB  21.5GB  21.5GB  primary  ext4            boot
 2      21.5GB  25.8GB  4302MB  primary  linux-swap(v1)
 3      25.8GB  500GB   474GB   primary  ext4


Model: ATA ST3250310AS (scsi)
Disk /dev/sdb: 250GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos
Disk Flags: 

Number  Start   End    Size   Type     File system  Flags
 1      32.3kB  250GB  250GB  primary  ext4         boot


Warning: The driver descriptor says the physical block size is 2048 bytes, but
Linux says it is 512 bytes.
Ignore/Cancel? i                                                          
Model: Kingston DataTraveler 2.0 (scsi)
Disk /dev/sdc: 16.0GB
Sector size (logical/physical): 2048B/512B
Partition Table: mac
Disk Flags: 

Number  Start   End     Size    File system  Name   Flags
 1      2048B   6143B   4096B                Apple
 2      1527MB  1529MB  2425kB               EFI


Model: SanDisk Ultra (scsi)
Disk /dev/sde: 31.1GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos
Disk Flags: 

Number  Start   End     Size    Type     File system  Flags
 1      11.2MB  31.1GB  31.1GB  primary  fat32        lba


$ **sudo blkid**
/dev/sda1: UUID="855c6698-a72d-4cc5-8b7e-3dee0c8b7fca" TYPE="ext4" PARTUUID="0009cba2-01"
/dev/sda3: UUID="4925dcbd-b2a1-4db6-adc0-69a9f05ad473" TYPE="ext4" PARTUUID="0009cba2-03"
/dev/sdb1: LABEL="kubuntu2" UUID="79731916-952b-4d88-b6d4-40e81b15731d" TYPE="ext4" PARTUUID="0b410b41-01"
/dev/loop0: TYPE="squashfs"
/dev/sda2: UUID="82e48eb2-0c33-4696-9154-d921da42bbd2" TYPE="swap" PARTUUID="0009cba2-02"
/dev/sdc1: UUID="2016-07-19-21-08-55-00" LABEL="Kubuntu 16.04.1 LTS amd64" TYPE="iso9660" PTUUID="17d962b7" PTTYPE="dos" PARTUUID="17d962b7-01"
/dev/sdc2: SEC_TYPE="msdos" UUID="0F7B-9366" TYPE="vfat" PARTUUID="17d962b7-02"
/dev/sde1: UUID="4E49-ECAD" TYPE="vfat"

$ **cat /etc/fstab**
overlay / overlay rw 0 0
tmpfs /tmp tmpfs nosuid,nodev 0 0

$ **cat /etc/default/grub**
# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.
# For full documentation of the options in this file, see:
#   info -f grub -n 'Simple configuration'

GRUB_DEFAULT=0
GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""

# Uncomment to enable BadRAM filtering, modify to suit your needs
# This works with Linux (no patch required) and with any kernel that obtains
# the memory map information from GRUB (GNU Mach, kernel of FreeBSD ...)
#GRUB_BADRAM="0x01234567,0xfefefefe,0x89abcdef,0xefefefef"

# Uncomment to disable graphical terminal (grub-pc only)
#GRUB_TERMINAL=console

# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
#GRUB_GFXMODE=640x480

# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID=true

# Uncomment to disable generation of recovery mode menu entries
#GRUB_DISABLE_RECOVERY="true"

# Uncomment to get a beep at grub start
#GRUB_INIT_TUNE="480 440 1"
$ 

```

---

### Post by Bashing-om on 2017-08-10
oygle; Oh Me;

You lost me - I know nothing of an overlay file system.
I do not see how in /etc/fstab that there are provisions for the upper and lower directories.
A normal fstab:
> 
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sda1 during installation
UUID=d9c2a8e6-d014-42a6-846f-7e7892f4aef5 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=44f3493e-30f0-46c5-af38-ce8dcc8e8ebc none            swap    sw              0       0

I am clueless how a overlay file system works and can offer no further advise,

Perhaps others here can jump in and assist, From the examples I have seen your fstab is incorrect .

[INDENT]but what do I know -
[/INDENT]

---

### Post by oygle on 2017-08-10
> **Bashing-om said:**
> 
You lost me - I know nothing of an overlay file system.
I do not see how in /etc/fstab that there are provisions for the upper and lower directories.
A normal fstab:

I am clueless how a overlay file system works and can offer no further advise,

Perhaps others here can jump in and assist, From the examples I have seen your fstab is incorrect .

Yes, I agree. The file fstab is usually way bigger than that.

I can boot okay to the Live usb. What would happen if I did the install ? Will it overwrite all the data ? My backups are not recent.  :(

---

### Post by Bashing-om on 2017-08-10
oygle; Welp ;

A re-install will overwrite in your current setup .
I am not convinced a re-install is requited.
Why a overlay file system ??  Can you not run the standard ext4 file system ?

I have the notion your issues stem from an overlay set up - but I have no experience to know .

[INDENT]maybe this
[INDENT][INDENT][INDENT]might be that
[/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by oygle on 2017-08-11
> **Bashing-om said:**
> 
Why a overlay file system ??  Can you not run the standard ext4 file system ?

I have the notion your issues stem from an overlay set up - but I have no experience to know .


Hmm, unless Kubuntu 'thinks' it is an overlay system ?? There are 2 HDD's. The primary is 500Gb and it has 2 partitions; both of those partitions are ext4. The other HDD is an old 250Gb drive used in windows, so it probably returns 'dos' as the filesystem.

Out of the hundreds of files that had to be moved, I remember 'modprobe' was one, and I see it is used for the kernel.

Thanks  :)

Edit:  Possibly all the 'overlay' (referenced in /etc/fstab/ file ) is what happens on a Live usb Boot ?

---

### Post by oygle on 2017-08-11
Have been reading other posts in regards to 'kernel panic'. Here is the bootinfo results ..

```

                  Boot Info Script 0.61      [1 April 2012]


============================= Boot Info Summary: ===============================

 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    in partition 97 for .
 => Windows is installed in the MBR of /dev/sdb.
 => No known boot loader is installed in the MBR of /dev/sdc.
 => No boot loader is installed in the MBR of /dev/sdd.

sda1: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  Ubuntu 16.04.3 LTS
    Boot files:        /boot/grub/grub.cfg /etc/fstab

sda2: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info: 

sda3: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  
    Boot files:        

sdb1: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  
    Boot files:        

sdc1: __________________________________________________________________________

    File system:       iso9660
    Boot sector type:  Unknown
    Boot sector info: 
    Mounting failed:   mount: /dev/sdc1 is already mounted or /tmp/BootInfo-WBOgtPk3/sdc1 busy

sdc2: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  FAT16
    Boot sector info:  According to the info in the boot sector, sdc2 starts 
                       at sector 0. But according to the info from fdisk, 
                       sdc2 starts at sector 2982352. According to the info 
                       in the boot sector, sdc2 has 0 sectors.
    Mounting failed:   mount: /dev/sdc1 is already mounted or /tmp/BootInfo-WBOgtPk3/sdc1 busy
mount: /dev/sdc2 is already mounted or /tmp/BootInfo-WBOgtPk3/sdc2 busy

sdd1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  -
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________
Disk /dev/sda: 465.8 GiB, 500107862016 bytes, 976773168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *             63    41,945,714    41,945,652  83 Linux
/dev/sda2          41,945,715    50,347,709     8,401,995  82 Linux swap / Solaris
/dev/sda3          50,347,710   976,768,064   926,420,355  83 Linux


Drive: sdb _____________________________________________________________________
Disk /dev/sdb: 232.9 GiB, 250059350016 bytes, 488397168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1    *             63   488,392,064   488,392,002  83 Linux


Drive: sdc _____________________________________________________________________
Disk /dev/sdc: 3.7 GiB, 4005560320 bytes, 7823360 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdc1    *              0     3,002,879     3,002,880   0 Empty
/dev/sdc2           2,982,352     2,987,087         4,736  ef EFI (FAT-12/16/32)

/dev/sdc1 overlaps with /dev/sdc2

GUID Partition Table detected, but does not seem to be used.

Partition    Start Sector    End Sector  # of Sectors System
/dev/sdc1               0     3,002,823     3,002,824 Data partition (Windows/Linux)
/dev/sdc2       2,982,352     2,987,087         4,736 Data partition (Windows/Linux)

Drive: sdd _____________________________________________________________________
Disk /dev/sdd: 29 GiB, 31104958464 bytes, 60751872 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdd1              21,920    60,751,871    60,729,952   c W95 FAT32 (LBA)


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda1        855c6698-a72d-4cc5-8b7e-3dee0c8b7fca   ext4       
/dev/sda2        82e48eb2-0c33-4696-9154-d921da42bbd2   swap       
/dev/sda3        4925dcbd-b2a1-4db6-adc0-69a9f05ad473   ext4       
/dev/sdb1        79731916-952b-4d88-b6d4-40e81b15731d   ext4       kubuntu2
/dev/sdc1        2016-07-19-21-08-55-00                 iso9660    Kubuntu 16.04.1 LTS amd64
/dev/sdc2        0F7B-9366                              vfat       
/dev/sdd1        4E49-ECAD                              vfat       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sda1        /media/kubuntu/855c6698-a72d-4cc5-8b7e-3dee0c8b7fca ext4       (rw,nosuid,nodev,relatime,data=ordered,uhelper=udisks2)
/dev/sda3        /media/kubuntu/4925dcbd-b2a1-4db6-adc0-69a9f05ad473 ext4       (rw,nosuid,nodev,relatime,data=ordered,uhelper=udisks2)
/dev/sdc         /cdrom                   iso9660    (ro,noatime)
/dev/sdd1        /media/kubuntu/4E49-ECAD vfat       (rw,nosuid,nodev,relatime,uid=999,gid=999,fmask=0022,dmask=0022,codepage=437,iocharset=iso8859-1,shortname=mixed,showexec,utf8,flush,errors=remount-ro,uhelper=udisks2)


=========================== sda1/boot/grub/grub.cfg: ===========================

--------------------------------------------------------------------------------
#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s $prefix/grubenv ]; then
  set have_grubenv=true
  load_env
fi
if [ "${next_entry}" ] ; then
   set default="${next_entry}"
   set next_entry=
   save_env next_entry
   set boot_once=true
else
   set default="0"
fi

if [ x"${feature_menuentry_id}" = xy ]; then
  menuentry_id_option="--id"
else
  menuentry_id_option=""
fi

export menuentry_id_option

if [ "${prev_saved_entry}" ]; then
  set saved_entry="${prev_saved_entry}"
  save_env saved_entry
  set prev_saved_entry=
  save_env prev_saved_entry
  set boot_once=true
fi

function savedefault {
  if [ -z "${boot_once}" ]; then
    saved_entry="${chosen}"
    save_env saved_entry
  fi
}
function recordfail {
  set recordfail=1
  if [ -n "${have_grubenv}" ]; then if [ -z "${boot_once}" ]; then save_env recordfail; fi; fi
}
function load_video {
  if [ x$feature_all_video_module = xy ]; then
    insmod all_video
  else
    insmod efi_gop
    insmod efi_uga
    insmod ieee1275_fb
    insmod vbe
    insmod vga
    insmod video_bochs
    insmod video_cirrus
  fi
}

if [ x$feature_default_font_path = xy ] ; then
   font=unicode
else
insmod part_msdos
insmod ext2
set root='hd0,msdos1'
if [ x$feature_platform_search_hint = xy ]; then
  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos1 --hint-efi=hd0,msdos1 --hint-baremetal=ahci0,msdos1  855c6698-a72d-4cc5-8b7e-3dee0c8b7fca
else
  search --no-floppy --fs-uuid --set=root 855c6698-a72d-4cc5-8b7e-3dee0c8b7fca
fi
    font="/usr/share/grub/unicode.pf2"
fi

if loadfont $font ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
if [ "${recordfail}" = 1 ] ; then
  set timeout=30
else
  if [ x$feature_timeout_style = xy ] ; then
    set timeout_style=menu
    set timeout=10
  # Fallback normal timeout code in case the timeout_style feature is
  # unavailable.
  else
    set timeout=10
  fi
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
#set_background_image "images/tile.png";

set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
if background_color 0,0,0; then
  clear
fi
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
function gfxmode {
	set gfxpayload="${1}"
	if [ "${1}" = "keep" ]; then
		set vt_handoff=vt.handoff=7
	else
		set vt_handoff=
	fi
}
if [ "${recordfail}" != 1 ]; then
  if [ -e ${prefix}/gfxblacklist.txt ]; then
    if hwmatch ${prefix}/gfxblacklist.txt 3; then
      if [ ${match} = 0 ]; then
        set linux_gfx_mode=keep
      else
        set linux_gfx_mode=text
      fi
    else
      set linux_gfx_mode=text
    fi
  else
    set linux_gfx_mode=keep
  fi
else
  set linux_gfx_mode=text
fi
export linux_gfx_mode
menuentry 'Ubuntu' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-simple-855c6698-a72d-4cc5-8b7e-3dee0c8b7fca' {
	recordfail
	load_video
	gfxmode $linux_gfx_mode
	insmod gzio
	if [ x$grub_platform = xxen ]; then insmod xzio; insmod lzopio; fi
	insmod part_msdos
	insmod ext2
	set root='hd0,msdos1'
	if [ x$feature_platform_search_hint = xy ]; then
	  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos1 --hint-efi=hd0,msdos1 --hint-baremetal=ahci0,msdos1  855c6698-a72d-4cc5-8b7e-3dee0c8b7fca
	else
	  search --no-floppy --fs-uuid --set=root 855c6698-a72d-4cc5-8b7e-3dee0c8b7fca
	fi
        linux	/boot/vmlinuz-4.4.0-89-generic root=UUID=855c6698-a72d-4cc5-8b7e-3dee0c8b7fca ro  quiet splash $vt_handoff
	initrd	/boot/initrd.img-4.4.0-89-generic
}
submenu 'Advanced options for Ubuntu' $menuentry_id_option 'gnulinux-advanced-855c6698-a72d-4cc5-8b7e-3dee0c8b7fca' {
	menuentry 'Ubuntu, with Linux 4.4.0-89-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-4.4.0-89-generic-advanced-855c6698-a72d-4cc5-8b7e-3dee0c8b7fca' {
		recordfail
		load_video
		gfxmode $linux_gfx_mode
		insmod gzio
		if [ x$grub_platform = xxen ]; then insmod xzio; insmod lzopio; fi
		insmod part_msdos
		insmod ext2
		set root='hd0,msdos1'
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos1 --hint-efi=hd0,msdos1 --hint-baremetal=ahci0,msdos1  855c6698-a72d-4cc5-8b7e-3dee0c8b7fca
		else
		  search --no-floppy --fs-uuid --set=root 855c6698-a72d-4cc5-8b7e-3dee0c8b7fca
		fi
		echo	'Loading Linux 4.4.0-89-generic ...'
	        linux	/boot/vmlinuz-4.4.0-89-generic root=UUID=855c6698-a72d-4cc5-8b7e-3dee0c8b7fca ro  quiet splash $vt_handoff
		echo	'Loading initial ramdisk ...'
		initrd	/boot/initrd.img-4.4.0-89-generic
	}
	menuentry 'Ubuntu, with Linux 4.4.0-89-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-4.4.0-89-generic-recovery-855c6698-a72d-4cc5-8b7e-3dee0c8b7fca' {
		recordfail
		load_video
		insmod gzio
		if [ x$grub_platform = xxen ]; then insmod xzio; insmod lzopio; fi
		insmod part_msdos
		insmod ext2
		set root='hd0,msdos1'
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos1 --hint-efi=hd0,msdos1 --hint-baremetal=ahci0,msdos1  855c6698-a72d-4cc5-8b7e-3dee0c8b7fca
		else
		  search --no-floppy --fs-uuid --set=root 855c6698-a72d-4cc5-8b7e-3dee0c8b7fca
		fi
		echo	'Loading Linux 4.4.0-89-generic ...'
	        linux	/boot/vmlinuz-4.4.0-89-generic root=UUID=855c6698-a72d-4cc5-8b7e-3dee0c8b7fca ro recovery nomodeset 
		echo	'Loading initial ramdisk ...'
		initrd	/boot/initrd.img-4.4.0-89-generic
	}
	menuentry 'Ubuntu, with Linux 4.4.0-87-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-4.4.0-87-generic-advanced-855c6698-a72d-4cc5-8b7e-3dee0c8b7fca' {
		recordfail
		load_video
		gfxmode $linux_gfx_mode
		insmod gzio
		if [ x$grub_platform = xxen ]; then insmod xzio; insmod lzopio; fi
		insmod part_msdos
		insmod ext2
		set root='hd0,msdos1'
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos1 --hint-efi=hd0,msdos1 --hint-baremetal=ahci0,msdos1  855c6698-a72d-4cc5-8b7e-3dee0c8b7fca
		else
		  search --no-floppy --fs-uuid --set=root 855c6698-a72d-4cc5-8b7e-3dee0c8b7fca
		fi
		echo	'Loading Linux 4.4.0-87-generic ...'
	        linux	/boot/vmlinuz-4.4.0-87-generic root=UUID=855c6698-a72d-4cc5-8b7e-3dee0c8b7fca ro  quiet splash $vt_handoff
		echo	'Loading initial ramdisk ...'
		initrd	/boot/initrd.img-4.4.0-87-generic
	}
	menuentry 'Ubuntu, with Linux 4.4.0-87-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-4.4.0-87-generic-recovery-855c6698-a72d-4cc5-8b7e-3dee0c8b7fca' {
		recordfail
		load_video
		insmod gzio
		if [ x$grub_platform = xxen ]; then insmod xzio; insmod lzopio; fi
		insmod part_msdos
		insmod ext2
		set root='hd0,msdos1'
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos1 --hint-efi=hd0,msdos1 --hint-baremetal=ahci0,msdos1  855c6698-a72d-4cc5-8b7e-3dee0c8b7fca
		else
		  search --no-floppy --fs-uuid --set=root 855c6698-a72d-4cc5-8b7e-3dee0c8b7fca
		fi
		echo	'Loading Linux 4.4.0-87-generic ...'
	        linux	/boot/vmlinuz-4.4.0-87-generic root=UUID=855c6698-a72d-4cc5-8b7e-3dee0c8b7fca ro recovery nomodeset 
		echo	'Loading initial ramdisk ...'
		initrd	/boot/initrd.img-4.4.0-87-generic
	}
	menuentry 'Ubuntu, with Linux 4.4.0-85-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-4.4.0-85-generic-advanced-855c6698-a72d-4cc5-8b7e-3dee0c8b7fca' {
		recordfail
		load_video
		gfxmode $linux_gfx_mode
		insmod gzio
		if [ x$grub_platform = xxen ]; then insmod xzio; insmod lzopio; fi
		insmod part_msdos
		insmod ext2
		set root='hd0,msdos1'
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos1 --hint-efi=hd0,msdos1 --hint-baremetal=ahci0,msdos1  855c6698-a72d-4cc5-8b7e-3dee0c8b7fca
		else
		  search --no-floppy --fs-uuid --set=root 855c6698-a72d-4cc5-8b7e-3dee0c8b7fca
		fi
		echo	'Loading Linux 4.4.0-85-generic ...'
	        linux	/boot/vmlinuz-4.4.0-85-generic root=UUID=855c6698-a72d-4cc5-8b7e-3dee0c8b7fca ro  quiet splash $vt_handoff
		echo	'Loading initial ramdisk ...'
		initrd	/boot/initrd.img-4.4.0-85-generic
	}
	menuentry 'Ubuntu, with Linux 4.4.0-85-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-4.4.0-85-generic-recovery-855c6698-a72d-4cc5-8b7e-3dee0c8b7fca' {
		recordfail
		load_video
		insmod gzio
		if [ x$grub_platform = xxen ]; then insmod xzio; insmod lzopio; fi
		insmod part_msdos
		insmod ext2
		set root='hd0,msdos1'
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos1 --hint-efi=hd0,msdos1 --hint-baremetal=ahci0,msdos1  855c6698-a72d-4cc5-8b7e-3dee0c8b7fca
		else
		  search --no-floppy --fs-uuid --set=root 855c6698-a72d-4cc5-8b7e-3dee0c8b7fca
		fi
		echo	'Loading Linux 4.4.0-85-generic ...'
	        linux	/boot/vmlinuz-4.4.0-85-generic root=UUID=855c6698-a72d-4cc5-8b7e-3dee0c8b7fca ro recovery nomodeset 
		echo	'Loading initial ramdisk ...'
		initrd	/boot/initrd.img-4.4.0-85-generic
	}
	menuentry 'Ubuntu, with Linux 4.4.0-83-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-4.4.0-83-generic-advanced-855c6698-a72d-4cc5-8b7e-3dee0c8b7fca' {
		recordfail
		load_video
		gfxmode $linux_gfx_mode
		insmod gzio
		if [ x$grub_platform = xxen ]; then insmod xzio; insmod lzopio; fi
		insmod part_msdos
		insmod ext2
		set root='hd0,msdos1'
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos1 --hint-efi=hd0,msdos1 --hint-baremetal=ahci0,msdos1  855c6698-a72d-4cc5-8b7e-3dee0c8b7fca
		else
		  search --no-floppy --fs-uuid --set=root 855c6698-a72d-4cc5-8b7e-3dee0c8b7fca
		fi
		echo	'Loading Linux 4.4.0-83-generic ...'
	        linux	/boot/vmlinuz-4.4.0-83-generic root=UUID=855c6698-a72d-4cc5-8b7e-3dee0c8b7fca ro  quiet splash $vt_handoff
		echo	'Loading initial ramdisk ...'
		initrd	/boot/initrd.img-4.4.0-83-generic
	}
	menuentry 'Ubuntu, with Linux 4.4.0-83-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-4.4.0-83-generic-recovery-855c6698-a72d-4cc5-8b7e-3dee0c8b7fca' {
		recordfail
		load_video
		insmod gzio
		if [ x$grub_platform = xxen ]; then insmod xzio; insmod lzopio; fi
		insmod part_msdos
		insmod ext2
		set root='hd0,msdos1'
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos1 --hint-efi=hd0,msdos1 --hint-baremetal=ahci0,msdos1  855c6698-a72d-4cc5-8b7e-3dee0c8b7fca
		else
		  search --no-floppy --fs-uuid --set=root 855c6698-a72d-4cc5-8b7e-3dee0c8b7fca
		fi
		echo	'Loading Linux 4.4.0-83-generic ...'
	        linux	/boot/vmlinuz-4.4.0-83-generic root=UUID=855c6698-a72d-4cc5-8b7e-3dee0c8b7fca ro recovery nomodeset 
		echo	'Loading initial ramdisk ...'
		initrd	/boot/initrd.img-4.4.0-83-generic
	}
	menuentry 'Ubuntu, with Linux 4.4.0-82-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-4.4.0-82-generic-advanced-855c6698-a72d-4cc5-8b7e-3dee0c8b7fca' {
		recordfail
		load_video
		gfxmode $linux_gfx_mode
		insmod gzio
		if [ x$grub_platform = xxen ]; then insmod xzio; insmod lzopio; fi
		insmod part_msdos
		insmod ext2
		set root='hd0,msdos1'
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos1 --hint-efi=hd0,msdos1 --hint-baremetal=ahci0,msdos1  855c6698-a72d-4cc5-8b7e-3dee0c8b7fca
		else
		  search --no-floppy --fs-uuid --set=root 855c6698-a72d-4cc5-8b7e-3dee0c8b7fca
		fi
		echo	'Loading Linux 4.4.0-82-generic ...'
	        linux	/boot/vmlinuz-4.4.0-82-generic root=UUID=855c6698-a72d-4cc5-8b7e-3dee0c8b7fca ro  quiet splash $vt_handoff
		echo	'Loading initial ramdisk ...'
		initrd	/boot/initrd.img-4.4.0-82-generic
	}
	menuentry 'Ubuntu, with Linux 4.4.0-82-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-4.4.0-82-generic-recovery-855c6698-a72d-4cc5-8b7e-3dee0c8b7fca' {
		recordfail
		load_video
		insmod gzio
		if [ x$grub_platform = xxen ]; then insmod xzio; insmod lzopio; fi
		insmod part_msdos
		insmod ext2
		set root='hd0,msdos1'
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos1 --hint-efi=hd0,msdos1 --hint-baremetal=ahci0,msdos1  855c6698-a72d-4cc5-8b7e-3dee0c8b7fca
		else
		  search --no-floppy --fs-uuid --set=root 855c6698-a72d-4cc5-8b7e-3dee0c8b7fca
		fi
		echo	'Loading Linux 4.4.0-82-generic ...'
	        linux	/boot/vmlinuz-4.4.0-82-generic root=UUID=855c6698-a72d-4cc5-8b7e-3dee0c8b7fca ro recovery nomodeset 
		echo	'Loading initial ramdisk ...'
		initrd	/boot/initrd.img-4.4.0-82-generic
	}
	menuentry 'Ubuntu, with Linux 4.4.0-81-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-4.4.0-81-generic-advanced-855c6698-a72d-4cc5-8b7e-3dee0c8b7fca' {
		recordfail
		load_video
		gfxmode $linux_gfx_mode
		insmod gzio
		if [ x$grub_platform = xxen ]; then insmod xzio; insmod lzopio; fi
		insmod part_msdos
		insmod ext2
		set root='hd0,msdos1'
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos1 --hint-efi=hd0,msdos1 --hint-baremetal=ahci0,msdos1  855c6698-a72d-4cc5-8b7e-3dee0c8b7fca
		else
		  search --no-floppy --fs-uuid --set=root 855c6698-a72d-4cc5-8b7e-3dee0c8b7fca
		fi
		echo	'Loading Linux 4.4.0-81-generic ...'
	        linux	/boot/vmlinuz-4.4.0-81-generic root=UUID=855c6698-a72d-4cc5-8b7e-3dee0c8b7fca ro  quiet splash $vt_handoff
		echo	'Loading initial ramdisk ...'
		initrd	/boot/initrd.img-4.4.0-81-generic
	}
	menuentry 'Ubuntu, with Linux 4.4.0-81-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-4.4.0-81-generic-recovery-855c6698-a72d-4cc5-8b7e-3dee0c8b7fca' {
		recordfail
		load_video
		insmod gzio
		if [ x$grub_platform = xxen ]; then insmod xzio; insmod lzopio; fi
		insmod part_msdos
		insmod ext2
		set root='hd0,msdos1'
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos1 --hint-efi=hd0,msdos1 --hint-baremetal=ahci0,msdos1  855c6698-a72d-4cc5-8b7e-3dee0c8b7fca
		else
		  search --no-floppy --fs-uuid --set=root 855c6698-a72d-4cc5-8b7e-3dee0c8b7fca
		fi
		echo	'Loading Linux 4.4.0-81-generic ...'
	        linux	/boot/vmlinuz-4.4.0-81-generic root=UUID=855c6698-a72d-4cc5-8b7e-3dee0c8b7fca ro recovery nomodeset 
		echo	'Loading initial ramdisk ...'
		initrd	/boot/initrd.img-4.4.0-81-generic
	}
	menuentry 'Ubuntu, with Linux 4.4.0-80-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-4.4.0-80-generic-advanced-855c6698-a72d-4cc5-8b7e-3dee0c8b7fca' {
		recordfail
		load_video
		gfxmode $linux_gfx_mode
		insmod gzio
		if [ x$grub_platform = xxen ]; then insmod xzio; insmod lzopio; fi
		insmod part_msdos
		insmod ext2
		set root='hd0,msdos1'
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos1 --hint-efi=hd0,msdos1 --hint-baremetal=ahci0,msdos1  855c6698-a72d-4cc5-8b7e-3dee0c8b7fca
		else
		  search --no-floppy --fs-uuid --set=root 855c6698-a72d-4cc5-8b7e-3dee0c8b7fca
		fi
		echo	'Loading Linux 4.4.0-80-generic ...'
	        linux	/boot/vmlinuz-4.4.0-80-generic root=UUID=855c6698-a72d-4cc5-8b7e-3dee0c8b7fca ro  quiet splash $vt_handoff
		echo	'Loading initial ramdisk ...'
		initrd	/boot/initrd.img-4.4.0-80-generic
	}
	menuentry 'Ubuntu, with Linux 4.4.0-80-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-4.4.0-80-generic-recovery-855c6698-a72d-4cc5-8b7e-3dee0c8b7fca' {
		recordfail
		load_video
		insmod gzio
		if [ x$grub_platform = xxen ]; then insmod xzio; insmod lzopio; fi
		insmod part_msdos
		insmod ext2
		set root='hd0,msdos1'
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos1 --hint-efi=hd0,msdos1 --hint-baremetal=ahci0,msdos1  855c6698-a72d-4cc5-8b7e-3dee0c8b7fca
		else
		  search --no-floppy --fs-uuid --set=root 855c6698-a72d-4cc5-8b7e-3dee0c8b7fca
		fi
		echo	'Loading Linux 4.4.0-80-generic ...'
	        linux	/boot/vmlinuz-4.4.0-80-generic root=UUID=855c6698-a72d-4cc5-8b7e-3dee0c8b7fca ro recovery nomodeset 
		echo	'Loading initial ramdisk ...'
		initrd	/boot/initrd.img-4.4.0-80-generic
	}
	menuentry 'Ubuntu, with Linux 4.4.0-79-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-4.4.0-79-generic-advanced-855c6698-a72d-4cc5-8b7e-3dee0c8b7fca' {
		recordfail
		load_video
		gfxmode $linux_gfx_mode
		insmod gzio
		if [ x$grub_platform = xxen ]; then insmod xzio; insmod lzopio; fi
		insmod part_msdos
		insmod ext2
		set root='hd0,msdos1'
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos1 --hint-efi=hd0,msdos1 --hint-baremetal=ahci0,msdos1  855c6698-a72d-4cc5-8b7e-3dee0c8b7fca
		else
		  search --no-floppy --fs-uuid --set=root 855c6698-a72d-4cc5-8b7e-3dee0c8b7fca
		fi
		echo	'Loading Linux 4.4.0-79-generic ...'
	        linux	/boot/vmlinuz-4.4.0-79-generic root=UUID=855c6698-a72d-4cc5-8b7e-3dee0c8b7fca ro  quiet splash $vt_handoff
		echo	'Loading initial ramdisk ...'
		initrd	/boot/initrd.img-4.4.0-79-generic
	}
	menuentry 'Ubuntu, with Linux 4.4.0-79-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-4.4.0-79-generic-recovery-855c6698-a72d-4cc5-8b7e-3dee0c8b7fca' {
		recordfail
		load_video
		insmod gzio
		if [ x$grub_platform = xxen ]; then insmod xzio; insmod lzopio; fi
		insmod part_msdos
		insmod ext2
		set root='hd0,msdos1'
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos1 --hint-efi=hd0,msdos1 --hint-baremetal=ahci0,msdos1  855c6698-a72d-4cc5-8b7e-3dee0c8b7fca
		else
		  search --no-floppy --fs-uuid --set=root 855c6698-a72d-4cc5-8b7e-3dee0c8b7fca
		fi
		echo	'Loading Linux 4.4.0-79-generic ...'
	        linux	/boot/vmlinuz-4.4.0-79-generic root=UUID=855c6698-a72d-4cc5-8b7e-3dee0c8b7fca ro recovery nomodeset 
		echo	'Loading initial ramdisk ...'
		initrd	/boot/initrd.img-4.4.0-79-generic
	}
	menuentry 'Ubuntu, with Linux 4.4.0-77-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-4.4.0-77-generic-advanced-855c6698-a72d-4cc5-8b7e-3dee0c8b7fca' {
		recordfail
		load_video
		gfxmode $linux_gfx_mode
		insmod gzio
		if [ x$grub_platform = xxen ]; then insmod xzio; insmod lzopio; fi
		insmod part_msdos
		insmod ext2
		set root='hd0,msdos1'
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos1 --hint-efi=hd0,msdos1 --hint-baremetal=ahci0,msdos1  855c6698-a72d-4cc5-8b7e-3dee0c8b7fca
		else
		  search --no-floppy --fs-uuid --set=root 855c6698-a72d-4cc5-8b7e-3dee0c8b7fca
		fi
		echo	'Loading Linux 4.4.0-77-generic ...'
	        linux	/boot/vmlinuz-4.4.0-77-generic root=UUID=855c6698-a72d-4cc5-8b7e-3dee0c8b7fca ro  quiet splash $vt_handoff
		echo	'Loading initial ramdisk ...'
		initrd	/boot/initrd.img-4.4.0-77-generic
	}
	menuentry 'Ubuntu, with Linux 4.4.0-77-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-4.4.0-77-generic-recovery-855c6698-a72d-4cc5-8b7e-3dee0c8b7fca' {
		recordfail
		load_video
		insmod gzio
		if [ x$grub_platform = xxen ]; then insmod xzio; insmod lzopio; fi
		insmod part_msdos
		insmod ext2
		set root='hd0,msdos1'
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos1 --hint-efi=hd0,msdos1 --hint-baremetal=ahci0,msdos1  855c6698-a72d-4cc5-8b7e-3dee0c8b7fca
		else
		  search --no-floppy --fs-uuid --set=root 855c6698-a72d-4cc5-8b7e-3dee0c8b7fca
		fi
		echo	'Loading Linux 4.4.0-77-generic ...'
	        linux	/boot/vmlinuz-4.4.0-77-generic root=UUID=855c6698-a72d-4cc5-8b7e-3dee0c8b7fca ro recovery nomodeset 
		echo	'Loading initial ramdisk ...'
		initrd	/boot/initrd.img-4.4.0-77-generic
	}
	menuentry 'Ubuntu, with Linux 4.4.0-75-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-4.4.0-75-generic-advanced-855c6698-a72d-4cc5-8b7e-3dee0c8b7fca' {
		recordfail
		load_video
		gfxmode $linux_gfx_mode
		insmod gzio
		if [ x$grub_platform = xxen ]; then insmod xzio; insmod lzopio; fi
		insmod part_msdos
		insmod ext2
		set root='hd0,msdos1'
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos1 --hint-efi=hd0,msdos1 --hint-baremetal=ahci0,msdos1  855c6698-a72d-4cc5-8b7e-3dee0c8b7fca
		else
		  search --no-floppy --fs-uuid --set=root 855c6698-a72d-4cc5-8b7e-3dee0c8b7fca
		fi
		echo	'Loading Linux 4.4.0-75-generic ...'
	        linux	/boot/vmlinuz-4.4.0-75-generic root=UUID=855c6698-a72d-4cc5-8b7e-3dee0c8b7fca ro  quiet splash $vt_handoff
		echo	'Loading initial ramdisk ...'
		initrd	/boot/initrd.img-4.4.0-75-generic
	}
	menuentry 'Ubuntu, with Linux 4.4.0-75-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-4.4.0-75-generic-recovery-855c6698-a72d-4cc5-8b7e-3dee0c8b7fca' {
		recordfail
		load_video
		insmod gzio
		if [ x$grub_platform = xxen ]; then insmod xzio; insmod lzopio; fi
		insmod part_msdos
		insmod ext2
		set root='hd0,msdos1'
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos1 --hint-efi=hd0,msdos1 --hint-baremetal=ahci0,msdos1  855c6698-a72d-4cc5-8b7e-3dee0c8b7fca
		else
		  search --no-floppy --fs-uuid --set=root 855c6698-a72d-4cc5-8b7e-3dee0c8b7fca
		fi
		echo	'Loading Linux 4.4.0-75-generic ...'
	        linux	/boot/vmlinuz-4.4.0-75-generic root=UUID=855c6698-a72d-4cc5-8b7e-3dee0c8b7fca ro recovery nomodeset 
		echo	'Loading initial ramdisk ...'
		initrd	/boot/initrd.img-4.4.0-75-generic
	}
}

### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###

### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry 'Memory test (memtest86+)' {
	insmod part_msdos
	insmod ext2
	set root='hd0,msdos1'
	if [ x$feature_platform_search_hint = xy ]; then
	  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos1 --hint-efi=hd0,msdos1 --hint-baremetal=ahci0,msdos1  855c6698-a72d-4cc5-8b7e-3dee0c8b7fca
	else
	  search --no-floppy --fs-uuid --set=root 855c6698-a72d-4cc5-8b7e-3dee0c8b7fca
	fi
	knetbsd	/boot/memtest86+.elf
}
menuentry 'Memory test (memtest86+, serial console 115200)' {
	insmod part_msdos
	insmod ext2
	set root='hd0,msdos1'
	if [ x$feature_platform_search_hint = xy ]; then
	  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos1 --hint-efi=hd0,msdos1 --hint-baremetal=ahci0,msdos1  855c6698-a72d-4cc5-8b7e-3dee0c8b7fca
	else
	  search --no-floppy --fs-uuid --set=root 855c6698-a72d-4cc5-8b7e-3dee0c8b7fca
	fi
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/30_uefi-firmware ###
### END /etc/grub.d/30_uefi-firmware ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

### BEGIN /etc/grub.d/41_custom ###
if [ -f  ${config_directory}/custom.cfg ]; then
  source ${config_directory}/custom.cfg
elif [ -z "${config_directory}" -a -f  $prefix/custom.cfg ]; then
  source $prefix/custom.cfg;
fi
### END /etc/grub.d/41_custom ###
--------------------------------------------------------------------------------

=============================== sda1/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sda1 during installation
UUID=855c6698-a72d-4cc5-8b7e-3dee0c8b7fca /               ext4    errors=remount-ro 0       1
# /home was on /dev/sda3 during installation
UUID=4925dcbd-b2a1-4db6-adc0-69a9f05ad473 /home           ext4    defaults        0       2
# swap was on /dev/sda2 during installation
UUID=82e48eb2-0c33-4696-9154-d921da42bbd2 none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
# / Kubuntu2 - secondary HDD - 250 Gb
UUID=79731916-952b-4d88-b6d4-40e81b15731d  /media/kubuntu2               ext4    noauto,errors=remount-ro 0       1
# / external hard drive - 500Gb
UUID=bbff7f7d-5db9-467c-b1c4-5831cc6870d6 /media/externaldisk               ext4    noauto,errors=remount-ro 0       1
--------------------------------------------------------------------------------

=================== sda1: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)


======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown MBR on /dev/sdc

00000000  45 52 08 00 00 00 90 90  00 00 00 00 00 00 00 00  |ER..............|
00000010  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000020  33 ed fa 8e d5 bc 00 7c  fb fc 66 31 db 66 31 c9  |3......|..f1.f1.|
00000030  66 53 66 51 06 57 8e dd  8e c5 52 be 00 7c bf 00  |fSfQ.W....R..|..|
00000040  06 b9 00 01 f3 a5 ea 4b  06 00 00 52 b4 41 bb aa  |.......K...R.A..|
00000050  55 31 c9 30 f6 f9 cd 13  72 16 81 fb 55 aa 75 10  |U1.0....r...U.u.|
00000060  83 e1 01 74 0b 66 c7 06  f1 06 b4 42 eb 15 eb 00  |...t.f.....B....|
00000070  5a 51 b4 08 cd 13 83 e1  3f 5b 51 0f b6 c6 40 50  |ZQ......?[Q...@P|
00000080  f7 e1 53 52 50 bb 00 7c  b9 04 00 66 a1 b0 07 e8  |..SRP..|...f....|
00000090  44 00 0f 82 80 00 66 40  80 c7 02 e2 f2 66 81 3e  |D.....f@.....f.>|
000000a0  40 7c fb c0 78 70 75 09  fa bc ec 7b ea 44 7c 00  |@|..xpu....{.D|.|
000000b0  00 e8 83 00 69 73 6f 6c  69 6e 75 78 2e 62 69 6e  |....isolinux.bin|
000000c0  20 6d 69 73 73 69 6e 67  20 6f 72 20 63 6f 72 72  | missing or corr|
000000d0  75 70 74 2e 0d 0a 66 60  66 31 d2 66 03 06 f8 7b  |upt...f`f1.f...{|
000000e0  66 13 16 fc 7b 66 52 66  50 06 53 6a 01 6a 10 89  |f...{fRfP.Sj.j..|
000000f0  e6 66 f7 36 e8 7b c0 e4  06 88 e1 88 c5 92 f6 36  |.f.6.{.........6|
00000100  ee 7b 88 c6 08 e1 41 b8  01 02 8a 16 f2 7b cd 13  |.{....A......{..|
00000110  8d 64 10 66 61 c3 e8 1e  00 4f 70 65 72 61 74 69  |.d.fa....Operati|
00000120  6e 67 20 73 79 73 74 65  6d 20 6c 6f 61 64 20 65  |ng system load e|
00000130  72 72 6f 72 2e 0d 0a 5e  ac b4 0e 8a 3e 62 04 b3  |rror...^....>b..|
00000140  07 cd 10 3c 0a 75 f1 cd  18 f4 eb fd 00 00 00 00  |...<.u..........|
00000150  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000160  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000170  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000180  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000190  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001a0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001b0  50 4b 2d 00 00 00 00 00  b7 62 d9 17 00 00 80 00  |PK-......b......|
000001c0  01 00 00 5b e0 fb 00 00  00 00 00 d2 2d 00 00 fe  |...[........-...|
000001d0  ff ff ef fe ff ff d0 81  2d 00 80 12 00 00 00 00  |........-.......|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200

Unknown BootLoader on sdc1

00000000  45 52 08 00 00 00 90 90  00 00 00 00 00 00 00 00  |ER..............|
00000010  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000020  33 ed fa 8e d5 bc 00 7c  fb fc 66 31 db 66 31 c9  |3......|..f1.f1.|
00000030  66 53 66 51 06 57 8e dd  8e c5 52 be 00 7c bf 00  |fSfQ.W....R..|..|
00000040  06 b9 00 01 f3 a5 ea 4b  06 00 00 52 b4 41 bb aa  |.......K...R.A..|
00000050  55 31 c9 30 f6 f9 cd 13  72 16 81 fb 55 aa 75 10  |U1.0....r...U.u.|
00000060  83 e1 01 74 0b 66 c7 06  f1 06 b4 42 eb 15 eb 00  |...t.f.....B....|
00000070  5a 51 b4 08 cd 13 83 e1  3f 5b 51 0f b6 c6 40 50  |ZQ......?[Q...@P|
00000080  f7 e1 53 52 50 bb 00 7c  b9 04 00 66 a1 b0 07 e8  |..SRP..|...f....|
00000090  44 00 0f 82 80 00 66 40  80 c7 02 e2 f2 66 81 3e  |D.....f@.....f.>|
000000a0  40 7c fb c0 78 70 75 09  fa bc ec 7b ea 44 7c 00  |@|..xpu....{.D|.|
000000b0  00 e8 83 00 69 73 6f 6c  69 6e 75 78 2e 62 69 6e  |....isolinux.bin|
000000c0  20 6d 69 73 73 69 6e 67  20 6f 72 20 63 6f 72 72  | missing or corr|
000000d0  75 70 74 2e 0d 0a 66 60  66 31 d2 66 03 06 f8 7b  |upt...f`f1.f...{|
000000e0  66 13 16 fc 7b 66 52 66  50 06 53 6a 01 6a 10 89  |f...{fRfP.Sj.j..|
000000f0  e6 66 f7 36 e8 7b c0 e4  06 88 e1 88 c5 92 f6 36  |.f.6.{.........6|
00000100  ee 7b 88 c6 08 e1 41 b8  01 02 8a 16 f2 7b cd 13  |.{....A......{..|
00000110  8d 64 10 66 61 c3 e8 1e  00 4f 70 65 72 61 74 69  |.d.fa....Operati|
00000120  6e 67 20 73 79 73 74 65  6d 20 6c 6f 61 64 20 65  |ng system load e|
00000130  72 72 6f 72 2e 0d 0a 5e  ac b4 0e 8a 3e 62 04 b3  |rror...^....>b..|
00000140  07 cd 10 3c 0a 75 f1 cd  18 f4 eb fd 00 00 00 00  |...<.u..........|
00000150  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001b0  50 4b 2d 00 00 00 00 00  b7 62 d9 17 00 00 80 00  |PK-......b......|
000001c0  01 00 00 5b e0 fb 00 00  00 00 00 d2 2d 00 00 fe  |...[........-...|
000001d0  ff ff ef fe ff ff d0 81  2d 00 80 12 00 00 00 00  |........-.......|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


=============================== StdErr Messages: ===============================

cat: /tmp/BootInfo-WBOgtPk3/Tmp_Log: No such file or directory

```

---

### Post by efflandt on 2017-08-11
The last computer I have with PATA (IDE) hard drive was a really low  end Compaq laptop from 2005, and laptops I have from 2006 on have SATA  drives. Any computer from 2008 should be be able to do LBA translation for any size SATA drive. It is just that if the drive is larger than 2 TB you have to use gpt partitioning instead of mbr (msdos) partitioning.

My 386DX33 PC (around 1995?) did not do LBA, so it could only boot from a partition within the first 528 MB (yes MB not GB) of a drive. Since the computer had no BIOS update to handle that I had to use an add-on card and compile my own kernels (in Slackware at that time) to support the add-on card to use the whole 540 MB.

---

### Post by oygle on 2017-08-11
> **efflandt said:**
> Any computer from 2008 should be be able to do LBA translation for any size SATA drive. It is just that if the drive is larger than 2 TB you have to use gpt partitioning instead of mbr (msdos) partitioning.

Okay thanks.  :)

I'm not convinced this is a ram problem, even though the memtest showed an error. But if it was a ram problem, how am I able to boot to the Live USB without any errors ? No hanging, just a very quick boot.

Are there any method/s to repair the kernel ?  Is this how to do a repair - [https://askubuntu.com/questions/226061/how-to-install-the-boot-repair-tool-in-an-ubuntu-live-disc](https://askubuntu.com/questions/226061/how-to-install-the-boot-repair-tool-in-an-ubuntu-live-disc)

---

### Post by Bashing-om on 2017-08-11
oygle; Hey ;

I see now what we are working with .
Are you able to boot from sda1 ?

Good deal with the provided boot info .
I do see that you are booting with a valid /etc/fstab file !
I do suggest we look at the referenced mountpoints in the /etc/fstab file.

what shows - booted from the install:
```

ls -al /media/
ls -al /media/<your_user_neame>

```
Make sure the mount points are valid for the floppy disk and that external hard drive/
Also want to verify "  bbff7f7d-5db9-467c-b1c4-5831cc6870d6"
what shows :
```

sudo blkid -c /dev/null -o list

```
Working from invalid info leads to real bad advice . I will get it right .

[INDENT][INDENT]all in the process
[/INDENT][/INDENT]

---

### Post by oygle on 2017-08-12
Have been able to at least start backups today, so in a day or so, will do a clean install.  :)

---

### Post by oygle on 2017-08-14
Was able to do a clean install of Kubuntu 17.04 from a live usb, and update the backups whilst booted up with the Live usb. However, the old hard drives and old ram have made the desktop redundant; not worth spending money on it.

---

### Post by Bashing-om on 2017-08-14
oygle; Ho Kay ;

Bear in mind I run a 2007 Box on a dual core Athlon CPU. 
A bit sluggish on the heavy weight DEs but performs adequate with the lighter DEs .
very fast with a minimal install -
very fast on a SSD full desktop xubuntu install.

Maybe 150 USD will put that machine of yours back on it's feet .

However, it you require to run heavy duty
[INDENT][INDENT]you got to have the hosses to do it
[/INDENT][/INDENT]

---

### Post by oygle on 2017-08-15
> **Bashing-om said:**
> Maybe 150 USD will put that machine of yours back on it's feet .

Thanks for your help. I've decided to upgrade to something else.  :)

---

