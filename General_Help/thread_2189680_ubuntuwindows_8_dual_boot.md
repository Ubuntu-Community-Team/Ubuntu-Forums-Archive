---
title: "ubuntu/windows 8 dual boot"
date: 2013-11-23
forum: General Help
---

### Post by asgard.guardian on 2013-11-23
I haven't been able to get into windows 8 since I successfully installed ubuntu. I love ubuntu but I still need windows 8, at least for the time being. 

The partition for windows still exists. It very obviously a boot issue. It appears system32/winload.exe is missing or damaged. Can anyone please help me troubleshoot this.I am a total noob when it comes to OS issues, boot issues, and ubuntu particularly. any help is appreciated. 

I ran boot repair and this was what the report looks like:

Boot Info Script e7fc706 + Boot-Repair extra info      [COLOR=#666666][[/COLOR]Boot-Info 6Nov2013[COLOR=#666666]][/COLOR]


[COLOR=#666666]=============================[/COLOR] Boot Info Summary: [COLOR=#666666]===============================[/COLOR]

 [COLOR=#666666]=[/COLOR]> No boot loader is installed in the MBR of /dev/sda.

sda1: __________________________________________________________________________

    File system:       
    Boot sector [COLOR=#AA22FF]type[/COLOR]:  -
    Boot sector info: 
    Mounting failed:   mount: unknown filesystem [COLOR=#AA22FF]type[/COLOR] [COLOR=#BB4444]''[/COLOR]

sda2: __________________________________________________________________________

    File system:       vfat
    Boot sector [COLOR=#AA22FF]type[/COLOR]:  Windows 8/2012: FAT32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /EFI/Boot/bkpbootx64.efi /EFI/Boot/bootx64.efi 
                       /EFI/ubuntu/grubx64.efi /EFI/ubuntu/shimx64.efi 
                       /EFI/Microsoft/Boot/bkpbootmgfw.efi 
                       /EFI/Microsoft/Boot/bootmgfw.efi 
                       /EFI/Microsoft/Boot/bootmgr.efi 
                       /EFI/Microsoft/Boot/bootx64.efi 
                       /EFI/Microsoft/Boot/memtest.efi

sda3: __________________________________________________________________________

    File system:       ntfs
    Boot sector [COLOR=#AA22FF]type[/COLOR]:  Windows 8/2012: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /bootmgr /Boot/BCD

sda4: __________________________________________________________________________

    File system:       ntfs
    Boot sector [COLOR=#AA22FF]type[/COLOR]:  Windows 8/2012: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 8
    Boot files:        /bootmgr /Boot/BCD /Windows/System32/winload.exe

sda5: __________________________________________________________________________

    File system:       ntfs
    Boot sector [COLOR=#AA22FF]type[/COLOR]:  Windows 8/2012: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sda6: __________________________________________________________________________

    File system:       ntfs
    Boot sector [COLOR=#AA22FF]type[/COLOR]:  Windows 8/2012: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sda7: __________________________________________________________________________

    File system:       ext4
    Boot sector [COLOR=#AA22FF]type[/COLOR]:  -
    Boot sector info: 
    Operating System:  Ubuntu 12.04.3 LTS 
    Boot files:        /boot/grub/grub.cfg /etc/fstab

sda8: __________________________________________________________________________

    File system:       swap
    Boot sector [COLOR=#AA22FF]type[/COLOR]:  -
    Boot sector info: 

[COLOR=#666666]============================[/COLOR] Drive/Partition Info: [COLOR=#666666]=============================[/COLOR]

Drive: sda _____________________________________________________________________

Disk /dev/sda: 750.2 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders, total 1465149168 sectors
[COLOR=#B8860B]Units[/COLOR] [COLOR=#666666]=[/COLOR] sectors of 1 * [COLOR=#B8860B]512[/COLOR] [COLOR=#666666]=[/COLOR] 512 bytes
Sector size [COLOR=#666666]([/COLOR]logical/physical[COLOR=#666666])[/COLOR]: 512 bytes / 4096 bytes

Partition  Boot  Start Sector    End Sector  [COLOR=#008800]*# of Sectors  Id System*[/COLOR]

/dev/sda1                   1 1,465,149,167 1,465,149,167  ee GPT


GUID Partition Table detected.

Partition    Start Sector    End Sector  [COLOR=#008800]*# of Sectors System*[/COLOR]
/dev/sda1              34       262,177       262,144 Microsoft Reserved Partition [COLOR=#666666]([/COLOR]Windows[COLOR=#666666])[/COLOR]
/dev/sda2         264,192       878,591       614,400 EFI System partition
/dev/sda3         878,592     2,109,439     1,230,848 Windows Recovery Environment [COLOR=#666666]([/COLOR]Windows[COLOR=#666666])[/COLOR]
/dev/sda4       2,109,440   588,271,615   586,162,176 Data partition [COLOR=#666666]([/COLOR]Windows/Linux[COLOR=#666666])[/COLOR]
/dev/sda5     588,271,616 1,002,309,916   414,038,301 Data partition [COLOR=#666666]([/COLOR]Windows/Linux[COLOR=#666666])[/COLOR]
/dev/sda6   1,423,446,016 1,465,147,391    41,701,376 Windows Recovery Environment [COLOR=#666666]([/COLOR]Windows[COLOR=#666666])[/COLOR]
/dev/sda7   1,002,311,680 1,411,088,383   408,776,704 Data partition [COLOR=#666666]([/COLOR]Windows/Linux[COLOR=#666666])[/COLOR]
/dev/sda8   1,411,088,384 1,423,446,015    12,357,632 Swap partition [COLOR=#666666]([/COLOR]Linux[COLOR=#666666])[/COLOR]

[COLOR=#BB4444]"blkid"[/COLOR] output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/sda2        9280-26E5                              vfat       SYSTEM
/dev/sda3        CA6850C36850B045                       ntfs       Recovery
/dev/sda4        FC7C53FF7C53B2DE                       ntfs       OS
/dev/sda5        785655335654F37C                       ntfs       Data
/dev/sda6        9EFE571DFE56ECD1                       ntfs       Restore
/dev/sda7        9dd39255-9d62-4fc7-9bb4-ac67e861449d   ext4       
/dev/sda8        d5d4b5a2-7bd3-4170-9be3-462f371dfc14   [COLOR=#B8860B]swap[/COLOR]       

[COLOR=#666666]================================[/COLOR] Mount points: [COLOR=#666666]=================================[/COLOR]

Device           Mount_Point              Type       Options

/dev/sda5        /media/Data              fuseblk    [COLOR=#666666]([/COLOR]rw,nosuid,nodev,allow_other,default_permissions,blksize[COLOR=#666666]=[/COLOR]4096[COLOR=#666666])[/COLOR]
/dev/sda6        /media/Restore           fuseblk    [COLOR=#666666]([/COLOR]rw,nosuid,nodev,allow_other,default_permissions,blksize[COLOR=#666666]=[/COLOR]4096[COLOR=#666666])[/COLOR]
/dev/sda7        /                        ext4       [COLOR=#666666]([/COLOR]rw,errors[COLOR=#666666]=[/COLOR]remount-ro[COLOR=#666666])[/COLOR]


[COLOR=#666666]===========================[/COLOR] sda7/boot/grub/grub.cfg: [COLOR=#666666]===========================[/COLOR]

--------------------------------------------------------------------------------

---

### Post by Allavona on 2013-11-23
Have you tried generating a new grub.cfg and reinsatlling grub to /dev/sda? Everything is being "seen," but you've no bootloader present in the MBR.

---

### Post by asgard.guardian on 2013-11-23
I have reinstalled grub. Although, I'm not too positive on what you mean. I ran the boot-repair program and it reinstalled grub and a number of others things. Is this what you mean? Sorry for the ignorance but I was a long time windows user. Thanks for the patience.

---

### Post by oldfred on 2013-11-24
It looks like Boot-Repair ran the rename function for those systems that only boot Windows. Many systems do not need that, but for those that do it is available. But then you can only boot Windows from the grub menu entry that Boot-Repair has added, not directly from UEFI.
If you can directly boot the ubuntu entry in UEFI, you do not need rename.

       To undo & to rename files to their original names, you just need to tick the "Restore EFI backups" option of Boot-Repair.


 It looks like boot repair ran its "buggy" UEFI rename function. I am not sure it is always required, but it is for those UEFI that internally hard code UEFI to only boot the Windows efi file. So Boot-Repair renames the Windows file and makes grub2's shim be the Windows file. The UEFI thinks it is booting Windows but is really booting grub2 and then from grub2 menu you can boot Windows.

   Then renamed /EFI/microsoft/boot/shimx64.efi to bootmgfw.efi
Actual Windows boot file, originally bootmgfw.efi.
/EFI/Microsoft/Boot/bkpbootmgfw.efi

   With the renamed file you cannot directly boot Windows from UEFI menu as it really is shim.

It also looks like you do not have the Windows  reserved partition. Did you manually delete a small partition that was unformatted.


 Order on drive is important:
[http://en.wikipedia.org/wiki/Microsoft_Reserved_Partition](http://en.wikipedia.org/wiki/Microsoft_Reserved_Partition)

 Microsoft suggested partitions including reserved partition for gpt & UEFI:
[http://technet.microsoft.com/en-us/library/dd744301%28WS.10%29.aspx](http://technet.microsoft.com/en-us/library/dd744301%28WS.10%29.aspx)
Older Windows info on gpt - 2008 updated 2011
[http://msdn.microsoft.com/en-us/windows/hardware/gg463525.aspx](http://msdn.microsoft.com/en-us/windows/hardware/gg463525.aspx)
Windows technical info on gpt and GUIDs
[http://msdn.microsoft.com/library/windows/desktop/aa365449](http://msdn.microsoft.com/library/windows/desktop/aa365449)

---

