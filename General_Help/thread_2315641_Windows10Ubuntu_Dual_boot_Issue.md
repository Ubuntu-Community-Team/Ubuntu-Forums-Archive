---
title: "Windows10/Ubuntu Dual boot Issue"
date: 2016-03-01
forum: General Help
---

### Post by Josh_Abraham on 2016-03-01
Thanks you for looking at my post and appreciate your help
I was able to create a partition and install Ubantu alongside Windows 10 and both OS were stable.  I was not given a choice on which OS to boot so while booting i had to go to the boot menu everytime to select which OS to load. 
In order to get the boot option. i went into windows 10, opened a command prompt with admin rights and ran bcdedit /set {bootmgr} path \EFI\ubuntu\grubx64.efi
Since then i am not able to boot into windows 10. 
My efiboormgr is as below . The boot order is correct and it thinks windows is loading but it is actually ubuntu which is.
```
BootCurrent: 0016
Timeout: 0 seconds
BootOrder: 0016,0017,0008,0009,000A,000B,000C,000D,000E,0014,0015,0013,0007
Boot0000  Setup
Boot0001  Boot Menu
Boot0016* Windows Boot Manager
Boot0017* ubuntu
```
---------------------------------------
Even if i select Windows Boot Manager from my boot menu it still loads ubuntu.
efibootmgr -v shows the below
----------------------------
```
BootCurrent: 0016
Timeout: 0 seconds
BootOrder: 0016,0017,0008,0009,000A,000B,000C,000D,000E,0014,0015,0013,0007
Boot0000  Setup    FvFile(721c8b66-426c-4e86-8e99-3457c46ab0b9)
Boot0001  Boot Menu    FvFile(126a762d-5758-4fca-8531-201a7f57f850)
Boot0002  Diagnostic Splash Screen    FvFile(a7d8d9a6-6ab0-4aeb-ad9d-163e59a7a380)
Boot0003  Lenovo Diagnostics    FvFile(3f7e615b-0d45-4f80-88dc-26b234958560)
Boot0004  Startup Interrupt Menu    FvFile(f46ee6f4-4785-43a3-923d-7f786c3c8479)
Boot0005  Rescue and Recovery    FvFile(665d3f60-ad3e-4cad-8e26-db46eee9f1b5)
Boot0006  MEBx Hot Key    FvFile(ac6fd56a-3d41-4efd-a1b9-870293811a28)
Boot0007* USB CD    VenMsg(bc7838d2-0f82-4d60-8316-c068ee79d25b,86701296aa5a7848b66cd49dd3ba6a55)
Boot0008* USB FDD    VenMsg(bc7838d2-0f82-4d60-8316-c068ee79d25b,6ff015a28830b543a8b8641009461e49)
Boot0009* ATAPI CD0    VenMsg(bc7838d2-0f82-4d60-8316-c068ee79d25b,aea2090adfde214e8b3a5e471856a35405)
Boot000A* ATA HDD0    VenMsg(bc7838d2-0f82-4d60-8316-c068ee79d25b,91af625956449f41a7b91f4f892ab0f600)
Boot000B* ATA HDD1    VenMsg(bc7838d2-0f82-4d60-8316-c068ee79d25b,91af625956449f41a7b91f4f892ab0f605)
Boot000C* ATA HDD2    VenMsg(bc7838d2-0f82-4d60-8316-c068ee79d25b,91af625956449f41a7b91f4f892ab0f604)
Boot000D* USB HDD    VenMsg(bc7838d2-0f82-4d60-8316-c068ee79d25b,33e821aaaf33bc4789bd419f88c50803)
Boot000E* PCI LAN    VenMsg(bc7838d2-0f82-4d60-8316-c068ee79d25b,78a84aaf2b2afc4ea79cf5cc8f3d3803)
Boot000F* IDER BOOT CDROM    PciRoot(0x0)/Pci(0x16,0x2)/Ata(0,1,0)
Boot0010* IDER BOOT Floppy    PciRoot(0x0)/Pci(0x16,0x2)/Ata(0,0,0)
Boot0011* ATA HDD    VenMsg(bc7838d2-0f82-4d60-8316-c068ee79d25b,91af625956449f41a7b91f4f892ab0f6)
Boot0012* All CD:    VenMsg(bc7838d2-0f82-4d60-8316-c068ee79d25b,aea2090adfde214e8b3a5e471856a354)
Boot0013* PCI LAN    VenMsg(bc7838d2-0f82-4d60-8316-c068ee79d25b,78a84aaf2b2afc4ea79cf5cc8f3d3803)
Boot0014  Other CD    VenMsg(bc7838d2-0f82-4d60-8316-c068ee79d25b,aea2090adfde214e8b3a5e471856a35406)
Boot0015  Other HDD    VenMsg(bc7838d2-0f82-4d60-8316-c068ee79d25b,91af625956449f41a7b91f4f892ab0f606)
Boot0016* Windows Boot Manager    HD(2,GPT,34028a74-e929-4953-88a5-a5b98dbd6c61,0x1f4800,0x82000)/File(\EFI\ubuntu\grubx64.efi)WINDOWS.........x...B.C.D.O.B.J.E.C.T.=.{.9.d.e.a.8.6.2.c.-.5.c.d.d.-.4.e.7.0.-.a.c.c.1.-.f.3.2.b.3.4.4.d.4.7.9.5.}....................
Boot0017* ubuntu    HD(2,GPT,34028a74-e929-4953-88a5-a5b98dbd6c61,0x1f4800,0x82000)/File(\EFI\ubuntu\shimx64.efi)
```
--------------------------------------------------------
Do you see that the windows boot manager entry points to ubuntu
```
Boot0016* Windows Boot Manager    HD(2,GPT,34028a74-e929-4953-88a5-a5b98dbd6c61,0x1f4800,0x82000)/File(\EFI\ubuntu\grubx64.efi)WINDOWS.........x...B.C.D.O.B.J.E.C.T.=.{.9.d.e.a.8.6.2.c.-.5.c.d.d.-.4.e.7.0.-.a.c.c.1.-.f.3.2.b.3.4.4.d.4.7.9.5.}....................
```

Also the currentboot in Ubuntu shows windows but for some reason it is booting ubuntu.
I am a beginner linux user and dont mind going to boot menu to load each os but how do i get back to loading windows.
Appreaciate your help.
Josh

---

### Post by oldfred on 2016-03-01
You posted the issue above.
You have Windows description but it uses 
 \EFI\ubuntu\grubx64.efi.

Is your ESP - efi system partition sda1 or another partition. The entries for editing UEFI default to sda1 and need extra settings if any other partition.

I do not know how to change an entry, so suggest deleting incorrect Windows entry (0016) and adding correct Windows entry.
      
 Delete entry change XXXX to correct entries. Some UEFI require all 4 HEX char, other just need 1 or 2 significant char.
sudo efibootmgr -b XXXX -B
       
 [http://linux.die.net/man/8/efibootmgr](http://linux.die.net/man/8/efibootmgr)
[URL="http://linux.dell.com/cgi-bin/gitweb/gitweb.cgi?p=efibootmgr.git;a=blob_plain;f=README;hb=HEAD"]http://linux.dell.com/cgi-bin/gitweb/gitweb.cgi?p=efibootmgr.git;a=blob_plain;f=README;hb=HEAD

      [/URL]
 New Windows entry - assumes default sda1  add -p 2 if sda2, see links above for details:
sudo efibootmgr -c -L "Windows Boot Manager" -l "\EFI\Microsoft\Boot\bootmgfw.efi"

    [URL="http://linux.dell.com/cgi-bin/gitweb/gitweb.cgi?p=efibootmgr.git;a=blob_plain;f=README;hb=HEAD"]
[/URL]

---

### Post by Josh_Abraham on 2016-03-01
Thanks you so much.  I removed my windows boot entry.  

Looks like the default sda1 is not true for me. How do I find where my windows boot is pointing to?

I want to rewrite this command and customize it.
 sudo efibootmgr -c -L "Windows Boot Manager" -l "\EFI\Microsoft\Boot\bootmgfw.efi"

---

### Post by oldfred on 2016-03-01
Your ESP is the FAT32 formatted partition with the boot flag. It may be labeled efi or ESP.

If unsure post this:
sudo parted -l

This is what mine looks like:
```
Number  Start   End     Size    File system  Name    Flags
 1      1049kB  53.5GB  53.5GB  fat32        ESP     boot, esp

```

You have to add drive & partition info to efibootmgr commands. If drive is sda, you to add correct partition info.
If sda2  then include:  -p 2

Note that some of the command codes are two items like -L and -l, so do not have between those.

If sda3 change 2 to 3.
sudo efibootmgr -c -p 2 -L "Windows Boot Manager" -l "\EFI\Microsoft\Boot\bootmgfw.efi"

---

### Post by Josh_Abraham on 2016-03-01
Thanks.
```
 sudo parted -l
[sudo] password for joshua: 
Error: Invalid argument during seek for read on /dev/sda
Retry/Ignore/Cancel?       ignore
Error: The backup GPT table is corrupt, but the primary appears OK, so that will be used.

ok/Cancel? Ok
Model: ATA ST500LM021-1KJ15 (scsi)
Disk /dev/sda: 500GB
Sector size (logical/physical): 512B/4096B
Partition Table: unknown
Disk Flags: 

Error: /dev/sdb: unrecognised disk label
Model: ATA ST500LM021-1KJ15 (scsi)                                        
Disk /dev/sdb: 500GB
Sector size (logical/physical): 512B/4096B
Partition Table: unknown
Disk Flags: 

Model: Linux device-mapper (linear) (dm)
Disk /dev/mapper/isw_cgaieedcei_OEMRAID0p4: 826GB
Sector size (logical/physical): 512B/4096B
Partition Table: loop
Disk Flags: 

Number  Start  End    Size   File system  Flags
 1      0.00B  826GB  826GB  ntfs


Model: Linux device-mapper (linear) (dm)
Disk /dev/mapper/isw_cgaieedcei_OEMRAID0p5: 15.1GB
Sector size (logical/physical): 512B/4096B
Partition Table: loop
Disk Flags: 

Number  Start  End     Size    File system  Flags
 1      0.00B  15.1GB  15.1GB  ntfs


Model: Linux device-mapper (linear) (dm)
Disk /dev/mapper/isw_cgaieedcei_OEMRAID0p1: 1049MB
Sector size (logical/physical): 512B/4096B
Partition Table: loop
Disk Flags: 

Number  Start  End     Size    File system  Flags
 1      0.00B  1049MB  1049MB  ntfs


Model: Linux device-mapper (linear) (dm)
Disk /dev/mapper/isw_cgaieedcei_OEMRAID0p2: 273MB
Sector size (logical/physical): 512B/4096B
Partition Table: loop
Disk Flags: 

Number  Start  End    Size   File system  Flags
 1      0.00B  273MB  273MB  fat32


Error: /dev/mapper/isw_cgaieedcei_OEMRAID0p3: unrecognised disk label
Model: Linux device-mapper (linear) (dm)                                  
Disk /dev/mapper/isw_cgaieedcei_OEMRAID0p3: 134MB
Sector size (logical/physical): 512B/4096B
Partition Table: unknown
Disk Flags: 

Model: Linux device-mapper (linear) (dm)
Disk /dev/mapper/isw_cgaieedcei_OEMRAID0p7: 157GB
Sector size (logical/physical): 512B/4096B
Partition Table: loop
Disk Flags: 

Number  Start  End    Size   File system  Flags
 1      0.00B  157GB  157GB  ext4


Model: Linux device-mapper (linear) (dm)
Disk /dev/mapper/isw_cgaieedcei_OEMRAID0p6: 32.5MB
Sector size (logical/physical): 512B/4096B
Partition Table: loop
Disk Flags: 

Number  Start  End     Size    File system     Flags
 1      0.00B  32.5MB  32.5MB  linux-swap(v1)


Model: Linux device-mapper (striped) (dm)
Disk /dev/mapper/isw_cgaieedcei_OEMRAID0: 1000GB
Sector size (logical/physical): 512B/4096B
Partition Table: gpt
Disk Flags: 

Number  Start   End     Size    File system     Name                          Flags
 1      1049kB  1050MB  1049MB  ntfs                                          hidden, diag
 2      1050MB  1322MB  273MB   fat32           EFI system partition          boot, esp
 3      1322MB  1456MB  134MB                   Microsoft reserved partition  msftres
 4      1456MB  828GB   826GB   ntfs            Basic data partition          msftdata
 6      828GB   828GB   32.5MB  linux-swap(v1)
 7      828GB   985GB   157GB   ext4
 5      985GB   1000GB  15.1GB  ntfs                                          hidden, diag
```

```
fdisk -l give the delow warnings

GPT PMBR size mismatch (1953536511 != 976773167) will be corrected by w(rite).
Disk /dev/sda: 465.8 GiB, 500107862016 bytes, 976773168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disklabel type: dos
Disk identifier: 0x9863939a

Device     Boot Start        End    Sectors   Size Id Type
/dev/sda1           1 1953536511 1953536511 931.5G ee GPT

Partition 1 does not start on physical sector boundary.


Disk /dev/sdb: 465.8 GiB, 500107862016 bytes, 976773168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/mapper/isw_cgaieedcei_OEMRAID0: 931.5 GiB, 1000210694144 bytes, 1953536512 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 16384 bytes / 32768 bytes
Disklabel type: gpt
Disk identifier: 5ED1396F-D439-4376-8FD7-07DD834C79EA

Device                                     Start        End    Sectors   Size Type
/dev/mapper/isw_cgaieedcei_OEMRAID0p1       2048    2050047    2048000  1000M Windows recovery environment
/dev/mapper/isw_cgaieedcei_OEMRAID0p2    2050048    2582527     532480   260M EFI System
/dev/mapper/isw_cgaieedcei_OEMRAID0p3    2582528    2844671     262144   128M Microsoft reserved
/dev/mapper/isw_cgaieedcei_OEMRAID0p4    2844672 1616932863 1614088192 769.7G Microsoft basic data
/dev/mapper/isw_cgaieedcei_OEMRAID0p5 1924132864 1953533951   29401088    14G Windows recovery environment
/dev/mapper/isw_cgaieedcei_OEMRAID0p6 1616932864 1616996351      63488    31M Linux swap
/dev/mapper/isw_cgaieedcei_OEMRAID0p7 1616996352 1924132863  307136512 146.5G Linux filesystem

Partition table entries are not in disk order.
```

```
sudo fixparts /dev/sda
FixParts 1.0.0

Loading MBR data from /dev/sda

This disk appears to be a GPT disk. Use GNU Parted or GPT fdisk on it!
Exiting!
```

```
lsblk
NAME                          MAJ:MIN RM   SIZE RO TYPE   MOUNTPOINT
sda                             8:0    0 465.8G  0 disk   
&#9492;&#9472;isw_cgaieedcei_OEMRAID0     252:0    0 931.5G  0 dmraid 
  &#9500;&#9472;isw_cgaieedcei_OEMRAID0p1 252:1    0  1000M  0 part   
  &#9500;&#9472;isw_cgaieedcei_OEMRAID0p2 252:2    0   260M  0 part   /boot/efi
  &#9500;&#9472;isw_cgaieedcei_OEMRAID0p3 252:3    0   128M  0 part   
  &#9500;&#9472;isw_cgaieedcei_OEMRAID0p4 252:4    0 769.7G  0 part   
  &#9500;&#9472;isw_cgaieedcei_OEMRAID0p5 252:5    0    14G  0 part   
  &#9500;&#9472;isw_cgaieedcei_OEMRAID0p6 252:6    0    31M  0 part   [SWAP]
  &#9492;&#9472;isw_cgaieedcei_OEMRAID0p7 252:7    0 146.5G  0 part   /
sdb                             8:16   0 465.8G  0 disk   
&#9492;&#9472;isw_cgaieedcei_OEMRAID0     252:0    0 931.5G  0 dmraid 
  &#9500;&#9472;isw_cgaieedcei_OEMRAID0p1 252:1    0  1000M  0 part   
  &#9500;&#9472;isw_cgaieedcei_OEMRAID0p2 252:2    0   260M  0 part   /boot/efi
  &#9500;&#9472;isw_cgaieedcei_OEMRAID0p3 252:3    0   128M  0 part   
  &#9500;&#9472;isw_cgaieedcei_OEMRAID0p4 252:4    0 769.7G  0 part   
  &#9500;&#9472;isw_cgaieedcei_OEMRAID0p5 252:5    0    14G  0 part   
  &#9500;&#9472;isw_cgaieedcei_OEMRAID0p6 252:6    0    31M  0 part   [SWAP]
  &#9492;&#9472;isw_cgaieedcei_OEMRAID0p7 252:7    0 146.5G  0 part   /
```

---

### Post by oldfred on 2016-03-02
I know nothing about RAID nor LVM. 
Many I have seen have ESP & /boot partitions outside of LVM and those with RAID often have a separate non-RAID boot drive.

You must have "FakeRAID" or BIOS RAID for UEFI to see the ESP inside the RAID partitions.
       Do not use gparted on RAID.
[http://www.howtoforge.com/how-to-resize-raid-partitions-shrink-and-grow-software-raid](http://www.howtoforge.com/how-to-resize-raid-partitions-shrink-and-grow-software-raid)
Don't bother with RAID 0 unless you have a specific need for speed without data redundancy, since if one drive goes out, you lose the whole array.
[http://en.wikipedia.org/wiki/RAID](http://en.wikipedia.org/wiki/RAID)
[http://www.smallnetbuilder.com/nas/nas-features/31745-data-recovery-tales-raid-is-not-backup](http://www.smallnetbuilder.com/nas/nas-features/31745-data-recovery-tales-raid-is-not-backup)

May be older and not include UEFI info.
       
 [https://help.ubuntu.com/community/FakeRaidHowto](https://help.ubuntu.com/community/FakeRaidHowto)
15.04 or later now uses mdadm to support intel fakeraids  
    
But you do need to resolve gpt issues first, but sometimes Linux does not see RAID correctly, depending on type of RAID. 
If RAID 0, it may not see gpt partition table at end of RAID but at end of drive?
So that may be the issue?

 repair gpt:
[http://www.rodsbooks.com/gdisk/repairing.html](http://www.rodsbooks.com/gdisk/repairing.html)

---

### Post by Josh_Abraham on 2016-03-02
When I try to add the Windows Boot Manager back It says

GUID Partition Table Header signature is wrong: 0 ! = 5152415020494645
GUID Partition Table Header signature is wrong: 0 ! = 5152415020494645
GUID Partition Table Header signature is wrong: 0 ! = 5152415020494645
BootCurrent: 0017
...

What should I do?

---

### Post by Josh_Abraham on 2016-03-02
I was able to add the Windows Boot Manager. Then I loaded Windows and it loaded fine. Then I loaded Ubuntu and it was fine. 
Then I tried efibootmgr -v and Windows seems to overwrite "\EFI\Microsoft\Boot\bootmgfw.efi" with "\EFI\ubuntu\grubx64.efi".

Now wheneven I reboot either though boot menu choosing Ubuntu or Windows it loads Ubuntu as it is pointing to "\EFI\ubuntu\grubx64.efi".
How do I prevent windows 10 from overwriting "\EFI\Microsoft\Boot\bootmgfw.efi" with "\EFI\ubuntu\grubx64.efi".

---

### Post by oldfred on 2016-03-02
I do not know BCD.
But Microsoft resyncs BCD and UEFI.
So what changes did you make in BCD?

This is the suggested entry"
 Some systems work better to register grub/shim from inside Windows - for those that keep resetting Windows as default
[http://askubuntu.com/questions/371559/grub-not-showing-on-startup-for-windows-8-1-ubuntu-13-10-dual-boot](http://askubuntu.com/questions/371559/grub-not-showing-on-startup-for-windows-8-1-ubuntu-13-10-dual-boot)
bcdedit /set {bootmgr} path \EFI\ubuntu\grubx64.efi
  
Did you replace the Windows entry and not add a second BCD entry for ubuntu?

---

### Post by Josh_Abraham on 2016-03-02
Thank you. This is what I initially did. 

In windows 10, opened a command prompt with admin rights and ran bcdedit /set {bootmgr} path \EFI\ubuntu\grubx64.efi

Should I get back into windows and run 

bcdedit /set {bootmgr} path \EFI\Microsoft\Boot\bootmgfw.efi

---

### Post by oldfred on 2016-03-02
I thought the BCD entry was an additional entry not replacing the Windows entry.
But do not know details of BCD.

If it is replacing default, then you can only boot Windows from grub. But I prefer that you have a way to boot all installed systems from UEFI. I also like to have another boot entry using /EFI/Boot/bootx64.efi. That is often called fallback or is a hard drive boot entry. Currently Linux does not add it. Boot-Repair is supposed to add it. And most Windows systems have that but bootx64.efi is really another copy of Windows bootgfw.efi. But that would stil use same BCD.

I only have Ubuntu on main working system, and only system with Windows is just to stream video and I still do not know Windows 10 commands. Last version of Windows I really used was XP, years ago.

---

### Post by Josh_Abraham on 2016-03-02
I was able to point Windows to boot with \EFI\Microsoft\Boot\bootmgfw.efi. I have to still go to the boot menu to load Ubuntu. I didn't figure out how to get the grub option. 
If anyone knows let me know.

---

### Post by oldfred on 2016-03-02
If both are UEFI, run this:
sudo update-grub

---

### Post by Josh_Abraham on 2016-03-02
Thanks. Tried sudo update-grub and the command ran successfully. However on reboot I am still not seeing an option to choose OS. I have to go to the boot menu.

---

### Post by oldfred on 2016-03-02
Is Windows hibernated. If so Linux NTFS driver will not mount it, and then os-prober cannot find Windows install.

 Fast Startup off (always on hibernation)
[http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html](http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html)
[http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.htmlold](http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.htmlold)

---

