---
title: "Xp not showing on ubuntu's grub"
date: 2013-06-30
forum: General Help
---

### Post by cuzzo13 on 2013-06-30
I had Windows 7 first then I installed xp now i just installed ubuntu 12.04. Windows 7 is on grub and it works along side ubuntu. But xp is not on there, I see the many threads on the subject but they all have specific partition settings. I ran fdisk -l but nothing happened so is there a way t fix it from windows perhaps easybcd?

---

### Post by hansdown on 2013-06-30
Welcome to the forum,cuzzo13. 

Running ubuntu, type 

> sudo update- grub

in terminal.

---

### Post by cuzzo13 on 2013-06-30
When I run that this is what it says; 

cuzzo@Cuzzos-Pc:~$ sudo update-grub
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-3.5.0-23-generic
Found initrd image: /boot/initrd.img-3.5.0-23-generic
Found memtest86+ image: /boot/memtest86+.bin
Found Windows 7 (loader) on /dev/sda1
Found Windows 7 (loader) on /dev/sda2
Found Windows Recovery Environment (loader) on /dev/sda4
done

However as you can see Xp is not there i forgot to mention i had ran this earlier. I thought the second win7 at sda2 was xp but it wont load I get a error when i choose that. Iam using a toshiba satellite l455d-s5976

---

### Post by hansdown on 2013-06-30
What is the error, when you choose 

> sda2

---

### Post by fantab on 2013-06-30
You say you had Win7 earlier and that you've installed XP recently.

Look in your BIOS settings for 'SATA Mode'. Tell us what mode it is set to, IDE or ACHI? 
XP will NOT boot in ACHI mode. The SATA mode must be set to IDE, but if you set to IDE then you may have to re-install Windows7 (or search the web for a solution to run Win7 in IDE mode when it was actually installed in ACHI mode).
Ubuntu will not have such issues though.

However, it may to important to note that ACHI is a better and superior interface to IDE which is more or less outdated now.

---

### Post by deadflowr on 2013-06-30
> [COLOR=#000000] I ran fdisk -l but nothing happened[/COLOR]

Needs to run as root.
Try it with sudo, and post the output.

---

### Post by cuzzo13 on 2013-06-30
It says 
cuzzo@Cuzzos-Pc:~$ sudo fdisk -l
[sudo] password for cuzzo: 

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x9a0c9a0c

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1            2048     3074047     1536000   27  Hidden NTFS WinRE
/dev/sda2   *     3074048   290269183   143597568    7  HPFS/NTFS/exFAT
/dev/sda3       290271230   471427424    90578097+   f  W95 Ext'd (LBA)
/dev/sda4       471437312   488396799     8479744    7  HPFS/NTFS/exFAT
/dev/sda5       344883483   471427424    63271971    7  HPFS/NTFS/exFAT
/dev/sda6       290271232   342929435    26329102   83  Linux
/dev/sda7       342931456   344883199      975872   82  Linux swap / Solaris

Partition table entries are not in disk order

Disk /dev/mapper/cryptswap1: 999 MB, 999292928 bytes
255 heads, 63 sectors/track, 121 cylinders, total 1951744 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xed39bb44

Disk /dev/mapper/cryptswap1 doesn't contain a valid partition table

Disk /dev/sdb: 4294 MB, 4294967296 bytes
133 heads, 62 sectors/track, 1017 cylinders, total 8388608 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System

Disk /dev/sdc: 15.9 GB, 15931539456 bytes
256 heads, 63 sectors/track, 1929 cylinders, total 31116288 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000d357e

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *        2048    31116287    15557120    c  W95 FAT32 (LBA)

Here is what choosing sda2 says
Windows could not start because the following file is missing
or corrupt:
<Windows root>\system32\hal.dll.
Please re-install a copy of the above file.

fantab Ill try your way if I have to but I want to avoid reinstalling win7 for now

---

### Post by fantab on 2013-06-30
Also post the output of:

```
sudo parted -l
```

Meanwhile check: [http://pcsupport.about.com/od/findbyerrormessage/a/missinghaldll.htm](http://pcsupport.about.com/od/findbyerrormessage/a/missinghaldll.htm)

---

### Post by cuzzo13 on 2013-06-30
cuzzo@Cuzzos-Pc:~$ sudo parted -l
[sudo] password for cuzzo: 
Model: ATA Hitachi HTS54502 (scsi)
Disk /dev/sda: 250GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type      File system  Flags
 1      1049kB  1574MB  1573MB  primary   ntfs         diag
 2      1574MB  149GB   147GB   primary   ntfs         boot
 3      149GB   241GB   92.8GB  extended               lba
 6      149GB   176GB   27.0GB  logical   ext4
 7      176GB   177GB   999MB   logical
 5      177GB   241GB   64.8GB  logical   ntfs
 4      241GB   250GB   8683MB  primary   ntfs


Model: LGE Android Platform (scsi)
Disk /dev/sdb: 4295MB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start  End  Size  Type  File system  Flags


Model: LGE Android Platform (scsi)
Disk /dev/sdc: 15.9GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type     File system  Flags
 1      1049kB  15.9GB  15.9GB  primary  fat32        boot, lba


Model: Linux device-mapper (crypt) (dm)
Disk /dev/mapper/cryptswap1: 999MB
Sector size (logical/physical): 512B/512B
Partition Table: loop

Number  Start  End    Size   File system     Flags
 1      0.00B  999MB  999MB  linux-swap(v1)

---

### Post by fantab on 2013-07-01
On what partition is XP installed? Is it /dev/sda4?

---

### Post by hansdown on 2013-07-01
Please note the android entries.

Just saying.

---

### Post by cuzzo13 on 2013-07-01
im not sure i know xp has a 60gb partition

---

### Post by hansdown on 2013-07-01
In a windows environement,

[http://support.microsoft.com/kb/314477](http://support.microsoft.com/kb/314477)

Error message 3.

Doesn't help the boot problem.

---

### Post by hansdown on 2013-07-01
> **cuzzo13 said:**
> im not sure i know xp has a 60gb partition

That is likely a restore partition.

---

### Post by cuzzo13 on 2013-07-01
> **hansdown said:**
> That is likely a restore partition.
 
No I specifically installed it to that partition 60GB after making it.

---

### Post by cuzzo13 on 2013-07-01
Also the Android entries are there because I was trying to boot from sd chip because I don't have a DVD or CD right now but that's not working my laptop recognizes the drive in bios and I used the unetbootin and USB creator and about two or three other methods that were recommended for Ubuntu and XP USB installs none seem to work the bios is set to boot it first and both work from disk as I used them earlier today to install both on this system.

---

### Post by cuzzo13 on 2013-07-01
I ran chkdsk d: /r and got the failed to successfully scan disks...error may be caused by a corrupt file system... 
Error message again.

---

### Post by fantab on 2013-07-01
Ok if you are cent percent sure that you've installed XP on 60GB partition which is /dev/sda5:

> 5      177GB   241GB   **64.8GB  logical **  ntfs

then, Windows WILL NOT boot from Logical Partition. It has to be installed on the Primary Partition only, AFAIK.

---

### Post by cuzzo13 on 2013-07-01
how would i change it?

---

### Post by oldfred on 2013-07-01
The first install of Windows has to be in a primary partition, but you can install additional copies of Windows in logical partitions. But all boot files for second install is usually moved to first install in primary partition and second install has no boot files.
Grub then will not find any bootable second install of Windows.

But you installed an older copy of Windows second which may not work or require you to run bdcEdit in Windows 7 to add the XP entry to the BCD.
The hal.dll is almost always an issue with boot.ini which could be the case with as BCD with Windows 7 has replaced the use of boot.ini. So XP may not have configured its boot.ini correctly.

 Windows Boot files - you may have both of these in your Windows 7 install:
WinXP
/boot.ini /ntldr /NTDETECT.COM
Vista/7 (with 7 the first two files are usually in a separate 100MB boot partition)
/bootmgr /Boot/BCD /Windows/System32/winload.exe 

Best to see details.
      
 Post the link to the BootInfo report that this creates. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.
LighterWeight (Lubuntu based) Boot-RepairCD
[http://sourceforge.net/projects/boot-repair-cd/files/](http://sourceforge.net/projects/boot-repair-cd/files/)
Full Ubuntu 13.04 liveDVD or USB Install with Boot-Repair included (for newer computers) 
[https://help.ubuntu.com/community/LinuxSecureRemix](https://help.ubuntu.com/community/LinuxSecureRemix)

---

