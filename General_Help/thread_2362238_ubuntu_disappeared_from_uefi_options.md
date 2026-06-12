---
title: "ubuntu disappeared from uefi options"
date: 2017-05-25
forum: General Help
---

### Post by ship22 on 2017-05-25
built a new computer about a month ago with an M.2 Samsung EVO storage stick. Was able to load both windows 10 and ubuntu 16.4 on it but after 30 days my cpu died.. long story short, the extensive troubleshooting ended up with only windows appearing on the EFI boot list.

There is still an EFI partition and ubuntu is still on there. Is there a way I can get this back on without reloading ubuntu?

root@ubuntu:/mnt/EFI# find .
.
./Microsoft
./Microsoft/Boot
./Microsoft/Boot/BCD
./Microsoft/Boot/BCD.LOG
./Microsoft/Boot/bg-BG
./Microsoft/Boot/bg-BG/bootmgfw.efi.mui
./Microsoft/Boot/bg-BG/bootmgr.efi.mui
./Microsoft/Boot/boot.stl
./Microsoft/Boot/bootmgfw.efi
./Microsoft/Boot/bootmgr.efi
<bunch of mickysoft localization dirs>
./Microsoft/Boot/BOOTSTAT.DAT
<mickysoft fonts>
./Microsoft/Boot/kd_02_10df.dll
./Microsoft/Boot/kd_02_10ec.dll
./Microsoft/Boot/kd_02_1137.dll
./Microsoft/Boot/kd_02_14e4.dll
./Microsoft/Boot/kd_02_15b3.dll
./Microsoft/Boot/kd_02_1969.dll
./Microsoft/Boot/kd_02_19a2.dll
./Microsoft/Boot/kd_02_8086.dll
./Microsoft/Boot/kd_07_1415.dll
./Microsoft/Boot/kd_0C_8086.dll
./Microsoft/Boot/kdstub.dll
./Microsoft/Boot/BCD.LOG1
./Microsoft/Boot/BCD.LOG2
./Microsoft/Recovery
./Microsoft/Recovery/BCD
./Microsoft/Recovery/BCD.LOG
./Microsoft/Recovery/BCD.LOG1
./Microsoft/Recovery/BCD.LOG2
./Boot
./Boot/bootx64.efi
./ubuntu
./ubuntu/fw
./ubuntu/fwupx64.efi
./ubuntu/grubx64.efi
./ubuntu/grub.cfg
./ubuntu/shimx64.efi
./ubuntu/mmx64.efi
./ubuntu/fbx64.efi

I can boot the installation flash drive.. hoping I can run a magic grub command that will just put micky and ubuntu in some happy .efi file that the asus bios will find and let me boot? Hoping to avoid reinstalling windows and ubuntu... spent a lot of time configuring them.

I have Microsoft and Ubuntu main os sharing the 250G M.2 device.. then a 960G SSD divided between windows and ubuntu for data partitions.

---

### Post by oldfred on 2017-05-25
What model Asus?

My Asus Z97 required a lot of UEFI setting changes.
       Asus z97 screenshots:
[http://ubuntuforums.org/showthread.php?t=2258575&page=297](http://ubuntuforums.org/showthread.php?t=2258575&page=297)
Minor problems with using an ASUS Z97-A Motherboard
[http://askubuntu.com/questions/503168/minor-problems-with-using-an-asus-z97-a-motherboard](http://askubuntu.com/questions/503168/minor-problems-with-using-an-asus-z97-a-motherboard)
[http://askubuntu.com/questions/554735/good-z97-motherboard-for-ubuntu](http://askubuntu.com/questions/554735/good-z97-motherboard-for-ubuntu)

If you re-install Ubuntu for full reinstall of grub2, it will update files in /EFI/ubuntu and add new entries in UEFI.
If a drive is disconnected, UEFI has entries in NVRAM and loses those. Typically it finds Windows but does not search for anything else.

If GUID matches then UEFI entry should work.
       
 to see GUID/partUUID for each device, post with code tags to preserve formatting:
lsblk -o +PARTUUID /dev/sda 
    
This shows details including the same GUID of ESP - efi system partition.
sudo efibootmgr -v

If entries not in UEFI, then you can use efibootmgr to add entries or use Boot-Repair which can reset with grub-install or do the full reinstall of all of grub.
      
 [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by ship22 on 2017-05-26
Thank you! I have a z270-A Prime. I will go through the information you provided and hopefully resolve this. Thank you very much.

---

### Post by oldfred on 2017-05-26
I think the UEFI is very similar to my older z97.

 Asus Prime Z270-A  Ethernet patch
[https://ubuntuforums.org/showthread.php?t=2351572](https://ubuntuforums.org/showthread.php?t=2351572)

---

### Post by ship22 on 2017-06-12
hoping someone can just give me a good efibootmgr command to add ubuntu back into the bootx64.efi file. It's all there, just don't want to mangle things by guessing and having to reformat and start over.

**Two base OS systems on NVME drive:**
Disk /dev/nvme0n1: 232.9 GiB, 250059350016 bytes, 488397168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: gpt
Disk identifier: 2A17C8F5-D5E4-49D3-A365-C5AD7C3A5BD5

Device             Start       End   Sectors   Size Type
/dev/nvme0n1p1      2048    923647    921600   450M Windows recovery environment
/dev/nvme0n1p2    923648   1126399    202752    99M EFI System
/dev/nvme0n1p3   1126400   1159167     32768    16M Microsoft reserved
/dev/nvme0n1p4   1159168 235519999 234360832 111.8G Microsoft basic data
/dev/nvme0n1p5 235520000 236496895    976896   477M EFI System
/dev/nvme0n1p6 236496896 488396799 251899904 120.1G Linux filesystem

[B]but after a bios update, only windows10 is showing up as a boot option.. (and the flash drive with the ubuntu install I plugged in):
*root@ubuntu:~# efibootmgr *[/B]
BootCurrent: 0002
Timeout: 1 seconds
BootOrder: 0000,0002,0003,0008,0009,000A,0007
Boot0000* Windows Boot Manager
Boot0002* UEFI: VerbatimSTORE N GO 5.00, Partition 1
Boot0003* UEFI: VerbatimSTORE N GO 5.00
Boot0007  SanDisk Ultra II 960GB
Boot0008  SanDisk Ultra II 960GB
Boot0009  Samsung SSD 960 EVO 250GB
Boot000A  VerbatimSTORE N GO 5.00
***root@ubuntu:~# efibootmgr -v***
BootCurrent: 0002
Timeout: 1 seconds
BootOrder: 0000,0002,0003,0008,0009,000A,0007
Boot0000* Windows Boot Manager    HD(2,GPT,e86a206e-c481-4c0c-bc72-4d493e352b41,0xe1800,0x31800)/File(\EFI\MICROSOFT\BOOT\BOOTMGFW.EFI)WINDOWS.........x...B.C.D.O.B.J.E.C.T.=.{.9.d.e.a.8.6.2.c.-.5.c.d.d.-.4.e.7.0.-.a.c.c.1.-.f.3.2.b.3.4.4.d.4.7.9.5.}...M................
Boot0002* UEFI: VerbatimSTORE N GO 5.00, Partition 1    PciRoot(0x0)/Pci(0x14,0x0)/USB(2,0)/HD(1,MBR,0x4294967271,0x2caa70,0x1280)..BO
Boot0003* UEFI: VerbatimSTORE N GO 5.00    PciRoot(0x0)/Pci(0x14,0x0)/USB(2,0)/CDROM(1,0x2caa70,0x4a00)..BO
Boot0007  SanDisk Ultra II 960GB    BBS(HD,,0x0)..BO
Boot0008  SanDisk Ultra II 960GB    BBS(HD,,0x0)..BO
Boot0009  Samsung SSD 960 EVO 250GB    BBS(HD,,0x0)..BO
Boot000A  VerbatimSTORE N GO 5.00    BBS(HD,,0x0)..BO

**Ubuntu is still on the efi partition:**
***root@ubuntu:~# ls /mnt/EFI/ubuntu/***
fbx64.efi  fw  fwupx64.efi  grub.cfg  grubx64.efi  mmx64.efi  shimx64.efi

Is there an efibootmgr command I can use to add ubuntu (on /dev/nvme0n1p6) back into the efi boot file? (is that /mnt/EFI/Boot/bootx64.efi ?)

I** mounted the efi partition on:**
/dev/nvme0n1p2     97280   28927     68353  30% /mnt

thank you.. just dont' want to wipe everything out yet again, if I can avoid it.

---

### Post by oldfred on 2017-06-13
If you updated UEFI, it reset a lot of things back to defaults.
With older BIOS, updates always reset everything & I had to take photos to remember all the settings I change.
With my UEFI, it both has screenshots and a list of changes that I am making when I change settings, so I both do screenshots & keep a manual list.

You can only have one ESP - efi system partition per device or drive.
You need to remove boot flag from /dev/nvme0n1p5. The ESP also must the be FAT32 formatted one.
I believe this is correct for NVMe drive.
 sudo efibootmgr -c -L "UEFI hard drive" -l "\EFI\Boot\bootx64.efi" -d /dev/nvme0n1 -p 2  
        sudo efibootmgr -c -g  -w -L "UEFI hard drive" -l '\EFI\Boot\bootx64.efi' -d /dev/sdX -p Y 
sdX is drive, Y is efi partition 
See also 
man efibootmgr

After running the command, run this to see if hard drive entry added and if first in boot order.
Some UEFI will not keep an Ubuntu entry as first, but often will allow a bootx64.efi or fallback entry to work. 

sudo efibootmgr -v

You have to have copied shimx64.efi to be bootx64.efi. Often if you already have bootx64.efi, your UEFI has a hard drive entry of some type. And then bootx64.efi is just another copy of the Windows .efi boot file.
Boot-Repair will copy shimx64.efi if you check the 'Use the Standard' file option in advanced options.

---

### Post by ship22 on 2017-06-18
That worked. Thank you oldfred!

---

### Post by oldfred on 2017-06-18
Your are welcome.

Please change to solved so others that search forum can find possible solution to their issue.

---

