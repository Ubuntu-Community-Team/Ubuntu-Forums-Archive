---
title: "rEFIt - Triple Boot - Windows Boot Manager - Failed To Start"
date: 2012-12-30
forum: General Help
---

### Post by wulgulmerang on 2012-12-30
Dear Community, 

I have just installed Ubuntu 12.10 alongside Snow Leopard and Windows 7.

I created 2 partitions:

(1) Ubuntu / partition ~40GB
(2) Linux Swap partition ~4.5GB

I configured the boot loader to be installed on (1) which was /dev/sda3

When I rebooted into rEFIt and selected the Windows Icon, Windows 7 failed to boot.  

When I selected the Windows 7 Loader on /dev/sda5 from within the Ubuntu Boot Loader, I got a Windows Boot Manager message saying that I would need to "Repair Your Computer".

I don't particularly want to try this as I may damage something else.

Here is the output from rEFIt's Partition Inspector.

Are there commands I can run from within Snow Leopard or Ubuntu 12.10 to fix this issue?

Warm Regards,
Dave.;)

```
*** Report for internal hard disk ***

Current GPT partition table:
 #      Start LBA      End LBA  Type
 1             40       409639  EFI System (FAT)
 2         409640    337953775  Mac OS X HFS+
[/LIST][LIST=1]
 3      338216960    417673215  Basic Data
 4      417673216    426459135  Linux Swap
 5      428406784    625141759  Basic Data

Current MBR partition table:
 # A    Start LBA      End LBA  Type
 1              1       409639  ee  EFI Protective
 2         409640    337953775  af  Mac OS X HFS+
 3 *    338216960    417673215  83  Linux
 4      417673216    426459135  82  Linux swap / Solaris

MBR contents:
 Boot Code: Unknown, but bootable

Partition at LBA 40:
 Boot Code: None (Non-system disk message)
 File System: FAT32
 Listed in GPT as partition 1, type EFI System (FAT)

Partition at LBA 409640:
 Boot Code: None
 File System: HFS Extended (HFS+)
 Listed in GPT as partition 2, type Mac OS X HFS+
 Listed in MBR as partition 2, type af  Mac OS X HFS+

Partition at LBA 338216960:
 Boot Code: GRUB
 File System: ext4
 Listed in GPT as partition 3, type Basic Data
 Listed in MBR as partition 3, type 83  Linux, active

Partition at LBA 417673216:
 Boot Code: None
 File System: Unknown
 Listed in GPT as partition 4, type Linux Swap
 Listed in MBR as partition 4, type 82  Linux swap / Solaris

Partition at LBA 428406784:
 Boot Code: Unknown, but bootable
 File System: NTFS
 Listed in GPT as partition 5, type Basic Data

```

---

### Post by mkeedlinger on 2012-12-30
I recently quad-booted my computer and I'm pretty sure the reason that you're having trouble is that Windows stores part of its boot manager in the MBR (Master Boot Record) and rEFIT overwrites the master boot record and it may not have support for finding Windows OSs by default. Consider using GRUB, it has a lot of documentation.

---

### Post by wulgulmerang on 2012-12-30
Thanks for the info, however, rEFIt was booting both Snow Leopard and Windows 7 correctly, before I installed Ubuntu 12.10 alongside (with the Ubuntu Boot Loader installed onto the / Ubuntu partition)

It would be nice to know why rEFIt now only works with Snow Leopard and Ubuntu 12.10 and why the Windows 7 Loader stopped functioning.

If there's a way to correct the issue from Terminal then that would be great.

I have quite a few useful applications on Windows 7 which I'd like to have access to. ;-)

---

### Post by wulgulmerang on 2012-12-31
From what I've read so far, it's looking like I've pushed the WINDOWS 7 partition out of the Master Boot Record (MBR), by creating 2 partitions "UBUNTU /" and "LINUX SWAP", in between the pre-existing partitions of MAC and WINDOWS 7.

Before: [hidden EFI], MAC, WINDOWS 7
After: [hidden EFI], MAC, UBUNTU /, LINUX SWAP, WINDOWS 7 (GPT can handle more than 4 primary partitions)

However, the Master Boot Record (MBR) can only store up to 4 primary partitions (3 primary and 1 extended primary containing up to 12 more logical partitions).

```
Current MBR partition table:
 # A    Start LBA      End LBA  Type
 1              1       409639  ee  EFI Protective
 2         409640    337953775  af  Mac OS X HFS+
 3 *    338216960    417673215  83  Linux
 4      417673216    426459135  82  Linux swap / Solaris
``` 

Note to self, I wonder if there's a way of using logical partitions to Triple Boot.

I have found an article that describes a solution to the problem of having the WINDOWS 7 partition pushed out of the Master Boot Record, so shall report back on how it all turns out.):P
[https://discussions.apple.com/thread/4144252?start=0&tstart=0](https://discussions.apple.com/thread/4144252?start=0&tstart=0)

```
sudo gpt -r -vv show disk0

gpt show: disk0: mediasize=320072933376; sectorsize=512; blocks=625142448
gpt show: disk0: Suspicious MBR at sector 0
gpt show: disk0: Pri GPT at sector 1
gpt show: disk0: Sec GPT at sector 625142447
      start       size  index  contents
          0          1         MBR
          1          1         Pri GPT header
          2         32         Pri GPT table
         34          6         
         40     409600      1  GPT part - C12A7328-F81F-11D2-BA4B-00A0C93EC93B
     409640  337544136      2  GPT part - 48465300-0000-11AA-AA11-00306543ECAC
  337953776     263184         
  338216960   79456256      3  GPT part - EBD0A0A2-B9E5-4433-87C0-68B6B72699C7
  417673216    8785920      4  GPT part - 0657FD6D-A4AB-43C4-84E5-0933C84B4F4F
  426459136    1947648         
  428406784  196734976      5  GPT part - EBD0A0A2-B9E5-4433-87C0-68B6B72699C7
  625141760        655         
  625142415         32         Sec GPT table
  625142447          1         Sec GPT header

sudo fdisk /dev/disk0
Disk: /dev/disk0	geometry: 38913/255/63 [625142448 sectors]
Signature: 0xAA55
         Starting       Ending
 #: id  cyl  hd sec -  cyl  hd sec [     start -       size]
------------------------------------------------------------------------
 1: EE    0   0   1 - 1023 254  63 [         1 -     409639] <Unknown ID>
 2: AF 1023 254  63 - 1023 254  63 [    409640 -  337544136] HFS+        
*3: 83 1023 254  63 - 1023 254  63 [ 338216960 -   79456256] Linux files*
 4: 82 1023 254  63 - 1023 254  63 [ 417673216 -    8785920] Linux swap

```

---

### Post by wulgulmerang on 2012-12-31
In an interesting twist of events, I now have access to Windows 7 through rEFIt.

However, the rEFIt Penguin, is now booting into Windows 7, and I'm no longer seeing the GRUB loader.

This is the output from partition inspector.  The Master Boot Record has been reduced to an EFI partition and a hybrid MBR partition.

Not sure what's happening or how to get rEFIt working with Ubuntu again (whilst keeping WINDOWS 7 on GPT (5) still booting). 

```
*** Report for internal hard disk ***

Current GPT partition table:
 #      Start LBA      End LBA  Type
 1             40       409639  EFI System (FAT)
 2         409640    337953775  Mac OS X HFS+
 3      338216960    417673215  Basic Data
 4      417673216    426459135  Linux Swap
 5      428406784    625141759  Basic Data

Current MBR partition table:
 # A    Start LBA      End LBA  Type
 1              1    428406783  ee  EFI Protective
 2 *    428406784    625141759  07  NTFS/HPFS

MBR contents:
 Boot Code: Unknown, but bootable

Partition at LBA 40:
 Boot Code: None (Non-system disk message)
 File System: FAT32
 Listed in GPT as partition 1, type EFI System (FAT)

Partition at LBA 409640:
 Boot Code: None
 File System: HFS Extended (HFS+)
 Listed in GPT as partition 2, type Mac OS X HFS+

Partition at LBA 338216960:
 Boot Code: GRUB
 File System: ext4
 Listed in GPT as partition 3, type Basic Data

Partition at LBA 417673216:
 Boot Code: None
 File System: Unknown
 Listed in GPT as partition 4, type Linux Swap

Partition at LBA 428406784:
 Boot Code: Unknown, but bootable
 File System: NTFS
 Listed in GPT as partition 5, type Basic Data
 Listed in MBR as partition 2, type 07  NTFS/HPFS, active
```

---

### Post by wulgulmerang on 2012-12-31
I am using [http://www.supergrubdisk.org/super-grub2-disk/](http://www.supergrubdisk.org/super-grub2-disk/) to boot into Ubuntu whilst waiting for a resolution.

Super-Grub2-Disk detects all operating systems, although I have only tested the boot of Ubuntu.

---

### Post by wulgulmerang on 2013-01-02
I need to get moving on this so I'm repartitioning and restoring Windows 7 using Carbon Copy Cloner and Repair Your Computer (the Fix Master Boot Record command).  

I'll then install the secure remix version of Ubuntu 12.10 which comes pre-packaged with Boot Repair.
[https://help.ubuntu.com/community/UbuntuSecureRemix](https://help.ubuntu.com/community/UbuntuSecureRemix)

---

### Post by wulgulmerang on 2013-01-02
Triple boot system is working ;-)

To avoid the problems I encountered use partitioning tools to structure the master boot record like this.

3 primary partitions and 1 primary extended partition containing 2 logical partitions for Ubuntu.

Everything is bootable in rEFIt.

The GRUB 2 loader was installed to logical partition (1) /dev/sda4

```

Primary Partition #    DiskPath                  Name
(1)                    /dev/sda1                 EFI
(2)                    /dev/sda2                 Macintosh HD (HFS)
(3)                    /dev/sda3                 Windows HD   (NTFS)

(4) [Extended Partition Containing]

Logical Partition #    DiskPath                  Name     
(1)                    /dev/sda4                 Ubuntu HD (ext4)       
(2)                    /dev/sda5                 Linux Swap

```

---

