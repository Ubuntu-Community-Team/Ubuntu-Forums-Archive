---
title: "My 160GB HDD shows up as 8GB after using GParted??"
date: 2013-07-31
forum: General Help
---

### Post by dwashere on 2013-07-31
First of all - thank you to each and every one who posted in this  thread ([http://ubuntuforums.org/showthread.php?t=2052274&page=1](http://ubuntuforums.org/showthread.php?t=2052274&page=1)).  Only this way could I find this place to ask for help.

Funny enough, I do have the problem described there initially.  Earlier  today I was playing away on my T42 with an internal hard drive of 160 GB  and a perfectly running Win7 installation, when, after using GParted to  prepare for a parallel, dual-boot installation of Linux, I was suddenly  left with 7.63 GiB of unallocated space.  That's what is left of my 160  GB hard drive.

Looking at things with my non-existent TestDisk capabilities it seems to  me that the partition table might be completely messed up. 

fdisk -l -u shows all four (last/initial) partitions (three ntfs, one  ext2 <-- the one I was working on), but also only about 8 GB as total  for the disk. (Before I created a new partition table.  Now it shows  four empty partitions.)

I tried data recovery through GParted - no success.
I tried creating a new partition table through GParted - no success in regaining either hard drive or files.

Any chance I can (a) reclaim this hard drive and (b) maybe even rescue some files?

Any help truly appreciated!

Joshua

-----------

(And all I wanted was to check out Ubuntu on that T42...)

---

### Post by sudodus on 2013-07-31
Welcome to the Ubuntu Forums :-)

1. Do you have any backup of your personal files?

2. Do you have any backup or restore disk/partition for Windows 7?

If this is the case, it might be easiest to reinstall Windows 7 and copy back the personal files.

Otherwise you can try different options with ***Testdisk***. If no success, you can try ***PhotoRec*** to recover your files. As long as the file data are still there (not overwritten), you can use PhotoRec to recover them, or at least a fair amount of the files, even if the partition table is destroyed. But it is a slow and tedious process.

You find information about Testdisk and PhotoRec at the same web site [http://www.cgsecurity.org/](http://www.cgsecurity.org/)

---

### Post by dwashere on 2013-07-31
Thank you!

I do have a backup of the system (Win7).  I do not have a backup of my files there, but they are not critical files, so I have already accepted the loss.

The main problem I am having still is that my hard disk is shown as being 8GB in size - when it actually is 160GB.

I have tried dd'ing the disk - as suggested in the referenced thread -, but even after doing that, all I get is "SCSI Disk" with "size: 7811Mib".

Any ideas how to possible get this hard drive back to life?

---

### Post by dwashere on 2013-07-31
...now GParted does not see the disk at all (after I dd'ed it).  Nothing.

---

### Post by sudodus on 2013-07-31
Please describe what kind of backup you have (how you created it)!

And describe the dd command line, you were using to restore it!

If the drive is not failing physically (and I don't think so), you should be able to start from the beginning with Gparted setting up a partition table. Menu 'Device' -- 'Create partition table'.

But if you intend to run dd for the whole drive, you need no partition table. It will be overwritten anyway when you restore from the backup image.

-o-

Is your computer an IBM Thinkpad T42? I have such a computer, and you probably need a non-pae or fake-pae system to run it. So try either Xubuntu 12.04.2 LTS or Lubuntu fake-PAE (13.04, to be upgraded soon to 13.10).

Or is it some other T42? In that case, please specify the CPU, RAM size and graphics chip/card!

---

### Post by slw210 on 2013-07-31
You might try running DBAN on it. [**Darik's Boot And Nuke**]("http://www.dban.org/")

---

### Post by dwashere on 2013-07-31
> **sudodus said:**
> Please describe what kind of backup you have (how you created it)!

Proprietary software that I use for all my OS backups.  (Can't use it now, though, because the disk is said to be only 8 GiB in size.)

> **sudodus said:**
> And describe the dd command line, you were using to restore it!

I did not use dd for restoration, but to write to the file as suggested by "Bashing-om" in [this thread]("http://ubuntuforums.org/showthread.php?t=2052274&page=1").

So it was:

```
sudo dd if=/dev/zero of=/dev/sda bs=1M
```

But it only did it within the 8 GiB the disk is now supposed to have.

> **sudodus said:**
> If the drive is not failing physically (and I don't think so), you should be able to start from the beginning with Gparted setting up a partition table. Menu 'Device' -- 'Create partition table'.

I tried that, to no avail, unfortunately.

> **sudodus said:**
> But if you intend to run dd for the whole drive, you need no partition table. It will be overwritten anyway when you restore from the backup image.

Cannot restore anything, because the needed disk space is not "seen", ie. the 160GB disk is said to be an 8GB disk.

> **sudodus said:**
> Is your computer an IBM Thinkpad T42? I have such a computer, and you probably need a non-pae or fake-pae system to run it. So try either Xubuntu 12.04.2 LTS or Lubuntu fake-PAE (13.04, to be upgraded soon to 13.10).

Yes, that's why a straight-forward Ubuntu installation would not work.  I intended to install a previous version and then try to upgrade, as that is one way it is supposed to work.  I do want to try out Unity.

If that had not worked, I would have tried installing Xubuntu and then Unity.  But I never got that far...

---

### Post by dwashere on 2013-07-31
> **slw210 said:**
> You might try running DBAN on it. [**Darik's Boot And Nuke**]("http://www.dban.org/")

Will check it out tomorrow.  Thanks!  I am afraid, though, it might just do as all other software seems to do - (a) see the drive as 8 GiB, and then (b) either stick within that limit or fail to work at all.  :(  But I will give it a try!

---

### Post by oldfred on 2013-07-31
This will show model info on drives:
sudo lshw -C Disk -short


And this shows more detail:
sudo lshw -class disk

---

### Post by sudodus on 2013-08-01
> **dwashere said:**
> Proprietary software that I use for all my OS backups.  (Can't use it now, though, because the disk is said to be only 8 GiB in size.)



I did not use dd for restoration, but to write to the file as suggested by "Bashing-om" in [this thread]("http://ubuntuforums.org/showthread.php?t=2052274&page=1").

So it was:

```
sudo dd if=/dev/zero of=/dev/sda bs=1M
```

But it only did it within the 8 GiB the disk is now supposed to have.


That command wiped [the available part of] the drive including the boot sector and the partition table.
> 

I tried that, to no avail, unfortunately.



Cannot restore anything, because the needed disk space is not "seen", ie. the 160GB disk is said to be an 8GB disk.

[QUOTE]Is your computer an IBM Thinkpad T42? I have such a computer, and you  probably need a non-pae or fake-pae system to run it. So try either  Xubuntu 12.04.2 LTS or Lubuntu fake-PAE (13.04, to be upgraded soon to  13.10).

Yes, that's why a straight-forward Ubuntu installation would not work.  I intended to install a previous version and then try to upgrade, as that is one way it is supposed to work.  I do want to try out Unity.

If that had not worked, I would have tried installing Xubuntu and then Unity.  But I never got that far...[/QUOTE]

I think you have a Pentium M CPU with PAE capability but no PAE flag. I run new PAE kernels of Lubuntu 13.04 and Saucy (13.10 alpha-2) using fake-PAE. It is also possible to run Xubuntu 12.04 LTS, but I think Ubuntu with Unity will be slow on that computer. See this link

[https://help.ubuntu.com/community/Lubuntu-fake-PAE](https://help.ubuntu.com/community/Lubuntu-fake-PAE)

I don't know enough to understand your problem with the hard disk drive.

Try to run some kind of Linux (for example Xubuntu 12.04 LTS or one of the versions of Lubuntu-fake-PAE. Boot a live session from a CD or USB drive and please post the output of the following commands:

```
sudo fdisk -lu
```
```
sudo parted -l
```
```
sudo blkid
```

Try to mount as many partitions as possible. Use the file browser: click on the icons and mount the partitions, that are shown in the left panel of the file browser. Then run

```
df
```

Please post the output between code tags like this
 
[noparse]```
output
```[/noparse]
 
to get output like this
 
```
output
```

This will show details about your hard disk drive: how it is partitioned, what is free space and what is unallocated space.

---

### Post by dwashere on 2013-08-01
> **oldfred said:**
> This will show model info on drives:
sudo lshw -C Disk -short

```
ubuntu@ubuntu:~$ sudo lshw -C Disk -short
H/W path         Device      Class          Description
=======================================================
/0/100/1f.1/0    /dev/sda    disk           8190MB QAMSUNE HM160HA
/0/100/1f.1/1    /dev/cdrom  disk           RW/DVD GCC-4242N
/0/100/1f.1/1/0  /dev/cdrom  disk           
/0/1/0.0.0       /dev/sdb    disk           2021MB SCSI Disk

```

**/dev/sda** is the 160GB hard drive in the IBM T42.
**/dev/sdb** is the USB stick I used to save terminal output into a text file so I could paste it into here.

> **oldfred said:**
>  And this shows more detail:
sudo lshw -class disk

```
ubuntu@ubuntu:~$ sudo lshw -class disk
  *-disk                  
       description: SCSI Disk
       physical id: 0
       bus info: scsi@0:0.0.0
       logical name: /dev/sda
       size: 7811MiB (8190MB)
  *-cdrom
       description: DVD reader
       product: RW/DVD GCC-4242N
       vendor: HL-DT-ST
       physical id: 1
       bus info: scsi@1:0.0.0
       logical name: /dev/cdrom
       logical name: /dev/cdrw
       logical name: /dev/dvd
       logical name: /dev/scd0
       logical name: /dev/sr0
       logical name: /cdrom
       version: 0201
       capabilities: removable audio cd-r cd-rw dvd
       configuration: ansiversion=5 mount.fstype=iso9660 mount.options=ro,noatime state=mounted status=ready
     *-medium
          physical id: 0
          logical name: /dev/cdrom
          logical name: /cdrom
          configuration: mount.fstype=iso9660 mount.options=ro,noatime state=mounted
  *-disk
       description: SCSI Disk
       physical id: 0.0.0
       bus info: scsi@2:0.0.0
       logical name: /dev/sdb
       size: 1928MiB (2021MB)
       capabilities: partitioned partitioned:dos
       configuration: signature=04dd5721


```

---

### Post by sudodus on 2013-08-01
> **slw210 said:**
> You might try running DBAN on it. [**Darik's Boot And Nuke**]("http://www.dban.org/")

This might help.

> **dwashere said:**
> ```
ubuntu@ubuntu:~$ sudo lshw -C Disk -short
H/W path         Device      Class          Description
=======================================================
/0/100/1f.1/0    /dev/sda    disk           8190MB QAMSUNE HM160HA
/0/100/1f.1/1    /dev/cdrom  disk           RW/DVD GCC-4242N
/0/100/1f.1/1/0  /dev/cdrom  disk           
/0/1/0.0.0       /dev/sdb    disk           2021MB SCSI Disk

```

**/dev/sda** is the 160GB hard drive in the IBM T42.
**/dev/sdb** is the USB stick I used to save terminal output into a text file so I could paste it into here.



```
ubuntu@ubuntu:~$ sudo lshw -class disk
  *-disk                  
       description: SCSI Disk
       physical id: 0
       bus info: scsi@0:0.0.0
       logical name: /dev/sda
       size: 7811MiB (8190MB)
  *-cdrom
       description: DVD reader
       product: RW/DVD GCC-4242N
       vendor: HL-DT-ST
       physical id: 1
       bus info: scsi@1:0.0.0
       logical name: /dev/cdrom
       logical name: /dev/cdrw
       logical name: /dev/dvd
       logical name: /dev/scd0
       logical name: /dev/sr0
       logical name: /cdrom
       version: 0201
       capabilities: removable audio cd-r cd-rw dvd
       configuration: ansiversion=5 mount.fstype=iso9660 mount.options=ro,noatime state=mounted status=ready
     *-medium
          physical id: 0
          logical name: /dev/cdrom
          logical name: /cdrom
          configuration: mount.fstype=iso9660 mount.options=ro,noatime state=mounted
  *-disk
       description: SCSI Disk
       physical id: 0.0.0
       bus info: scsi@2:0.0.0
       logical name: /dev/sdb
       size: 1928MiB (2021MB)
       capabilities: partitioned partitioned:dos
       configuration: signature=04dd5721


```

It really looks like the drive 'thinks' it is only 8 GB. Very strange. Somehow it has been damaged at a fundamental level. Maybe DBAN will help.

But 8 GB is actually enough to host Lubuntu, so you could try to install Lubuntu-fake-PAE using the 'grub-n-iso' method.

---

### Post by dwashere on 2013-08-01
> **sudodus said:**
> I think you have a Pentium M CPU with PAE capability but no PAE flag. I run new PAE kernels of Lubuntu 13.04 and Saucy (13.10 alpha-2) using fake-PAE. It is also possible to run Xubuntu 12.04 LTS, but I think Ubuntu with Unity will be slow on that computer. See this link

[https://help.ubuntu.com/community/Lubuntu-fake-PAE](https://help.ubuntu.com/community/Lubuntu-fake-PAE)



Yes, that's how I see it, too.  No PAE flag.  Thank you for pointing me towards "fake-PAE" - that is new information for me.  Will check it out.  As to Ubuntu with Unity being slow - I read that a few times, but I still wanted to try it out for myself.  I really like the concept of Unity, so it is kind of a deal breaker for me.

> **sudodus said:**
>  I don't know enough to understand your problem with the hard disk drive.

[...] 

> **sudodus said:**
> please post the output of the following commands:

> **sudodus said:**
>  ```
sudo fdisk -lu
```

```
ubuntu@ubuntu:~$ sudo fdisk -lu
ubuntu@ubuntu:~$ sudo fdisk -lu
```

No output. Nothing. 

> **sudodus said:**
>  ```
sudo parted -l
```

```
ubuntu@ubuntu:~$ sudo parted -l
Error: /dev/sda: unrecognised disk label
Warning: Unable to open /dev/sr0 read-write (Read-only file system).  /dev/sr0
has been opened read-only.
Error: /dev/sr0: unrecognised disk label
```

> **sudodus said:**
> ```
sudo blkid
```

```
ubuntu@ubuntu:~$ sudo blkid
/dev/loop0: TYPE="squashfs"
```

> **sudodus said:**
>  Try to mount as many partitions as possible. Use the file browser: click on the icons and mount the partitions, that are shown in the left panel of the file browser. Then run

```
df
```

There is nothing to mount. :icon_frown:

---

### Post by matt_symes on 2013-08-01
Hi

What does the hard drives firmware think of the situation ?

```
sudo hdparm -I /dev/sda
```

Capital i above after the dash.

Please post the output back here.

Kind regards

---

### Post by dwashere on 2013-08-01
> **sudodus said:**
> It really looks like the drive 'thinks' it is only 8 GB. Very strange. Somehow it has been damaged at a fundamental level.

So that *would* be possible?  To "turn" a 160GB hard drive into an 8GB hard drive?  Simply by messing with the partitions?

> **sudodus said:**
>  But 8 GB is actually enough to host Lubuntu, so you could try to install Lubuntu-fake-PAE using the 'grub-n-iso' method.

I am running a LIVE ISO of Ubuntu 11.04, and I have tried installing it into the 8GB shown.  Nothing doing!  All I get it "input/output error" or that the partition could not be mounted.  So not even the 8GB it shows can be put to any use.

How can that be?

**Background Info**

_Where was I coming from?_
IBM T42 with Win7 running perfectly fine with all the Aero stuff enabled.  Everything worked swell - sleep, hibernation, wake-up, WiFi, everything.

_What did I try to do?_
Set up dual-boot with Ubuntu in order to check Ubuntu out.

_How did I try to do it?_
Just before my hard disk got completely screwed up, was at the following place.

160GB hard disk partitioned like this:

sda1 | 100MB | Win7 | NTFS | Primary
sda2 | 50GB   | Win7 | NTFS | Primary, boot
sda3 | 65GB   | Files  | NTFS | Primary
sda4 | 45GB   | Linux | ext4  | Primary

I intended to install Linux into sda4.  At the beginning of the installation process, Xubuntu let me know it would prefer to have a swap partition.  So I thought I would create one.

I fire up GParted and went to work at sda4 (all queued):

(1) Change sda4 from Primary to Extened.
(2) Create two logical partitions within that extended partition.

Then I let GParted execute that, expecting nothing worse than total data loss on the drive (not the loss of a physical drive).  GParted through up an error, aborted the process, and suddenly I was left with this unusable hard drive thinking its size was 8GB.

What could have happened there?  Any chance I can get this hard drive back to work?

I will definitely try out DBAN.

---

### Post by dwashere on 2013-08-01
> **matt_symes said:**
> Hi

What does the hard drives firmware think of the situation ?

```
sudo hdparm -I /dev/sda
```


```
ubuntu@ubuntu:~$ sudo hdparm -I /dev/sda

/dev/sda:
 HDIO_DRIVE_CMD(identify) failed: Input/output error
```

That does not look good, does it?  What have I done? :shock:

---

### Post by dwashere on 2013-08-01
...or did it just happen to die at that very moment?  But what about the size anomaly? :confused:

---

### Post by matt_symes on 2013-08-01
Hi

> **dwashere said:**
> ```
ubuntu@ubuntu:~$ sudo hdparm -I /dev/sda

/dev/sda:
 HDIO_DRIVE_CMD(identify) failed: Input/output error
```

That does not look good, does it?  What have I done? :shock:

No. That does not look too good. 

Have you checked the drives settings in the BIOS ? What are they set to ? AHCI / IDE ? Any other drive settings ?

What does this return (from a live cd/usb) ?

```
dmesg | grep -iE "sda|ata"
```

or 

 ```
grep -iE "sda|ata" /var/log/syslog
```

Check the drives cables (if any), check the drive is securely attached, try the drive with the same command in another drive bay if possible.

Kind regards

---

### Post by sudodus on 2013-08-01
> **dwashere said:**
> So that *would* be possible?  To "turn" a 160GB hard drive into an 8GB hard drive?  Simply by messing with the partitions?



I am running a LIVE ISO of Ubuntu 11.04, and I have tried installing it into the 8GB shown.  Nothing doing!  All I get it "input/output error" or that the partition could not be mounted.  So not even the 8GB it shows can be put to any use.

How can that be?

**Background Info**

_Where was I coming from?_
IBM T42 with Win7 running perfectly fine with all the Aero stuff enabled.  Everything worked swell - sleep, hibernation, wake-up, WiFi, everything.

_What did I try to do?_
Set up dual-boot with Ubuntu in order to check Ubuntu out.

_How did I try to do it?_
Just before my hard disk got completely screwed up, was at the following place.

160GB hard disk partitioned like this:

sda1 | 100MB | Win7 | NTFS | Primary
sda2 | 50GB   | Win7 | NTFS | Primary, boot
sda3 | 65GB   | Files  | NTFS | Primary
sda4 | 45GB   | Linux | ext4  | Primary

I intended to install Linux into sda4.  At the beginning of the installation process, Xubuntu let me know it would prefer to have a swap partition.  So I thought I would create one.

I fire up GParted and went to work at sda4 (all queued):

(1) Change sda4 from Primary to Extened.
(2) Create two logical partitions within that extended partition.

Then I let GParted execute that, expecting nothing worse than total data loss on the drive (not the loss of a physical drive).  GParted through up an error, aborted the process, and suddenly I was left with this unusable hard drive thinking its size was 8GB.

What could have happened there?  Any chance I can get this hard drive back to work?

I will definitely try out DBAN.

This is a very good description of what you did. And I do not see anything wrong. I have used gparted like that many times successfully. There are risks, but as you said, "... expecting nothing worse than total data loss on the drive (not the loss of a physical drive)".

One very unlikely event is that your drive was physically damaged at the same time as you used gparted.

Another unlikely event is that there is some yet unknown bug in the firmware/BIOS or gparted, so that it could write where it should not write.

***DBAN*** suggested by *slw210*, or ***hdparm*** suggested by *matt_symes* might help you repair the drive or (hdparm) find some error.

You can also check if the drive has ***S.M.A.R.T.*** which monitors the physical status (bad sectors). The drive is old and might not have it, but it is worth installing and checking. The drive in my T42 has ***S.M.A.R.T.***

```
sudo apt-get install smartmontools
```

```
sudo smartctl -H /dev/sda
```

See more advanced options in the manual

```
man smartctl
```

---

### Post by dwashere on 2013-08-01
Running DBAN with about two hours to go.  Drive is listed there as "[...] 7811MB [...]" drive.  Would a running time (DBAN "autonuke") between two and a half or three hours relate more to 8GB or 160GB? (Still hoping [-o< )

Will proceed from there, then, once it has completed.

---

### Post by matt_symes on 2013-08-01
Hi

As well as my last post, can you also post the output of

```
sudo hdparm -N /dev/sda
```

Capital N above.

And also try sudodus smartctl proprosal.

Edit: i see you have just tried dban. 

I am thinking drive firmware corruption or invalid HPA setting maybe ?

Kind regards

---

### Post by dwashere on 2013-08-01
(Waiting for DBAN to complete.)

---

### Post by sudodus on 2013-08-01
> **dwashere said:**
> Running DBAN with about two hours to go.  Drive is listed there as "[...] 7811MB [...]" drive.  Would a running time (DBAN "autonuke") between two and a half or three hours relate more to 8GB or 160GB? (Still hoping [-o< )

Will proceed from there, then, once it has completed.

I used hdparm to do a similar thing with a 250 GB drive and it needed about that time. This low level process is much faster than dd overwriting with zeros. So there is still hope :-)

---

### Post by dwashere on 2013-08-01
DBAN completed with errors.  The error count at the end went up to nearly 2,000, and eventually it finished with "non-fatal errors".  I was referred to a log that I cannot seem to access, since DBAN now seems to be stuck in advertising mode. :confused: 

EDIT: Maybe I would have needed some place to save a log?

---

### Post by matt_symes on 2013-08-01
Hi

What about the output from the posts #18 and #21.

What do they return ?

Kind regards

---

### Post by dwashere on 2013-08-01
> **matt_symes said:**
> Hi

What about the output from the posts #18 and #21.

What do they return ?

Kind regards

#18 is here:

```
ubuntu@ubuntu:~$ dmesg | grep -iE "sda|ata"
[    0.000000]  BIOS-e820: 000000005ff60000 - 000000005ff77000 (ACPI data)
[    0.000000] Memory: 1528476k/1572224k available (5188k kernel code, 43296k reserved, 2540k data, 700k init, 662920k highmem)
[    0.000000]       .data : 0xc15112a1 - 0xc178c480   (2540 kB)
[    0.060560] ACPI: EC: GPE = 0x1c, I/O: command/status = 0x66, data = 0x62
[    0.069536] libata version 3.00 loaded.
[    3.578301] ata_piix 0000:00:1f.1: version 2.13
[    3.578540] ata_piix 0000:00:1f.1: PCI INT A -> Link[LNKC] -> GSI 11 (level, low) -> IRQ 11
[    3.578600] ata_piix 0000:00:1f.1: setting latency timer to 64
[    3.584087] scsi0 : ata_piix
[    3.584334] scsi1 : ata_piix
[    3.585017] ata1: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0x1860 irq 14
[    3.585022] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0x1868 irq 15
[    4.779419] ata2.00: ATAPI: HL-DT-STCD-RW/DVD DRIVE GCC-4242N, 0201, max UDMA/33
[    4.784494] ata1.00: ATA-8: QAMSUNE HM160HA, LQ100-10, max UDMA/100
[    4.784499] ata1.00: 15997968 sectors, multi 16, CHS 15871/16/63
[    4.792177] ata1.00: configured for UDMA/100
[    4.792375] scsi 0:0:0:0: Direct-Access     ATA      QAMSUNE HM160HA  LQ10 PQ: 0 ANSI: 5
[    4.792721] sd 0:0:0:0: [sda] 15997968 512-byte logical blocks: (8.19 GB/7.62 GiB)
[    4.792794] sd 0:0:0:0: [sda] Write Protect is off
[    4.792798] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    4.792830] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    4.793433] ata2.00: configured for UDMA/33
[    4.873169] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6
[    4.873173] ata1.00: BMDMA stat 0x24
[    4.873178] ata1.00: failed command: READ DMA
[    4.873186] ata1.00: cmd c8/00:08:01:00:00/00:00:00:00:00/a0 tag 0 dma 4096 in
[    4.873188]          res 51/84:00:08:00:00/00:00:00:00:00/a0 Emask 0x10 (ATA bus error)
[    4.873192] ata1.00: status: { DRDY ERR }
[    4.873195] ata1.00: error: { ICRC ABRT }
[    4.873232] ata1: soft resetting link
[    5.052260] ata1.00: configured for UDMA/100
[    5.052269] ata1: EH complete
[    5.082669] ata1.00: limiting speed to UDMA/66:PIO4
[    5.082673] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6
[    5.082676] ata1.00: BMDMA stat 0x24
[    5.082679] ata1.00: failed command: READ DMA
[    5.082687] ata1.00: cmd c8/00:08:01:00:00/00:00:00:00:00/a0 tag 0 dma 4096 in
[    5.082689]          res 51/84:00:08:00:00/00:00:00:00:00/a0 Emask 0x10 (ATA bus error)
[    5.082693] ata1.00: status: { DRDY ERR }
[    5.082696] ata1.00: error: { ICRC ABRT }
[    5.082725] ata1: soft resetting link
[    5.260257] ata1.00: configured for UDMA/66
[    5.260263] ata1: EH complete
[    5.292173] ata1.00: limiting speed to UDMA/33:PIO4
[    5.292177] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6
[    5.292180] ata1.00: BMDMA stat 0x24
[    5.292184] ata1.00: failed command: READ DMA
[    5.292191] ata1.00: cmd c8/00:08:01:00:00/00:00:00:00:00/a0 tag 0 dma 4096 in
[    5.292193]          res 51/84:00:08:00:00/00:00:00:00:00/a0 Emask 0x10 (ATA bus error)
[    5.292197] ata1.00: status: { DRDY ERR }
[    5.292200] ata1.00: error: { ICRC ABRT }
[    5.292229] ata1: soft resetting link
[    5.472259] ata1.00: configured for UDMA/33
[    5.472265] ata1: EH complete
[    5.501677] ata1.00: limiting speed to PIO4
[    5.501680] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6
[    5.501684] ata1.00: BMDMA stat 0x24
[    5.501687] ata1.00: failed command: READ DMA
[    5.501695] ata1.00: cmd c8/00:08:01:00:00/00:00:00:00:00/a0 tag 0 dma 4096 in
[    5.501697]          res 51/84:00:08:00:00/00:00:00:00:00/a0 Emask 0x10 (ATA bus error)
[    5.501700] ata1.00: status: { DRDY ERR }
[    5.501703] ata1.00: error: { ICRC ABRT }
[    5.501732] ata1: soft resetting link
[    5.680256] ata1.00: configured for PIO4
[    5.680262] ata1: EH complete
[    5.689934]  sda: unknown partition table
[    5.690082] sda: detected capacity change from 0 to 8190959616
[    5.690207] sda: detected capacity change from 0 to 8190959616
[    5.690320] sd 0:0:0:0: [sda] Attached SCSI disk
[    5.690967] Write protecting the kernel read-only data: 2148k
[   79.775193] libipw: 802.11 data/management/control stack, git-1.1.13
[  231.354308] EXT4-fs (sda1): Couldn't mount because of unsupported optional features (2000000)
[  601.763022] EXT4-fs (sda1): Couldn't mount because of unsupported optional features (2000000)
[  763.070402] sd 0:0:0:0: [sda] Synchronizing SCSI cache
[  763.070549] sd 0:0:0:0: [sda] Stopping disk
[  763.477842] ata_piix 0000:00:1f.1: PCI INT A disabled
[  763.477848] PM: suspend of drv:ata_piix dev:0000:00:1f.1 complete after 339.578 msecs
[  764.052309] ata_piix 0000:00:1f.1: restoring config space at offset 0x9 (was 0x0, writing 0x60000000)
[  764.053685] ata_piix 0000:00:1f.1: PCI INT A -> Link[LNKC] -> GSI 11 (level, low) -> IRQ 11
[  764.053690] ata_piix 0000:00:1f.1: setting latency timer to 64
[  764.227335] sd 0:0:0:0: [sda] Starting disk
[  764.326619] ata1.00: NODEV after polling detection
[  764.326623] ata1.00: revalidation failed (errno=-2)
[  769.224131] ata2.00: ACPI cmd ef/03:42:00:00:00:a0 (SET FEATURES) filtered out
[  769.224136] ata2.00: ACPI cmd ef/03:0c:00:00:00:a0 (SET FEATURES) filtered out
[  769.224666] ata2.00: ACPI cmd e3/00:1f:00:00:00:a0 (IDLE) succeeded
[  769.225236] ata2.00: ACPI cmd e3/00:02:00:00:00:a0 (IDLE) succeeded
[  769.248181] ata2.00: configured for UDMA/33
[  769.380173] ata1.00: NODEV after polling detection
[  769.380176] ata1.00: revalidation failed (errno=-2)
[  774.536173] ata1.00: NODEV after polling detection
[  774.536176] ata1.00: revalidation failed (errno=-2)
[  774.536178] ata1.00: disabled
[  774.536204] ata1: soft resetting link
[  774.692078] ata1: EH complete
[  774.692101] sd 0:0:0:0: [sda] START_STOP FAILED
[  774.692104] sd 0:0:0:0: [sda]  Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK

```

```
ubuntu@ubuntu:~$ grep -iE "sda|ata" /var/log/syslog
Aug  1 18:55:28 ubuntu kernel: [    0.000000]  BIOS-e820: 000000005ff60000 - 000000005ff77000 (ACPI data)
Aug  1 18:55:28 ubuntu kernel: [    0.000000] Memory: 1528476k/1572224k available (5188k kernel code, 43296k reserved, 2540k data, 700k init, 662920k highmem)
Aug  1 18:55:28 ubuntu kernel: [    0.000000]       .data : 0xc15112a1 - 0xc178c480   (2540 kB)
Aug  1 18:55:28 ubuntu kernel: [    0.060560] ACPI: EC: GPE = 0x1c, I/O: command/status = 0x66, data = 0x62
Aug  1 18:55:28 ubuntu kernel: [    0.069536] libata version 3.00 loaded.
Aug  1 18:55:28 ubuntu kernel: [    3.578301] ata_piix 0000:00:1f.1: version 2.13
Aug  1 18:55:28 ubuntu kernel: [    3.578540] ata_piix 0000:00:1f.1: PCI INT A -> Link[LNKC] -> GSI 11 (level, low) -> IRQ 11
Aug  1 18:55:28 ubuntu kernel: [    3.578600] ata_piix 0000:00:1f.1: setting latency timer to 64
Aug  1 18:55:28 ubuntu kernel: [    3.584087] scsi0 : ata_piix
Aug  1 18:55:28 ubuntu kernel: [    3.584334] scsi1 : ata_piix
Aug  1 18:55:28 ubuntu kernel: [    3.585017] ata1: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0x1860 irq 14
Aug  1 18:55:28 ubuntu kernel: [    3.585022] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0x1868 irq 15
Aug  1 18:55:28 ubuntu kernel: [    4.779419] ata2.00: ATAPI: HL-DT-STCD-RW/DVD DRIVE GCC-4242N, 0201, max UDMA/33
Aug  1 18:55:28 ubuntu kernel: [    4.784494] ata1.00: ATA-8: QAMSUNE HM160HA, LQ100-10, max UDMA/100
Aug  1 18:55:28 ubuntu kernel: [    4.784499] ata1.00: 15997968 sectors, multi 16, CHS 15871/16/63
Aug  1 18:55:28 ubuntu kernel: [    4.792177] ata1.00: configured for UDMA/100
Aug  1 18:55:28 ubuntu kernel: [    4.792375] scsi 0:0:0:0: Direct-Access     ATA      QAMSUNE HM160HA  LQ10 PQ: 0 ANSI: 5
Aug  1 18:55:28 ubuntu kernel: [    4.792721] sd 0:0:0:0: [sda] 15997968 512-byte logical blocks: (8.19 GB/7.62 GiB)
Aug  1 18:55:28 ubuntu kernel: [    4.792794] sd 0:0:0:0: [sda] Write Protect is off
Aug  1 18:55:28 ubuntu kernel: [    4.792798] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
Aug  1 18:55:28 ubuntu kernel: [    4.792830] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Aug  1 18:55:28 ubuntu kernel: [    4.793433] ata2.00: configured for UDMA/33
Aug  1 18:55:28 ubuntu kernel: [    4.873169] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6
Aug  1 18:55:28 ubuntu kernel: [    4.873173] ata1.00: BMDMA stat 0x24
Aug  1 18:55:28 ubuntu kernel: [    4.873178] ata1.00: failed command: READ DMA
Aug  1 18:55:28 ubuntu kernel: [    4.873186] ata1.00: cmd c8/00:08:01:00:00/00:00:00:00:00/a0 tag 0 dma 4096 in
Aug  1 18:55:28 ubuntu kernel: [    4.873188]          res 51/84:00:08:00:00/00:00:00:00:00/a0 Emask 0x10 (ATA bus error)
Aug  1 18:55:28 ubuntu kernel: [    4.873192] ata1.00: status: { DRDY ERR }
Aug  1 18:55:28 ubuntu kernel: [    4.873195] ata1.00: error: { ICRC ABRT }
Aug  1 18:55:28 ubuntu kernel: [    4.873232] ata1: soft resetting link
Aug  1 18:55:28 ubuntu kernel: [    5.052260] ata1.00: configured for UDMA/100
Aug  1 18:55:28 ubuntu kernel: [    5.052269] ata1: EH complete
Aug  1 18:55:28 ubuntu kernel: [    5.082669] ata1.00: limiting speed to UDMA/66:PIO4
Aug  1 18:55:28 ubuntu kernel: [    5.082673] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6
Aug  1 18:55:28 ubuntu kernel: [    5.082676] ata1.00: BMDMA stat 0x24
Aug  1 18:55:28 ubuntu kernel: [    5.082679] ata1.00: failed command: READ DMA
Aug  1 18:55:28 ubuntu kernel: [    5.082687] ata1.00: cmd c8/00:08:01:00:00/00:00:00:00:00/a0 tag 0 dma 4096 in
Aug  1 18:55:28 ubuntu kernel: [    5.082689]          res 51/84:00:08:00:00/00:00:00:00:00/a0 Emask 0x10 (ATA bus error)
Aug  1 18:55:28 ubuntu kernel: [    5.082693] ata1.00: status: { DRDY ERR }
Aug  1 18:55:28 ubuntu kernel: [    5.082696] ata1.00: error: { ICRC ABRT }
Aug  1 18:55:28 ubuntu kernel: [    5.082725] ata1: soft resetting link
Aug  1 18:55:28 ubuntu kernel: [    5.260257] ata1.00: configured for UDMA/66
Aug  1 18:55:28 ubuntu kernel: [    5.260263] ata1: EH complete
Aug  1 18:55:28 ubuntu kernel: [    5.292173] ata1.00: limiting speed to UDMA/33:PIO4
Aug  1 18:55:28 ubuntu kernel: [    5.292177] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6
Aug  1 18:55:28 ubuntu kernel: [    5.292180] ata1.00: BMDMA stat 0x24
Aug  1 18:55:28 ubuntu kernel: [    5.292184] ata1.00: failed command: READ DMA
Aug  1 18:55:28 ubuntu kernel: [    5.292191] ata1.00: cmd c8/00:08:01:00:00/00:00:00:00:00/a0 tag 0 dma 4096 in
Aug  1 18:55:28 ubuntu kernel: [    5.292193]          res 51/84:00:08:00:00/00:00:00:00:00/a0 Emask 0x10 (ATA bus error)
Aug  1 18:55:28 ubuntu kernel: [    5.292197] ata1.00: status: { DRDY ERR }
Aug  1 18:55:28 ubuntu kernel: [    5.292200] ata1.00: error: { ICRC ABRT }
Aug  1 18:55:28 ubuntu kernel: [    5.292229] ata1: soft resetting link
Aug  1 18:55:28 ubuntu kernel: [    5.472259] ata1.00: configured for UDMA/33
Aug  1 18:55:28 ubuntu kernel: [    5.472265] ata1: EH complete
Aug  1 18:55:28 ubuntu kernel: [    5.501677] ata1.00: limiting speed to PIO4
Aug  1 18:55:28 ubuntu kernel: [    5.501680] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6
Aug  1 18:55:28 ubuntu kernel: [    5.501684] ata1.00: BMDMA stat 0x24
Aug  1 18:55:28 ubuntu kernel: [    5.501687] ata1.00: failed command: READ DMA
Aug  1 18:55:28 ubuntu kernel: [    5.501695] ata1.00: cmd c8/00:08:01:00:00/00:00:00:00:00/a0 tag 0 dma 4096 in
Aug  1 18:55:28 ubuntu kernel: [    5.501697]          res 51/84:00:08:00:00/00:00:00:00:00/a0 Emask 0x10 (ATA bus error)
Aug  1 18:55:28 ubuntu kernel: [    5.501700] ata1.00: status: { DRDY ERR }
Aug  1 18:55:28 ubuntu kernel: [    5.501703] ata1.00: error: { ICRC ABRT }
Aug  1 18:55:28 ubuntu kernel: [    5.501732] ata1: soft resetting link
Aug  1 18:55:28 ubuntu kernel: [    5.680256] ata1.00: configured for PIO4
Aug  1 18:55:28 ubuntu kernel: [    5.680262] ata1: EH complete
Aug  1 18:55:28 ubuntu kernel: [    5.689934]  sda: unknown partition table
Aug  1 18:55:28 ubuntu kernel: [    5.690082] sda: detected capacity change from 0 to 8190959616
Aug  1 18:55:28 ubuntu kernel: [    5.690207] sda: detected capacity change from 0 to 8190959616
Aug  1 18:55:28 ubuntu kernel: [    5.690320] sd 0:0:0:0: [sda] Attached SCSI disk
Aug  1 18:55:28 ubuntu kernel: [    5.690967] Write protecting the kernel read-only data: 2148k
Aug  1 18:55:35 ubuntu modem-manager[1278]: <info>  Loaded plugin AnyData
Aug  1 18:55:39 ubuntu kernel: [   79.775193] libipw: 802.11 data/management/control stack, git-1.1.13
Aug  1 18:57:07 ubuntu activate-dmraid: No Serial ATA RAID disks detected
Aug  1 18:58:11 ubuntu kernel: [  231.354308] EXT4-fs (sda1): Couldn't mount because of unsupported optional features (2000000)
Aug  1 18:58:11 ubuntu ubiquity: mount: wrong fs type, bad option, bad superblock on /dev/sda1,
Aug  1 19:04:10 ubuntu activate-dmraid: No Serial ATA RAID disks detected
Aug  1 19:04:18 ubuntu os-prober: debug: running /usr/lib/os-probes/50mounted-tests on /dev/sda1
Aug  1 19:04:21 ubuntu kernel: [  601.763022] EXT4-fs (sda1): Couldn't mount because of unsupported optional features (2000000)
Aug  1 19:04:21 ubuntu os-prober: debug: running /usr/lib/os-probes/50mounted-tests on /dev/sda2
Aug  1 19:04:21 ubuntu 50mounted-tests: debug: /dev/sda2 type not recognised; skipping
Aug  1 19:04:21 ubuntu os-prober: debug: running /usr/lib/os-probes/50mounted-tests on /dev/sda5
Aug  1 19:04:21 ubuntu 50mounted-tests: debug: /dev/sda5 type not recognised; skipping
Aug  1 22:18:13 ubuntu kernel: [  763.070402] sd 0:0:0:0: [sda] Synchronizing SCSI cache
Aug  1 22:18:13 ubuntu kernel: [  763.070549] sd 0:0:0:0: [sda] Stopping disk
Aug  1 22:18:13 ubuntu kernel: [  763.477842] ata_piix 0000:00:1f.1: PCI INT A disabled
Aug  1 22:18:13 ubuntu kernel: [  763.477848] PM: suspend of drv:ata_piix dev:0000:00:1f.1 complete after 339.578 msecs
Aug  1 22:18:13 ubuntu kernel: [  764.052309] ata_piix 0000:00:1f.1: restoring config space at offset 0x9 (was 0x0, writing 0x60000000)
Aug  1 22:18:13 ubuntu kernel: [  764.053685] ata_piix 0000:00:1f.1: PCI INT A -> Link[LNKC] -> GSI 11 (level, low) -> IRQ 11
Aug  1 22:18:13 ubuntu kernel: [  764.053690] ata_piix 0000:00:1f.1: setting latency timer to 64
Aug  1 22:18:13 ubuntu kernel: [  764.227335] sd 0:0:0:0: [sda] Starting disk
Aug  1 22:18:13 ubuntu kernel: [  764.326619] ata1.00: NODEV after polling detection
Aug  1 22:18:13 ubuntu kernel: [  764.326623] ata1.00: revalidation failed (errno=-2)
Aug  1 22:18:13 ubuntu kernel: [  769.224131] ata2.00: ACPI cmd ef/03:42:00:00:00:a0 (SET FEATURES) filtered out
Aug  1 22:18:13 ubuntu kernel: [  769.224136] ata2.00: ACPI cmd ef/03:0c:00:00:00:a0 (SET FEATURES) filtered out
Aug  1 22:18:13 ubuntu kernel: [  769.224666] ata2.00: ACPI cmd e3/00:1f:00:00:00:a0 (IDLE) succeeded
Aug  1 22:18:13 ubuntu kernel: [  769.225236] ata2.00: ACPI cmd e3/00:02:00:00:00:a0 (IDLE) succeeded
Aug  1 22:18:13 ubuntu kernel: [  769.248181] ata2.00: configured for UDMA/33
Aug  1 22:18:13 ubuntu kernel: [  769.380173] ata1.00: NODEV after polling detection
Aug  1 22:18:13 ubuntu kernel: [  769.380176] ata1.00: revalidation failed (errno=-2)
Aug  1 22:18:13 ubuntu kernel: [  774.536173] ata1.00: NODEV after polling detection
Aug  1 22:18:13 ubuntu kernel: [  774.536176] ata1.00: revalidation failed (errno=-2)
Aug  1 22:18:13 ubuntu kernel: [  774.536178] ata1.00: disabled
Aug  1 22:18:13 ubuntu kernel: [  774.536204] ata1: soft resetting link
Aug  1 22:18:13 ubuntu kernel: [  774.692078] ata1: EH complete
Aug  1 22:18:13 ubuntu kernel: [  774.692101] sd 0:0:0:0: [sda] START_STOP FAILED
Aug  1 22:18:13 ubuntu kernel: [  774.692104] sd 0:0:0:0: [sda]  Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK
Aug  1 23:03:06 ubuntu kernel: [ 3468.333793] sd 2:0:0:0: [sdb] Asking for cache data failed
Aug  1 23:03:06 ubuntu kernel: [ 3468.338550] sd 2:0:0:0: [sdb] Asking for cache data failed
Aug  1 23:03:07 ubuntu kernel: [ 3468.462562] sd 2:0:0:0: [sdb] Asking for cache data failed
Aug  1 23:03:38 ubuntu kernel: [ 3500.134640] sd 0:0:0:0: [sda] Unhandled error code
Aug  1 23:03:38 ubuntu kernel: [ 3500.134645] sd 0:0:0:0: [sda]  Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK
Aug  1 23:03:38 ubuntu kernel: [ 3500.134651] sd 0:0:0:0: [sda] CDB: Read(10): 28 00 00 00 08 02 00 00 02 00
Aug  1 23:03:38 ubuntu kernel: [ 3500.134663] end_request: I/O error, dev sda, sector 2050
Aug  1 23:03:38 ubuntu kernel: [ 3500.134689] EXT4-fs (sda1): unable to read superblock
``` 

Is #21 still interesting?

---

### Post by dwashere on 2013-08-01
> **matt_symes said:**
> 
Have you checked the drives settings in the BIOS ? What are they set to ? AHCI / IDE ? Any other drive settings ?


It shows up as "IDE".  I could not see any other settings relating to the drive.

---

### Post by matt_symes on 2013-08-02
Hi

> **dwashere said:**
> It shows up as "IDE".  I could not see any other settings relating to the drive.

Can you set it to AHCI in the BIOS ? 

I have not actually looked at the drives specs, so AHCI may not be valid for the drive. That'll need checking.
 
For some reason it is running in PIO mode and not using DMA.

What BIOS do you have ?

EDIT: Have you looked at the cables ?

Kind regards

---

### Post by dwashere on 2013-08-02
> **matt_symes said:**
> Can you set it to AHCI in the BIOS ?

I do not seem to be able to set anything in the BIOS regarding the hard drive except for boot order (and maybe a password?).

> **matt_symes said:**
>  I have not actually looked at the drives specs, so AHCI may not be valid for the drive. That'll need checking.
 
It's a Samsung HM160HC.

> **matt_symes said:**
> What BIOS do you have ?

IBM BIOS Setup Utility.  It's on a T42 laptop.

> **matt_symes said:**
>  EDIT: Have you looked at the cables ?

I am guessing you are referring to the wiring inside the laptop?  The hard drive is in an easy-to-remove bay.  I checked with another T42's hard drive (same model, same specs), and that one works flawlessly, so it does not seem to be anything in the machine.  It must be the drive itself.

Any more ideas?  What do you think?  Did GParted write to the firmware?

---

### Post by sudodus on 2013-08-02
I think the HDD is serious damaged. It is hard to know exactly what happened. I have not used tools, that can save a drive from such damages. So I'm sorry, but I have no more ideas what to do.

Maybe try with ***hdparm*** which was mentioned before, to do something similar to what DBAN was supposed to do. There are more options for hdparm, many of which are considered dangerous. But if you have no other choice, think positive: dangerous = powerful. Read the manual

```
 man hdparm
```

But you cannot spend too much time trying to rescue this HDD. At some point you must give up and consider it bricked.

---

### Post by dwashere on 2013-08-02
> **sudodus said:**
> 

You can also check if the drive has ***S.M.A.R.T.*** which monitors the physical status (bad sectors). The drive is old and might not have it, but it is worth installing and checking. The drive in my T42 has ***S.M.A.R.T.***

```
sudo apt-get install smartmontools
```

```
sudo smartctl -H /dev/sda
```

See more advanced options in the manual

```
man smartctl
```

Unfortunately, I was unable to install smartools.  This is what I got:

```
ubuntu@ubuntu:~$ sudo apt-get install smartmontools
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  bsd-mailx postfix
Suggested packages:
  procmail postfix-mysql postfix-pgsql postfix-ldap postfix-pcre sasl2-bin
  dovecot-common resolvconf postfix-cdb gsmartcontrol smart-notifier
Recommended packages:
  mailx mailutils
The following NEW packages will be installed:
  bsd-mailx postfix smartmontools
0 upgraded, 3 newly installed, 0 to remove and 0 not upgraded.
Need to get 1,634 kB of archives.
After this operation, 4,698 kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Err http://archive.ubuntu.com/ubuntu/ natty/main postfix i386 2.8.2-1ubuntu1
  404  Not Found [IP: 91.189.91.15 80]
Get:1 http://archive.ubuntu.com/ubuntu/ natty/main bsd-mailx i386 8.1.2-0.20100314cvs-1 [77.7 kB]
Err http://archive.ubuntu.com/ubuntu/ natty/main smartmontools i386 5.39.1+svn3124-2
  404  Not Found [IP: 91.189.91.15 80]
Fetched 77.7 kB in 0s (110 kB/s)
Failed to fetch http://archive.ubuntu.com/ubuntu/pool/main/p/postfix/postfix_2.8.2-1ubuntu1_i386.deb  404  Not Found [IP: 91.189.91.15 80]
Failed to fetch http://archive.ubuntu.com/ubuntu/pool/main/s/smartmontools/smartmontools_5.39.1+svn3124-2_i386.deb  404  Not Found [IP: 91.189.91.15 80]
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?
```

**But**:

After I switched hard drives (same model, same specs) with another T42 (as described in my last post) in order to test this machine's inner wirings, *the faulty drive is now seen as 160GB drive and accessible!* I have no idea what happened.

[U]What did I do?
[/U]
I took the hard drive in its bay from this T42 (T42-1) to another T42 (T42-2).  I then put the faulty drive into T42-2 and the ok drive into T42-1.  I powered up both T42.  T42-1 running a live Ubuntu 11.04, checking I can properly access the non-faulty drive, T42-2 running nothing, just turned on, turn to hard drive to boot, end with blinking cursor on black screen.  Shut down.

Then I put the hard drives back into the respective T42 machines.  Power up T42-2 to check everything works fine.  Boots into XP.  Check!
Power up T42-1 to test S.M.A.R.T.  Installing smarttools does not work.  I start fiddling with system settings, happen upon Disk Utility, give it a spin (just for the heck of it) - and there it is, my (ex-??) faulty 160 GB drive, showing up as its true self.

I am now installing Ubuntu 11.04 to test things out.

I am attaching three screenshots.

What do you think?  What happened?  How does this hard drive look?  Just about dead?

_Screenshots_
[ATTACH=CONFIG]245024[/ATTACH][ATTACH=CONFIG]245025[/ATTACH][ATTACH=CONFIG]245026[/ATTACH]

---

### Post by VMC on 2013-08-02
I think it was mentioned earlier regarding the cables. Maybe one got loose or misaligned. By unplugging and re-plugging the drive, it worked. That should reflect the cables in some way.

---

### Post by sudodus on 2013-08-03
> **VMC said:**
> I think it was mentioned earlier regarding the cables. Maybe one got loose or misaligned. By unplugging and re-plugging the drive, it worked. That should reflect the cables in some way.

+1

It is hard to believe it was a software error that came and went away just like that. It is more likely that there is a bad connection somewhere (at one of the pins or somewhere inside the disk casing, the electronic part of it). I would not rely too much on that drive, so if you intend to have important stuff in it, back it up frequently!

---

### Post by dwashere on 2013-08-04
First of all - **THANK YOU VERY MUCH** to each and everyone of you helping me out.  It is great to know there is a place to turn should difficulties arise.  I am very thankful for the time and energy all of you you invested, especially *sudosus* and *matt_symes*.

\\:D/

Now to what happened to my hard drive. I hear you both - you are saying that is is pretty obvious that it was a hardware, connection problem.  Correct?  

That just does not want to make any sense to me.  It happened right as I was using GParted and the laptop was not touched at all during that time, let alone the hard drive bay, so how would a physical connection problem have occurred?  I find it very hard to imagine.

And yet, I would love to understand what happened there.  The hard drive suddenly "thinking" it is only 8GB, all those weird errors...

Any alternative, software/firmware ideas?  I know too little about how hard drives work at that level to comfortably spectulate.

By the way - Ubuntu 12.04 is now running fine on the machine using said hard drive.  I can finally test drive Unity and the HUD myself, and I am very happy about that.  Will keep in mind to backup regularly should the drive decide to die.

Thank you again, very much.  

(I would like to leave this thread open another day to see if anybody has any other explanation ideas, and then mark it as "SOLVED", if that is alright.)

---

### Post by matt_symes on 2013-08-05
Hi

> [COLOR=#000000]Now to what happened to my hard drive. I hear you both - you are saying that is is pretty obvious that it was a hardware, connection problem. Correct? [/COLOR]

I never exactly said that, but i do think it was worth checking and eliminating. 

Personally i suspect some firmware settings/issue but i don't discount any potential problem/ solution especially on a forum when i have no direct access to the hardware.

Is the drive working now and showing the full storage capacity ? If so, what did you do ?

Kind regards

---

### Post by dwashere on 2013-08-07
> I never exactly said that, but i do think it was worth checking and eliminating.

I was referring to VMC and sudosus, both of which seemed to have said something like that.

> Personally i suspect some firmware settings/issue but i don't discount  any potential problem/ solution especially on a forum when i have no  direct access to the hardware.

I would guess in the same direction (firmware), although I know too little to go much farther.  As to the potential problems/solutions - I generally agree with that.  In my case I am still wondering how unplugging and re-plugging solved my problem...     

> Is the drive working now and showing the full storage capacity ? If so, what did you do ?


Yes, it is, strangely.  This is what I did:

> [U]What did I do?
[/U]
I took the hard drive in its bay from this T42 (T42-1) to another T42  (T42-2).  I then put the faulty drive into T42-2 and the ok drive into  T42-1.  I powered up both T42.  T42-1 running a live Ubuntu 11.04,  checking I can properly access the non-faulty drive, T42-2 running  nothing, just turned on, turn to hard drive to boot, end with blinking  cursor on black screen.  Shut down.

Then I put the hard drives back into the respective T42 machines.  Power  up T42-2 to check everything works fine.  Boots into XP.  Check!
Power up T42-1 to test S.M.A.R.T.  Installing smarttools does not work.   I start fiddling with system settings, happen upon Disk Utility, give  it a spin (just for the heck of it) - and there it is, my (ex-??) faulty  160 GB drive, showing up as its true self.

What do you think?

---

### Post by sudodus on 2013-08-07
I think we'll never know for sure. I still think it is a bad connection, not a firmware error, because firmware should not be written and rewritten like that.

Another possible(?) cause might be that something was remaining in some memory (cached or something like that), and there is a bug, so that the process is depending on it (instead of resetting everything). I have had such experiences when programming simulation programs some decade ago.

But who am I to rule out what *matt_symes* is suggesting? It can certainly be a firmware settings/issue.

---

### Post by VMC on 2013-08-07
Its one of those times when you throw everything at the wall and see what sticks, and then say, Ah, that's the cause, but forgetting all the others things you did.
Troubleshooting can be a art form at times. I remember at my job having replaced a circuit board that I thought was causing the trouble, only finding out that it masked a related piece of circuity that was also defective. Wholesaling several circuit boards fixed the problem, but compounded the issue. In the end, it was determined that one board was defective, and dirt causing the second board failure.

This may be one of those times...

---

### Post by matt_symes on 2013-08-08
Hi

I'm glad it's fixed :)

If moving it to another PC fixed it, then it was most likey a dodgy connection.

Kind regards

---

### Post by dwashere on 2013-08-14
Thank you all again for your support and help!  I am happy, too, that the machine is back in business now, and I am liking Ubuntu 12.04 so much that I put it on another machine for a friend (ACER desktop M3640).  Still fighting with a Windows application that he needs to run (installing a 64bit version of Ubuntu does not seem to help using WINE...), but it's fun to feel a little bit more computing power backing Ubuntu and Unity.

It really looks like it was a connection problem, after all.  I noticed that the screw holding the bay in position was missing.  The bay fits pretty tight, so it's easy to miss that screw not being there, making it possible that the bay moves just a little tiny bit, enough to render the drive unusable in that moment.  Happened a few days ago while I had the T42 on my lap.  Suddenly it did not work anymore, and having been through all this, I pulled out the drive, re-connected it, and voila!, back to business again.

Then, as VMC suggests, who knows what else might be going on?  I can totally relate to your description.

Thank you all again!  It is great to have help!

All the best,

Joshua

---

