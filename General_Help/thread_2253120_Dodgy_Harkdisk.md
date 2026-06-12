---
title: "Dodgy Harkdisk?"
date: 2014-11-17
forum: General Help
---

### Post by nickc on 2014-11-17
Hi, I have just purchased a new 3TB hard drive (Seagate Barracuda 7200RPM) and am having some problems with it.

When I first installed it I used fdisk to create a new partition using the entire disk. I then formatted it with "mkfs.ext4 /dev/sdc1".

The format took a while (~30 mins) and throughout the disk was making a weird squeaking noise, sounded like a dog chewing a toy! I've never heard a hard drive make a noise quite like.

Once finished, I tried to mount the partition but received the following error.

```
nick@pluto:~$ sudo mount /dev/sdc1 /backup
mount: special device /dev/sdc1 does not exist
```

I then tried to fdisk again to read the partition table but now fdisk can't see the disk either.

```
nick@pluto:~$ sudo fdisk /dev/sdc
fdisk: unable to read /dev/sdc: Input/output error
```

Looking at dmesg, I can see lots of scary looking messages.

```
[  276.053440] ata3.00: status: { DRDY ERR }
[  276.053443] ata3.00: error: { ABRT }
[  276.053596] ata3.00: configured for UDMA/133 (device error ignored)
[  276.053615] sd 2:0:0:0: [sdc]  
[  276.053618] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[  276.053622] sd 2:0:0:0: [sdc]  
[  276.053624] Sense Key : Aborted Command [current] [descriptor]
[  276.053629] Descriptor sense data with sense descriptors (in hex):
[  276.053631]         72 0b 00 00 00 00 00 0c 00 0a 80 00 00 00 00 00 
[  276.053640]         00 00 00 04 
[  276.053645] sd 2:0:0:0: [sdc]  
[  276.053647] Add. Sense: No additional sense information
[  276.053650] sd 2:0:0:0: [sdc] CDB: 
[  276.053652] Read(10): 28 00 00 00 00 04 00 00 04 00
[  276.053676] ata3: EH complete
```

Right now I'm thinking the drive is a dud? Is there anything I'm missing or do I need to RMA it?

Cheers, Nick

---

### Post by oldfred on 2014-11-17
First you cannot use fdisk on drives over 2TiB.
Fdisk is for MBR(msdos) partitioning and when they designed MBR back in the 1980's they allowed 2TiB as the max. Even GB was not thought of so they had lots of room to grow.

You can use gparted, parted or gdisk. Gdisk is the fdisk for gpt drives.

 GPT Advantages (older but still valid)  see post#2 by srs5694:
[http://ubuntuforums.org/showthread.php?t=1457901](http://ubuntuforums.org/showthread.php?t=1457901)
[https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT](https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT)

      GPT fdisk Tutorial - user srs5694 in forums
[http://ubuntuforums.org/showthread.php?t=1439794](http://ubuntuforums.org/showthread.php?t=1439794)
[http://www.rodsbooks.com/gdisk/](http://www.rodsbooks.com/gdisk/)

I do not have 3TB drives but started using gpt to learn about it back with 10.10 and now all new drives & even new flash drives are gpt partitioned.

  I used gparted and selected gpt under device, advanced & select gpt over msdos(MBR) default partitioning....
    
If you are going to boot from drive, either system must be newer and you use UEFI and must have an efi partition for boot files or if BIOS then you need a bios_grub partition.

Does BIOS/UEFI show drive correctly?

---

### Post by nickc on 2014-11-17
Thanks for the reply, I was unaware I needed to use gdisk for disks >2TB - this is the first time I've used such a disk.

Unfortunately gdisk can't read it either, I just get I/O errors. 

The BIOS does recognise it.

I've been passing commands to it via hdparm but only -I seems to work, everything else gives I/O error.

---

### Post by Elfy on 2014-11-17
Moved to a support area.

---

### Post by oldrocker99 on 2014-11-17
Gparted is a **must** for any Linux user, and it works like a charm on ANY hard drive; it's great for formatting, partitioning, and resizing partitions.

---

### Post by tgalati4 on 2014-11-17
Check your BIOS for SATA options.  Try different ones.  Modern drives need newer SATA settings to work correctly.  Check for a BIOS update.  Sometimes your BIOS needs updating to work correctly with large drives.

---

### Post by matt_symes on 2014-11-17
Hi

Run a smart test on it; specifically a surface test.

If the BIOS can see it and hdparm -l returns info then the firmware can be read.

I would be worried about the sound you described when it was formatted and the I/O errors may, and I stress may, be a drive motor, actuator or surface platter problem.

```
sudo smartctl -t long /dev/sdc
```

You may have to install it first

```
sudo apt-get install smartmontools
```

It's not 100%reliable but mat give an indication.

To view the output after the test completes

```
sudo smartctl -a /dev/sdc
```

Kind regards

---

