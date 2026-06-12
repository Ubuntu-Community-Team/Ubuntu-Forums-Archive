---
title: "Clonezilla Failed To Clone 1TB To  WD HDD"
date: 2013-04-10
forum: General Help
---

### Post by coljohnhannibalsmith on 2013-04-10
Hello,

Clonezilla Failed To Clone to 1TB WD HDD.

My Dell has a 4500rpm 1TB WD internal HDD.  I bought a WD 5400rpm 1TB HDD and tried to clone my internal to it using Clonezilla.

Clonezilla failed with the following messages:

[COLOR=#ff0000][I]The partition table in this disc is illegal or invalid /dev/sdb.  Is this disc too small?

Error can't have a partition outside the disc.

Program terminated.[/I][/COLOR]

My version of Clonezilla is about 3 years old.  Does it not support 1TB HDDs, or is my drive bad.

Thanks Hannibal

---

### Post by matt_symes on 2013-04-10
Hi

With both disks plugged in, please post the output of

```
sudo parted -l
```

Kind regards

---

### Post by coljohnhannibalsmith on 2013-04-11
```

sophie@sophie-Inspiron-5520:~$ sudo parted -l
[sudo] password for sophie: 
Model: ATA ST1000LM024 HN-M (scsi)
Disk /dev/sda: 1000GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type      File system     Flags
 1      32.3kB  41.1MB  41.1MB  primary   fat16           diag
 2      41.9MB  21.3GB  21.3GB  primary   ntfs            boot
 3      21.3GB  322GB   301GB   primary   ntfs
 4      322GB   1000GB  678GB   extended
 5      322GB   992GB   670GB   logical   ext4)
 6      992GB   1000GB  8486MB  logical   linux-swap(v1) 


Error: Can't have a partition outside the disk!                           

sophie@sophie-Inspiron-5520:~$ 
```

(This is the drive that I'm trying to clone to)  (Also sda6 is  linux swap on my internal drive and somehow sda6 and my new drive are  being seen as one partition).


BTW, it turns out that the internal drive is a Samsung:

Source:    sda 1000GB_ST1000LM024_HNM_ata-xxxxxxx    
Dest:       sdb 1000GB_JPVT-22A1YT0__usb-xxxxxxxxxx

---

### Post by coljohnhannibalsmith on 2013-04-13
Bump!

---

### Post by coljohnhannibalsmith on 2013-04-13
Additional information:

Please look at sda6 on the attachment.  I did not have the other drive connected at this time.

I tried Acronis True Image and it stopped immediately.

Has anyone cloned a 1TB dual boot system?  It looks like the cloning software can't deal with it.

Thanks Hannibal

---

### Post by coljohnhannibalsmith on 2013-04-19
Bump.

---

### Post by sudodus on 2013-04-19
I'm using Clonezilla a lot and like it, but it does not want to clone to or restore from an image to a drive or partition, that is smaller than the original one. And sometimes two 1 TB drives might be slightly different in size. What you can do is to shrink the last partittion, the swap, and after that the extended partition, so that they will fit in the target drive.

I think you should get a current version of Clonezilla. The iso file is less than 200 MB and quite easy to download. If you have old computers you need the 32 bit version (the stable version). If you have a new computer with Windows 8 and/or UEFI, you need the 64 bit Ubuntu based alternate version.

If your 1 TB drives contain no Windows or Mac operating system, you can create partitions with gparted and copy the files of each partition with rsync. This gives you the chance to change the size of the partitions. And you must also make a boot sector to the head of the new drive, if it is a boot drive.

---

### Post by matt_symes on 2013-04-19
Hi

I don't think your drives are bad in a hardware sense.

> Error: Can't have a partition outside the disk! 

Partitions 1 to 6 are all on the same drive.

This is your problem. Shrink your swap partition down in size or delete it while you clone onto the second hard drive.

Kind regards

---

### Post by dentaku65 on 2013-04-20
As far as I recall during the wizard of disk cloning Clonezilla have an option, in other options or advanced options, to skip the check of target disk size or do no check target disk size. If the disk image is bigger than the target disk size with that option disabled (or enabled, really I don't remeber exactly) the cloning will fail.

---

### Post by prodigy_ on 2013-04-20
I tried to use Clonezilla once and found it amazingly underwhelming. I wanted to copy a partition to a smaller partition (which should be fine when the source partition is 95% free). And Clonezilla said I had to edit the ISO just to enable that option in principle. At this point I laughed and thought that somebody ought to tell the developers about basic conventions of *NIX programming. Such as instead of blocking features of your back-end issue a warning and let users decide what's best for them.

Anyway, I found it easier to copy file systems one by one with **rsync -xc** and then reinstall grub from a live medium.

---

### Post by coljohnhannibalsmith on 2013-04-20
> **matt_symes said:**
> Hi

I don't think your drives are bad in a hardware sense.



Partitions 1 to 6 are all on the same drive.

This is your problem. Shrink your swap partition down in size or delete it while you clone onto the second hard drive.

Kind regards

Matt,

Gparted won't let me shrink the Swap partion while the drive is mounted (this is the system drive).  Also the SWAP partion is 8GB.  How small should I make it?  I believe to get around the mounting problem, I will have to boot from a live CD and use GParted from there to shrink the partition.

Please fill me in on the details.

Thanks Hannibal

---

### Post by sudodus on 2013-04-20
> **coljohnhannibalsmith said:**
> Matt,

Gparted won't let me shrink the Swap partion while the drive is mounted (this is the system drive).  Also the SWAP partion is 8GB.  How small should I make it?  I believe to get around the mounting problem, I will have to boot from a live CD and use GParted from there to shrink the partition.

Please fill me in on the details.

Thanks Hannibal

Yes, you should boot from another drive, and the Ubuntu install CD/DVD/USB is a good choice. Gparted comes with it and is ready to use.

It is OK to remove the swap for this operation to succeed. Afterwards you can create new swap (as much as there is free space). The old rule that swap should be twice the ram is no longer valid with the large amount of ram in new computers. You can run without swap, but it is a good idea to have say 1 or 2 GB swap to buffer for temporary high memory demands. If you want to hibernate safely, you need at least the same amount of swap as ram.

Anyway, if you wipe and recreate swap, you need to edit the UUID specification for the swap partition in the file **[FONT=courier new]/etc/fstab[/FONT]**. The command
```
sudo blkid
``` will list data such as UUID and labels of the partitions.

---

### Post by coljohnhannibalsmith on 2013-04-20
> **matt_symes said:**
> Hi

I don't think your drives are bad in a hardware sense.



Partitions 1 to 6 are all on the same drive.

This is your problem. Shrink your swap partition down in size or delete it while you clone onto the second hard drive.

Kind regards

GParted will not let me shink the Swap Partition while the drive is mounted, so it appears that I will have to boot from a USB stick and them resize the partition.  My Swap partition is currently 8GB, what should I shrink it to.  Can you fill me in on the details?

Thanks Hannibal

---

### Post by coljohnhannibalsmith on 2013-04-22
> **matt_symes said:**
> Hi

I don't think your drives are bad in a hardware sense.



Partitions 1 to 6 are all on the same drive.

This is your problem. Shrink your swap partition down in size or delete it while you clone onto the second hard drive.

Kind regards

Matt,

I've shrunk my Swap partition down to 2GB from 8GB.  There is now 6GB of unallocated space at the end of the drive in sda6.  I've bought a completely different drive; and I'm going to try cloning again.  I'll post the results when I'm done.

Thanks Hannibal

---

### Post by Slim Odds on 2013-04-22
> **coljohnhannibalsmith said:**
> <cut>
My version of Clonezilla is about 3 years old.  Does it not support 1TB HDDs, or is my drive bad.

Thanks Hannibal

A LOT has changed in three years. A LOT.

I would HIGHLY recommend a newer version of Clonzilla.

---

### Post by coljohnhannibalsmith on 2013-04-23
This is the output from GParted:


```
Partition          File System          label          size               Used          Unused          Flags
/dev/sda1        fat 16                                 39.19MiB        288.00KiB    38.19 MiB       diag
/dev/sda2        ntfs                    Recovery    19.81GiB         12.18GiB     7.63GiB          boot
/dev/sda3        ntfs                    OS             280.21GiB       60.08GiB     220.13GiB
/dev/sda4        extended                              631.45GiB                -                 -
/dev/sda5        ext4                                     623.54GiB      381.44GiB     242.10GiB
/dev/sda6        linux-swap                                1.95GiB                -                 -
unallocated      unallocated                               5.95GiB                -                 -
```

I've tried Clonezilla in Beginner, Expert, and Sector by Sector modes and the ntfs partitions get copied perfectly; but when it reaches (sda5 the linux partition) it fails with the following message:

```
Source Partition file system is ext4
/dev/sdc5 (destination drive) NOT found.

The /proc/partitions in this system:
Major          Minor          #blocks               Name
8                0               97672584             sda
8                1                    40131             sda1
8                2               20772864             sda2
8                3               293825072           sda3
8                4                            1           sda4
8                5               653834240           sda5
8                6               2048000              sda6
11              0                1048575              sr0
8                16              976896                sdb
8                17               975872               sdb1
8                32              976762584           sdc
8                33              321048                sdc1
8                34              166182912           sdc2
8                35              810251992           sdc3
7                  0              93008                 loop0

```


It appears that Clonezilla cannot see the Linux Partition no matter what I try.  Also Dell setup the blocks to be 512 Bytes instead of 4096.  I can't see why Clonezilla cannot cope with the partition table since the drives are exactly the same size.

Is there something I've missed, or is there another way to do this?  Someone recommended (rsync -xc).

If this will work how do I enter the full command when the (source drive is sda) and the (destination drive is sdc).

Thanks Hannibal

---

### Post by Slim Odds on 2013-04-23
Get a newer version of Clonezilla. Three years in an eternity with stuff like this.

---

### Post by sudodus on 2013-04-23
> **Slim Odds said:**
> Get a newer version of Clonezilla. Three years in an eternity with stuff like this.
+1

1. You need a current version of Clonezilla. We don't know how well it can handle ext4 file systems. Please listen to our advice :-)

2. After shrinking the swap partition, you need also shrink the extended partition (so that the unallocated space will be outside the extended partition). Then maybe it will work with a new Clonezilla.

---

### Post by coljohnhannibalsmith on 2013-04-23
Oh yes I forgot to mention, I now have the latest version of clonezilla.  Also, rsync does not look like it will work on a dual boot system.

Thanks Hannibal

---

### Post by sudodus on 2013-04-23
1. Check :KS

And now for the next item:

2. After shrinking the swap partition, you need also shrink the extended  partition (so that the unallocated space will be outside the extended  partition)

Good luck :-)

If this won't work, there is always dd, nicknamed 'disk destroyer'. The distance between miracle and catastrophe is minimal with dd :-P

But if you are careful and triple check before running the command, it will work with dd.

---

### Post by tgalati4 on 2013-04-23
Use the old standby, copy:

```
sudo cp /dev/sda /dev/sdb
```

Use gparted to fix any errors on /dev/sdb.  Don't forget to correct your UUID's using* blkid *in grub and /etc/fstab so that the drive will boot properly.

---

### Post by coljohnhannibalsmith on 2013-04-23
> **tgalati4 said:**
> Use the old standby, copy:

```
sudo cp /dev/sda /dev/sdb
```

Use gparted to fix any errors on /dev/sdb.  Don't forget to correct your UUID's using* blkid *in grub and /etc/fstab so that the drive will boot properly.

I've tried everything and nothing's worked.  I tried three different drives and three different versions of Clonezilla.  I now have the latest version.

Will cp also copy the boot loader?  Also, when I cp to the new drive why will I have to correct the UUID's and how do I do this?

Thanks Hannibal

---

### Post by Slim Odds on 2013-04-23
No cp is not for that. Look into dd

---

### Post by coljohnhannibalsmith on 2013-04-25
Hello,

I've tried cp and dd neither worked.  My computer behaved like it was copying the files; but the destination drive had nothing but unallocated space when I checked it with GParted.  I've also been through three different drives, three different versions of Clonzilla, and two versions of Acronis True Image.  All my drives couldn't have been bad, especially since they were brand new,  The only thing I haven't changed is my cloning kit.  Could that be at fault?

Also, I noticed that when Clonezilla copied the first three partitions, I could see the files once the drive was mounted as an external file system; however GParted read the drive as totally unallocated. So it appears that there's a read-error with my rig.  This could be Gparted's fault, the fault of my pc, or a fault with my cloning kit.

Thanks Hannibal

---

### Post by tgalati4 on 2013-04-25
The cp command takes a long time, like 20 minutes.  It's not a bit-by-bit copy but a logical copy which helps get around different drive architectures.  It will copy bootloaders, I have even cloned WinXP drives and they boot!  You have to change UUID's using the *blkid* command because drives are not always called "/dev/sda" because they can be moved around (like a USB enclosure).  UUID's are User-Unique Identification numbers that will remain the same if you move the drive to another machine or to another ribbon cable.  So any configuration file that uses UUID's needs to be updated if you want the clone to boot and mount properly.

dd is a bit-by-bit copy but you may run into problems if the disk drives have different cylinder-head-sector counts.

---

### Post by coljohnhannibalsmith on 2013-04-26
More info,

I found a very serious bug and got the following error messages:

libparted Bug Found!

Partition(s) 3 on /dev/sdc have been written but we have been unable to inform the kernel of the change, probably because it/they are in use.  As a result, the old partition(s) will remain in use.  You should reboot now before making further changes.

Also:

Error informing the kernel about modification to partition /dev/sdc1 - device or resource busy.  This means linux won't know about any changes you made to /dev/sdc1 until you reboot.  So you shouldn't mount it or use it in any way before rebooting.

Hannibal

---

### Post by Slim Odds on 2013-04-26
Is it a bug, or was the drive mounted while you were doing this?

The second is more likely.

---

### Post by coljohnhannibalsmith on 2013-04-26
I'm pretty sure the drive was not mounted.  Clonezilla will not clone mounted drives.

Hannibal

---

### Post by coljohnhannibalsmith on 2013-04-30
More info,

I finally purchased another cloneing kit SATA only from Apricorn. This time Clonezilla got farther along. It was able to read the Linux partition sda5 and tried to clone to it. It almost finished when I got a file system error. I can't remember what it was now.

The Apricorn Cloneing kit came with it's on software "EZ GIG IV." This performed a sector by sector copy which lasted 4 hours and reported no errors. Also, when I checked the destination drive with GParted I found that all the partitions had been copied; although when I tried to boot from the destination drive it gave me errors that it could not find the drive in Windows, although it did finally boot. When I tried to boot to the Linux partition it gave me two errors. The first error was the the drive could not be mounted because of errors with the drive. And, the secound error was the TMP partionion could not be setup.

I've been cloneing my drives as a method of backup for more than 5 years and have never had this much trouble. Could it be that Dell puts something on the boot sector to prevent there drive from being cloned. Also, will I have to by a retail version of Windows 7 and rebuild my system from scratch.

Is there a diagnostic program that will find and correct errors on my hard drive? I've already tried Gparted.

Any input appreciated.

Hannibal

---

### Post by sudodus on 2013-04-30
The program e2fsck is good for linux ext file systems (ext2, ext3, ext4)

```
 sudo e2fsck -f /dev/sdxy
``` where x is the drive letter and y is the partition number. It is very important that the drive is not mounted.

Windows partitions should be checked with Windows software, ```
chkdsk /f
``` or in modern versions of Windows a GUI front end for chkdsk.

---

### Post by coljohnhannibalsmith on 2013-05-01
Hello,

I tried to repair the file system and found no errors.  Also, I purchased a different cloning kit from Apricorn (SATA ONLY) and Clonezilla got a little farther along this tine.  This time it found the Linux partition sdc5 on the destination drive and failed just before completing the copy.  I then used the software that came with the cloning kit "EZ GIG IV."  It copied all the partitions with a sector by sector copy; but both the Windows & Ubuntu partitions reported drive errors such as not finding the drive, drive not ready, and the TMP folder not found.  I'm also getting drive not ready errors intermitantly on the source drive, but only in Ubuntu, not Windows.

What can I do next?

Thanks Hannibal

---

### Post by coljohnhannibalsmith on 2013-05-01
Bump.

---

### Post by sudodus on 2013-05-02
Let us start from the beginning.

1. Please check that your RAM is completely reliable: Run memtest (on of the choices on the grub menu) overnight! One single error during the whole night is too much.

2. Check the S.M.A.R.T. information, that both HDDs are healthy.

3. Please run following commands ***now*** for both drives, the source and the target and post the output.

```
sudo parted -l
```
```
sudo fdisk -lu
```

- wait -

4. I will try to see, if all the partitions in the source drive can be fit into the target drive. If the drives seem to be reasonably similar, I will probably suggest that you use ***dd*** to clone. It is one of the advanced options of Clonezilla, but you have so bad experiences with that program, that I suggest that you run dd from an Ubuntu install CD/DVD/USB drive instead.

The dd method is slower than Clonezilla, and you need to be very careful and triple check that there is no typing error. The margin between miracle and catastrophe is very narrow. If dd does not work, I think there is probably something wrong with the hardware, for example bad sectors or failing electronics in one of the drives (or the drives are too different, but it is less probable).

---

### Post by coljohnhannibalsmith on 2013-05-04
More Info,

Please see the attachments for the output of "sudo parted -l" and "sudo fdisk -lu.

Also, what is S.M.A.R.T. information and how do I get it?

Thanks Hannibal

---

### Post by sudodus on 2013-05-05
S.M.A.R.T. information is collected by the built-in systems of modern HDDs. A summary can often be seen in a BIOS setup menu.

You can also see it with smartctl that is installed with the package smartmontools
```
 sudo apt-get install smartmontools
```

See ```
man smartctl
```
There are examples near the end of the manual. For example
```
sudo smartctl -a /dev/sdb
```
```
       sudo smartctl -t long /dev/hdc
       Begin an extended self-test of drive /dev/hdc.  You can issue this command on a running system.
       The results can be seen in the self-test log visible with the ´-l selftest´ option after it has
       completed.

```

---

### Post by sudodus on 2013-05-05
Check that the last partition is within the drive (from the output of fdisk -lu)
1953523711*512=
1000204140032 which is smaller than
1000204886016.

This partition table is OK, as far as I can see from both outputs. Which drive is it, the source or target in the cloning process? (I guess the source.)

What size is the target drive? Please post the corresponding output of ```
sudo fdisk -lu
``` for the other drive!

The problem might be that the extended partition's end as well as the swap partition's end will be outside the target drive.

---

### Post by gaetanm on 2013-05-05
> **coljohnhannibalsmith said:**
> More Info,

Please see the attachments for the output of "sudo parted -l" and "sudo fdisk -lu.

Also, what is S.M.A.R.T. information and how do I get it?

Thanks Hannibal

The problem is AF drive technology verses legacy 512e vereses 512 do a tootle search on AF drives

---

