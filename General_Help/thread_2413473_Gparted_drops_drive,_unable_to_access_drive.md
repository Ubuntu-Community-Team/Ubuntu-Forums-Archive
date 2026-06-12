---
title: "Gparted drops drive, unable to access drive"
date: 2019-02-26
forum: General Help
---

### Post by Randy_Bass on 2019-02-26
I have an older computer with legacy BIOS, with several linux distros (My primary choice is Ubuntu 18.04, with Xfce DE). I also have Windows 10 installed. I recently lost a 2 TB hard drive, and am trying to replace it with a 4 TB GPT drive. I also have a 180 GB SSD and 360 GB HD. 

This is my first time working with GPT, and I thought no big whup. I wanted to put the Windows 10 at the beginning of the 4TB drive... let me cut it short and say Windows won't allow me to combine legacy BIOS with GPT. Then I thought I would move a few Linux distros from my SSD to the 4 TB drive, and move the Windows to the (MBR) SSD. Sorry about all the Windows talk, the problem is really with Linux.

First step is to create new ext4 partitions on the 4 TB drive. In GParted it shows the 4 TB drive as SDC. I create a few partitions, and when I click on "apply all operations," I get an error message 
> Could not stat device /dev/sdc.
GParted reloads drive info, and now /dev/sdc is not showing at all. I can go to a terminal window and issue the command
```
sudo lsblk
```
and /dev/sdc does not list, whereas it did before. Similarly with the command
```
sudo fdisk -l
```
I can also give the command 
```
ls /dev
```
And it shows all the other partitions (along with everything else), but no sdc.

I could reboot, and /dev/sdc is visible again. I used gparted to delete the 2 Windows system partitions, as there was a warning that they were not on proper boundaries, and gparted was able to complete that just fine. But then I tried to create new ext4 partitions, and got the same behavior of the error message and the drive no longer being visible. 

Is there a problem using GParted with a GPT drive, or am I doing something wrong?

______________________________________________________________
UPDATE:

I booted fresh into Ubuntu, opened GParted, and deleted all the existing partitions on the 4 TB drive. Then I recreated the GPT table. Then I added 7 primary linux partitions (ext4, swap, lvm2). I clicked on "Apply all operations" and it completed the first 4, then choked on the 5th one, issuing two messages:
> Error fsyncing/closing /dev/sdc

Error initializing scsi device /dev/sdc      No such device

After which Gparted rescanned, and /dev/sdc is not available. As before, /dev/sdc is not displayed when I issue the command:

```
sudo lsblk
```

I haven't rebooted yet, but suspect /dev/sdc will be back, perhaps with the first 4 partitions created. I find it ironic that it choked on the 5th one, as I would expect with an MBR drive, which can only handle 4 primary partitions. I wouldn't think I would need to create an extended partition with logical partitions inside with a GPT drive.

_______________________________________________________________
UPDATE 2:

I rebooted, reopened GParted, deleted the 5th (corrupted ?) partition. I got the error message again:

> Could not stat device /dev/sdc - No such file or directory

Again, /dev/sdc is not showing. I rebooted, used parted at the command line to delete partition /dev/sdc5, and that worked okay. I entered GParted, recreated partition 5 (8 GB swap). That worked okay. One at a time, I created the partitions
/dev/sdc6 60 GB lvm2
/dev/sdc7 1000 GB lvm2
on the last one, it issued the same error statement as before. Perhaps I have a corrupted installation of GParted? I issued the commands

```
sudo apt-get remove gparted
```

and

```
sudo apt-get install gparted
```

then rebooted again.
I again entered GParted, deleted the last 1000 GB lvm partition, and recreated it. That went okay. I then created a 1000 GB ext4 partition. That went okay. Then I got cocky, I created three partitions, a 50 GB ntfs, a 50 GB FAT32, and a 1000 GB ntfs. I selected Apply, and got the following message:
> Input/Output error. End of file while reading /dev/sdc

Then another error message

> Partition(s) 1, 2, 3, 4, 5, 6, 7, 8, 9 have been written, but we have been unable to inform the kernel of the change, probably because it/they are in use. As a result, the old partitions will remain in use. You should reboot now before making further changes.

I like verbosity. I guess that means it made the changes, but the kernel doesn't know about it and can't access them.

Then I got the standard message

> Error fsyncing/closing /dev/sdc: input/output error

So can I only add 1 partition at a time? Is that the problem? 

I rebooted, and tried creating the 50 GB ntfs partition. It crashed again. So much for that theory. I rebooted, and the new partition was ok. I tried creating a 50 GB FAT32. It crashed again.   

Hmmm.... I'm starting to feel like the definition of an idiot. I don't understand why GParted is having so much trouble.

__________________________________________________________
UPDATE 3

I thought maybe the problem is with GParted. I went into parted, and created a 50 GB fat32 and 1000 GB ntfs partition, the last two partitions I want on this drive. That leaves me about 256 GB of unformatted space. I opened up GParted again, just for yucks, and it said those last two partitions I just created were of unknown file type. Hmmm.... I closed GParted, went back into parted, and checked the alignment (opt) of all 11 partitions, and they all checked out okay.
I reran glist -l /dev/sdc with the following output:

> sudo gdisk -l /dev/sdcGPT fdisk (gdisk) version 1.0.3


Partition table scan:
  MBR: protective
  BSD: not present
  APM: not present
  GPT: present


Found valid GPT with protective MBR; using GPT.
Disk /dev/sdc: 7814037168 sectors, 3.6 TiB
Model: WDC WD4005FZBX-0
Sector size (logical/physical): 512/4096 bytes
Disk identifier (GUID): 66623392-DE6E-4253-ABE7-6230ABAB2A2B
Partition table holds up to 128 entries
Main partition table begins at sector 2 and ends at sector 33
First usable sector is 34, last usable sector is 7814037134
Partitions will be aligned on 2048-sector boundaries
Total free space is 1317944941 sectors (628.4 GiB)


Number  Start (sector)    End (sector)  Size       Code  Name
   1            2048         2050047   1000.0 MiB  8300  Boot_1
   2         2050048         4098047   1000.0 MiB  8300  Boot_2
   3         4098048         6146047   1000.0 MiB  8300  Boot_3
   4         6146048         8194047   1000.0 MiB  8300  Boot_4
   5         8194048        24578047   7.8 GiB     8200  linux_swap_hdd4
   6        24578048       147458047   58.6 GiB    8E00  lvm_hdd41
   7       147458048      2195458047   976.6 GiB   8E00  lvm_data_hdd4
   8      2195458048      4243458047   976.6 GiB   8300  backup_hdd4
   9      4243458048      4345858047   48.8 GiB    0700  win_data_hdd4
  10      4345858048      4449218559   49.3 GiB    0700  win_fat_hdd4
  11      4449218560      6496094207   976.0 GiB   0700  win_backup

It looks like everything is okay. So why did Gparted have trouble with it?

Acting on the premise that everything is okay (:O), I opened KVPM and created a new physical volume and volume group on sdc7. Then I started to add some logical volumes to the volume group. When I created the 4th logical volume, I got the error message

> Error fsyncing/closing /dev/sdc: input/output error

Again, the drive is invisible. So it's not just GParted that is having trouble with this.

I rebooted into Windows 10. The last two partitions (sdc10, sdc11) existed and were the correct size, but were listed as unformatted. I was able to format them both as ntfs. I copied data to sdc9 (win_data_hdd4) with no problems, and was able to access the data after copying it. 

So it appear that I had problems with parted, GParted, and KVPM, all of which modified the disk structure. I can't believe it's an Ubuntu/GPT issue, because people have been using it for years with both legacy BIOS and UEFI, even though this is my first time. I'm beginning to wonder if I have a defective hard drive. What else could it be?

---

### Post by yancek on 2019-02-26
> Windows won't allow me to combine legacy BIOS with GPT.

That's correct but you can combine BIOS with GPT using a Linux system.  It isn't really clear to me whether you installed windows 10 to the new 4TB drive, did you?  Did you use EFI/GPT or do a Legacy install of windows 10?  If you have not data on the 4TB drive, you might try selecting the Device tab and creating a new partition table on sdc.  Make sure you have the correct drive as this will eliminate all data on the drive. GParted is capable of working with GPT drives.

---

### Post by oldfred on 2019-02-26
You have to first set drive to gpt using gparted or any of the other tools.
Gparted should be defaulting to gpt since over 2TiB.
Did Windows try to make drive MBR and then only 2TiB. So now correct partition tools are having issues?
Post this:
sudo parted -l
sudo gdisk -l /dev/sdc (if still sdc)

If at some time in near future drive may be used with a newer UEFI system, it pays to add the ESP - efi system partition at beginning of drive now. And for BIOS boot you need a 1 or 2MB unformatted bios_grub partition for grub to correctly install in BIOS mode.

---

### Post by Randy_Bass on 2019-02-26
Thank you, Yancek. I started in Windows 10 by initializing the device as GPT. Then I cloned the Windows system partitions to it, and created some additional NTFS partitions. I shut down, unplugged the old driven and tried booting to the new drive, which didn't work. It took the better part of the day to determine that I had legacy BIOS and that Windows won't work with that on the GPT drive. There was a workaround to build a small boot partition for Windows on a MBR drive and keep the Windows system on the GPT drive, which I was going to try, but then got the idea of just putting Windows on the MBR SSD and move stuff from the SSD to the GPT drive. Then I rebooted into Ubuntu to add some ext4 partitions to the GPT drive, which is where I ran into trouble. See my update in the original post for what I did this morning.

OldFred, Thank you for your response. I will take your advice about adding the [COLOR=#000000]ESP - efi system partition.[/COLOR] I want to have the option to move this to an UEFI computer in the future. See my update on the original post for what I did this morning. After that, with /dev/sdc not visible again, here are the outputs of the commands you requested:

```
sudo parted -lModel: ATA ST3360320AS (scsi)
Disk /dev/sda: 360GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos
Disk Flags: 


Number  Start   End     Size    Type      File system  Flags
 1      32.3kB  123MB   123MB   primary   ntfs         boot
 2      123MB   48.0GB  47.9GB  primary   ntfs
 3      48.0GB  95.2GB  47.2GB  primary   ntfs
 4      95.2GB  360GB   265GB   extended
 5      95.2GB  96.3GB  1049MB  logical   ext4
 6      96.3GB  149GB   52.4GB  logical                lvm
 7      149GB   360GB   211GB   logical                lvm




Model: ATA INTEL SSDSC2BW18 (scsi)
Disk /dev/sdb: 180GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos
Disk Flags: 


Number  Start   End     Size    Type      File system     Flags
 3      1049kB  1050MB  1049MB  primary   ext4
 1      1050MB  103GB   102GB   primary                   lvm
 4      103GB   180GB   77.3GB  extended                  lba
 5      103GB   115GB   12.0GB  logical   ext4
 6      115GB   121GB   6291MB  logical   ext4
 8      121GB   122GB   1049MB  logical   ext4
 9      122GB   123GB   1049MB  logical   ext4
10      123GB   124GB   1049MB  logical   fat32           boot
 7      124GB   133GB   8389MB  logical   ext3
11      133GB   134GB   1049MB  logical   ext4
12      134GB   136GB   2097MB  logical   linux-swap(v1)
13      136GB   180GB   44.3GB  logical                   lvm




Model: WD Elements 25A3 (scsi)
Disk /dev/sdd: 5001GB
Sector size (logical/physical): 512B/4096B
Partition Table: gpt
Disk Flags: 


Number  Start   End     Size    File system  Name           Flags
 1      1049kB  105GB   105GB   ext4         ext5tb_lvm
 2      105GB   3775GB  3670GB  ext4         ext5tb_backup
 3      3775GB  5001GB  1226GB  ntfs         ext5tb_ntfs    msftdata




Model: Linux device-mapper (linear) (dm)
Disk /dev/mapper/vg_ssd1-ubu_root_ssd1: 16.1GB
Sector size (logical/physical): 512B/512B
Partition Table: loop
Disk Flags: 


Number  Start  End     Size    File system  Flags
 1      0.00B  16.1GB  16.1GB  ext4




Model: Linux device-mapper (linear) (dm)
Disk /dev/mapper/vg_ssd1-swap_ssd1: 8590MB
Sector size (logical/physical): 512B/512B
Partition Table: loop
Disk Flags: 


Number  Start  End     Size    File system     Flags
 1      0.00B  8590MB  8590MB  linux-swap(v1)




Model: Linux device-mapper (linear) (dm)
Disk /dev/mapper/vg_ssd1-centos_home_ssd1: 21.5GB
Sector size (logical/physical): 512B/512B
Partition Table: loop
Disk Flags: 


Number  Start  End     Size    File system  Flags
 1      0.00B  21.5GB  21.5GB  ext4




Model: Linux device-mapper (linear) (dm)
Disk /dev/mapper/vg_ssd1-centos_root_ssd1: 16.1GB
Sector size (logical/physical): 512B/512B
Partition Table: loop
Disk Flags: 


Number  Start  End     Size    File system  Flags
 1      0.00B  16.1GB  16.1GB  ext4




Model: Linux device-mapper (linear) (dm)
Disk /dev/mapper/vg_ssd1-ubu_home_ssd1: 21.5GB
Sector size (logical/physical): 512B/512B
Partition Table: loop
Disk Flags: 


Number  Start  End     Size    File system  Flags
 1      0.00B  21.5GB  21.5GB  ext4




Model: Linux device-mapper (linear) (dm)
Disk /dev/mapper/vg_ubu-h4_ubu_home: 16.1GB
Sector size (logical/physical): 512B/512B
Partition Table: loop
Disk Flags: 


Number  Start  End     Size    File system  Flags
 1      0.00B  16.1GB  16.1GB  ext4




Model: Linux device-mapper (linear) (dm)
Disk /dev/mapper/vg_ubu-h4_ubu_swap: 8590MB
Sector size (logical/physical): 512B/512B
Partition Table: loop
Disk Flags: 


Number  Start  End     Size    File system     Flags
 1      0.00B  8590MB  8590MB  linux-swap(v1)




Model: Linux device-mapper (linear) (dm)
Disk /dev/mapper/vg_ubu-h4_ubu_root: 16.1GB
Sector size (logical/physical): 512B/512B
Partition Table: loop
Disk Flags: 


Number  Start  End     Size    File system  Flags
 1      0.00B  16.1GB  16.1GB  ext4




Model: Linux device-mapper (linear) (dm)
Disk /dev/mapper/vg_ssd2-ubu_home_ssd2: 21.5GB
Sector size (logical/physical): 512B/512B
Partition Table: loop
Disk Flags: 


Number  Start  End     Size    File system  Flags
 1      0.00B  21.5GB  21.5GB  ext4




Model: Linux device-mapper (linear) (dm)
Disk /dev/mapper/vg_ubu-h4_ubu_home2: 5369MB
Sector size (logical/physical): 512B/512B
Partition Table: loop
Disk Flags: 


Number  Start  End     Size    File system  Flags
 1      0.00B  5369MB  5369MB  ext4




Model: Linux device-mapper (linear) (dm)
Disk /dev/mapper/vg_ssd2-ubu_root_ssd2: 21.5GB
Sector size (logical/physical): 512B/512B
Partition Table: loop
Disk Flags: 


Number  Start  End     Size    File system  Flags
 1      0.00B  21.5GB  21.5GB  ext4
```   



```
sudo gdisk -l /dev/sdc
GPT fdisk (gdisk) version 1.0.3


Problem opening /dev/sdc for reading! Error is 2.
The specified file does not exist!
```

OldFred, okay, I rebooted, and issued the gdisk command again. Here are the results:

```
sudo gdisk -l /dev/sdcGPT fdisk (gdisk) version 1.0.3


Partition table scan:
  MBR: protective
  BSD: not present
  APM: not present
  GPT: present


Found valid GPT with protective MBR; using GPT.
Disk /dev/sdc: 7814037168 sectors, 3.6 TiB
Model: WDC WD4005FZBX-0
Sector size (logical/physical): 512/4096 bytes
Disk identifier (GUID): 66623392-DE6E-4253-ABE7-6230ABAB2A2B
Partition table holds up to 128 entries
Main partition table begins at sector 2 and ends at sector 33
First usable sector is 34, last usable sector is 7814037134
Partitions will be aligned on 2048-sector boundaries
Total free space is 7789461101 sectors (3.6 TiB)


Number  Start (sector)    End (sector)  Size       Code  Name
   1            2048         2050047   1000.0 MiB  8300  Boot_1
   2         2050048         4098047   1000.0 MiB  8300  Boot_2
   3         4098048         6146047   1000.0 MiB  8300  Boot_3
   4         6146048         8194047   1000.0 MiB  8300  Boot_4
   5         8194048        24578047   7.8 GiB     8300
```

---

### Post by oldfred on 2019-02-26
Your partition 5 is larger than you drive??

       Disk /dev/sdc: 7814037168 sectors, 3.6 TiB
5 8194048 24578047 7.8 GiB 8300  

See if gdisk will update partition tables.
      
 GPT fdisk Tutorial 
[http://www.rodsbooks.com/gdisk/walkthrough.html](http://www.rodsbooks.com/gdisk/walkthrough.html)
[URL="http://www.rodsbooks.com/gdisk/"]http://www.rodsbooks.com/gdisk/
      [/URL]
 repair gpt:
[http://www.rodsbooks.com/gdisk/repairing.html](http://www.rodsbooks.com/gdisk/repairing.html)
More repair info  use p, v & w to write the partition table. If not correct just use q to quit. : 
If any error messages post those.

    [URL="http://www.rodsbooks.com/gdisk/"]
[/URL]

---

### Post by Randy_Bass on 2019-02-26
OldFred,
Actually, partition 5 is only 7.8 GiB in size. The first two numbers are the start and end sectors.
Oops, I forgot to put the UEFI stuff first. Now looks like I'll have to rebuild it. I'll read through the tutorials and get back on this.

---

### Post by oldfred on 2019-02-26
Sorry, mis-read GB & TB.

I like to add ESP & bios_grub as first two partitions on every new or reformatted drive including larger flash drives. Smaller drives like my flash drives I typically use a smaller ESP, but larger drives will use a larger ESP for potential other boot or configurations. I like to save my UEFI updates and some internal screen shots from UEFI and they can only go into a FAT32 partitioned drive. So some extra is worth having.

Partitions still similar to this, but versions have been updated.
[https://ubuntuforums.org/showthread.php?t=2305833&p=13404413#post13404413](https://ubuntuforums.org/showthread.php?t=2305833&p=13404413#post13404413)

My drives still are not fully partitioned, as I may add more test installs or expand data partitions.

---

### Post by Randy_Bass on 2019-02-27
See my UPDATE 3 in my original entry above

---

### Post by oldfred on 2019-02-27
Was drive ever RAID? That can leave meta-data on drive that has to be removed.
But it seems it is something your Windows install did. Windows in BIOS mode & then MBR can cause issues on gpt drives.

       Even if raid not used BIOS may have set parameters, Also check BIOS settings should be AHCI
sudo dmraid -E -r /dev/sdc

Did you run the gdisk re-write/update of partition table? Post #5?

---

### Post by Randy_Bass on 2019-02-27
OldFred, No, drive was never raid. I had to install dmraid. Well, now the drive is not visible immediately on boot. I ran dmesg to see what it said, but I don't understand what to do about it. The results pertaining to /dev/sdc are here:
```
[   23.483544] sd 1:0:1:0: [sdc] tag#0 FAILED Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE[   23.483547] sd 1:0:1:0: [sdc] tag#0 Sense Key : Aborted Command [current] 
[   23.483551] sd 1:0:1:0: [sdc] tag#0 Add. Sense: Internal target failure
[   23.483554] sd 1:0:1:0: [sdc] tag#0 CDB: Read(16) 88 00 00 00 00 00 00 7d 04 00 00 00 02 00 00 00
[   23.483556] print_req_error: I/O error, dev sdc, sector 8193024
[   23.483637] sd 1:0:1:0: rejecting I/O to offline device
[   23.483692] sd 1:0:1:0: killing request
[   23.483695] sd 1:0:1:0: rejecting I/O to offline device
[   23.483749] sd 1:0:1:0: [sdc] killing request
[   23.483754] ata2: EH complete
[   23.483764] sd 1:0:1:0: [sdc] FAILED Result: hostbyte=DID_NO_CONNECT driverbyte=DRIVER_OK
[   23.483766] sd 1:0:1:0: [sdc] CDB: Read(16) 88 00 00 00 00 01 83 32 87 80 00 00 00 08 00 00
[   23.483768] print_req_error: I/O error, dev sdc, sector 6496094080
[   23.483837] sd 1:0:1:0: rejecting I/O to offline device
[   23.483904] ata2.01: detaching (SCSI 1:0:1:0)
[   23.484871] sd 1:0:1:0: [sdc] Synchronizing SCSI cache
[   23.484898] sd 1:0:1:0: [sdc] Synchronize Cache(10) failed: Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK
[   23.484899] sd 1:0:1:0: [sdc] Stopping disk
[   23.484908] sd 1:0:1:0: [sdc] Start/Stop Unit failed: Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK
[   23.484933] scsi 1:0:1:0: rejecting I/O to dead device
[   23.484996] scsi 1:0:1:0: rejecting I/O to dead device
[   23.485056] scsi 1:0:1:0: rejecting I/O to dead device
[   23.485058] blk_partition_remap: fail for partition 2
[   23.485060] Buffer I/O error on dev sdc2, logical block 255967, async page read
[   23.485133] blk_partition_remap: fail for partition 1
[   23.485136] Buffer I/O error on dev sdc1, logical block 255998, async page read
[   23.485261] scsi 1:0:1:0: rejecting I/O to dead device
[   23.485265] blk_partition_remap: fail for partition 3
[   23.485267] Buffer I/O error on dev sdc3, logical block 3, async page read
[   23.485381] scsi 1:0:1:0: rejecting I/O to dead device
[   23.485442] scsi 1:0:1:0: rejecting I/O to dead device
[   23.485502] scsi 1:0:1:0: rejecting I/O to dead device
[   23.485547] blk_partition_remap: fail for partition 6
[   23.485549] Buffer I/O error on dev sdc6, logical block 15359984, async page read
[   23.485635] scsi 1:0:1:0: rejecting I/O to dead device
[   23.485696] scsi 1:0:1:0: rejecting I/O to dead device
[   23.485708] blk_partition_remap: fail for partition 8
[   23.485709] Buffer I/O error on dev sdc8, logical block 255999984, async page read
[   23.485736] blk_partition_remap: fail for partition 5
[   23.485738] Buffer I/O error on dev sdc5, logical block 2047984, async page read
[   23.485902] scsi 1:0:1:0: rejecting I/O to dead device
[   23.485972] blk_partition_remap: fail for partition 7
[   23.485974] Buffer I/O error on dev sdc7, logical block 255999984, async page read
[   23.486084] blk_partition_remap: fail for partition 10
[   23.486087] Buffer I/O error on dev sdc10, logical block 12920048, async page read
[   23.486285] blk_partition_remap: fail for partition 9
[   23.486287] Buffer I/O error on dev sdc9, logical block 12799984, async page read

```

---

### Post by oldfred on 2019-02-27
How are you connecting drive?

We have seen multiple users trying to use older USB cases or cables that just do not work with drives over 2TiB.
And some that do not have enough power from USB port.
I have an adapter cable that works fine with my very old SSD from 2011, but would not even see my HDD. Some have separate power and those will typically work with HDDs. But Some older ones just do not work.

---

### Post by Randy_Bass on 2019-02-28
I called Western Digital tech support. I explained the problem, to which the immediate reply was, "We don't support Linux." Yeah, yeah, yeah. I explained my problem was that I created some partitions in Windows, but Windows doesn't support GPT with Legacy BIOS. He went away for a few minutes, I presume to ask someone what I meant by legacy BIOS. He came back and told me to install UEFI on my computer. Well, no, I can't do that either. I asked him how could I wipe the disk clean in Windows so I could start over with a factory fresh drive. He did point out where I could find instructions to do that. My thinking is that with a wiped drive, I could reboot into Ubuntu and create a good GPT there. Piece of cake... not. Now Ubuntu wouldn't boot and drops into emergency mode. I went back to Windows and created a GPT, and tried booting into Ubuntu - same diff. I booted into Vector Slackware Linux, and it booted okay, but when I entered parted, it didn't see the sdc drive.

Well, the whole day was wasted. Tomorrow, I'm going to go back into Windows and wipe it again and put an MBR on it. That should allow me to boot into Ubuntu, where I'll change it to GPT, and then I'll be off and running. If that fails, I'll return the disk, and stick to 2 TB maximum drives with MBR as long as I'm working with a legacy BIOS machine.

---

### Post by Randy_Bass on 2019-03-02
Sorry to take so long to respond since my last update. I booted into Windows and put an MBR partition table on the 4TB drive, such that only 2.2 TB was visible. I thought everything would be fine then, but such was not the case. I booted back into Ubuntu, and it again dropped down to emergency mode, and still had no visibility of sdc. I rebooted into Vector Slackware Linux, and it at least booted up, although it still had no visibility of the sdc hard drive. So I booted back to Windows, converted the 4 TB drive back to GPT, made two partitiond of 2 TB each (it wouldn't reach beyond a 2 TB Partition). Then I went into diskpart, and issued a clean all command, which writes zeros to the entire drive. This took a day and a half to accomplish. I took the 4 TB drive back and exchanged it for a 2 TB drive, which can have an MBR partition file and Windows can handle it alongside Linux (this is on my legacy BIOS computer). 

So now I'm back again with the new 2 TB drive installed on /dev/sdc. I booted into Ubuntu first off, and it still drops me down to emergency mode. I don't know what the issue is with that. I went through dmesg and nothing stood out. Maybe upgrading my BIOS got something confused. I don't know. I rebooted into Vector Slackware Linux, and it came up fine, and I have visibility to the as-yet unpartitioned 2 TB drive on /dev/sdc. Well, if worse comes to worst, I have my Ubuntu backed up from a few days before this whole debacle started, so I can restore it if I'm not able to fix it. That and also to restore what I had on my original 2 TB drive that failed.

Bottom line, if you want a dual-or-multi-boot system with Linux and Windows and are running on a legacy BIOS computer, stick to drives that are 2 TB or less in size.

@Oldfred and @YanceK, thnk you so much for your assistance.

---

### Post by oldos2er on 2019-03-03
Moved to General Help.

---

### Post by Randy_Bass on 2019-03-03
@oldfred, All of my internal drives are SATA power and SATA 2 data. The external 5TB drive is USB, and I have no problem accessing that in Ubuntu. I did have a partition on the 5TB external formatted as NTFS to be used as backup for my Windows, but Windows was unable to access it --- now I know why. I did return the 4 TB I was having problems with and got a new 2 TB drive, and am trying to convert that from GPT to MBR, and partition and format it, but I am having the same problem of Ubuntu not recognizing it, although I am able to boot into Ubuntu okay, so at least it's not dropping me down to emergency mode.

I just issued the command 

```
journalctl -xb
```

And got the (partial) output:

> ata2.01: exception Emask 0x10 SAct 0x0 SErr 0x280100 action 0x0ata2.01: SError: { UnrecovData 10B8B BadCRC }
ata2.01: failed command: READ DMA EXT
ata2.01: cmd 25/00:80:80:00:00/00:01:00:00:00/f0 tag 0 dma 196608 in
                                res 51/84:2f:cf:00:00/84:01:00:00:00/f0 Emask 0x30 (host bus error)
ata2.01: status: { DRDY ERR }
ata2.01: error: { ICRC ABRT }

I'm not having much luck at all with this.

---

### Post by oldfred on 2019-03-03
I do not have any large drives, but converted to only using gpt back in 2011, for all new or reformatted drives including larger flash drives.
And have not noticed any issues.

From a Windows drive, you can read data on a gpt drive with any Windows newer than XP. XP did not work with gpt at all.
But Windows boot drive must be MBR for BIOS and gpt for UEFI.

---

### Post by Randy_Bass on 2019-03-11
@oldfred, well, I could see my 5TB external drive in Windows 10, but for some reason it could not access the NTFS backup partition I created on it, so I never backed up Windows to that drive, only to the drive it was on (which was failing). I was able to use Clonezilla and image it to the new drive before the failing drive went down completely, and was able to install it on my new 2 TB drive, so all is good there - mental note: to read and write with both Linux and Windows, a FAT32 partition is needed, but file size is limited to 4 GB, not enough for a system image file. 

Unfortunately, somehow (I blame it on the failing drive), all of my Linux operating systems (count 6) became corrupted and none of them could boot. What happened was the partition tables on all of my old drives became corrupted. I had to install a new 16.04 Ubuntu from a live CD to the new 2TB drive. I had not backed the MBRs or partition tables up in a while, so what I had was obsolete, and I made a note to include MBR and partition table and LVM metadata as part of my regular weekly backups. Luckily, LVM creates metadata backups every time I modify the volume, which included my weekly snapshots to do weekly backups, so I was able to access those from my backups. I was able to repair the partition tables from lsblk printouts I had done. I tried to reinstall my old 18.04 Ubuntu from a backup image, but fsarchiver changed with the 18.04 release, so it would not restore from the new 16.04 Ubuntu version that I just installed. So I had to download and install Ubuntu 18.04 and download the latest fsarchiver to do the restore. This has all taken me a few weeks, and all is not totally well with my old disks yet, but at least I have my old Ubuntu 18.04 up and running the way I like it, and my Windows 10 is safe with a backup image on the external drive. Quite the learning experience.

---

