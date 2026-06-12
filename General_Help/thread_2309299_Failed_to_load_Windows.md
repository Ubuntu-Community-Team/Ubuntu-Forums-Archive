---
title: "Failed to load Windows"
date: 2016-01-09
forum: General Help
---

### Post by leonardo23 on 2016-01-09
Hi all,
yesterday I was trying to install a version of ArchLinux, but  a blackout forced me to stop the installation and to erase the linux partitions. So I get the "Missing operating system" message during the attempt to reboot win10. I followed the ubuntu guide to restore MBR with a live USB but it didn't work and I obtained only a black window with a blinking  dash. So I thought to reinstall Ubuntu and repair mbr with boot-repair, but now I get "Microsoft failed to load" and tips about repair windows with the CD, but I haven't it, I bought the pc with embedded license. Now I'm using Ubuntu succesfully installed in a partition, and the grub selection of win10 doesn't work ("Microsoft failed to load, etc."). How could I fix this? :D Please help me, and thanks!

P.S. The data on the hdd are not very important, I can erase them if it is necessary (in case: how could I do a "factory reset" of the hdd with Ubuntu?)

This is the output of "fidsk -l":
```
Device     Start      End   Sector   Size Type
/dev/sda1        2048  31459327  31457280    15G Windows recovery environment
/dev/sda2    31459328  31664127    204800   100M Microsoft basic data
/dev/sda3    31664128 897124510 865460383 412,7G Microsoft basic data
/dev/sda4   897126400 897128447      2048     1M BIOS boot
/dev/sda5   897128448 964339711  67211264  32,1G Linux filesystem
/dev/sda6   964339712 976771071  12431360     6G Linux swap

```

---

### Post by oldfred on 2016-01-09
Is this a new system with UEFI?
It looks like Windows is in BIOS/MBR mode, but drive may now be gpt as I do not see an extended partition. Windows in BIOS mode only boots from MBR(msdos) partitioned drive.

Post this:
        sudo parted /dev/sda unit s print

Did you leave Windows 10 always on hibernation or fast start up on? 
      
 Fast Startup off
[http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html](http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html)
[URL="http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.htmlold"]http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.htmlold
[/URL]
 How to: perform a repair upgrade using the Windows 10 ISO file
[http://answers.microsoft.com/en-us/insider/wiki/insider_wintp-insider_install/how-to-perform-a-repair-upgrade-using-the-windows/35160fbe-9352-4e70-9887-f40096ec3085](http://answers.microsoft.com/en-us/insider/wiki/insider_wintp-insider_install/how-to-perform-a-repair-upgrade-using-the-windows/35160fbe-9352-4e70-9887-f40096ec3085)
How to: Create a Recovery Drive for reinstalling Windows 10 from Windows 10
[http://answers.microsoft.com/en-us/windows/wiki/windows_10-win_upgrade/how-to-create-a-recovery-drive-for-reinstalling/58df9c7d-84de-4652-9952-8bac34abc6c5](http://answers.microsoft.com/en-us/windows/wiki/windows_10-win_upgrade/how-to-create-a-recovery-drive-for-reinstalling/58df9c7d-84de-4652-9952-8bac34abc6c5)


Grub only boots working Windows or a Windows that is not hibernated. Windows also must be in the same boot mode UEFI or BIOS as Ubuntu is installed.

---

### Post by leonardo23 on 2016-01-09
Thanks for the reply :)
No, it is with classic BIOS.

Output:
```
Modello: ATA ST3500418AS (scsi)Disco /dev/sda: 976773168s
Dimensione del settore (logica/fisica): 512B/512B
Tabella delle partizioni: gpt
Flag del disco: 


Numero  Inizio      Fine        Dimensione  File system     Nome                  Flag
 1      2048s       31459327s   31457280s   ntfs            Windows RE            diag
 2      31459328s   31664127s   204800s     ntfs            Microsoft basic data  msftdata
 3      31664128s   897124510s  865460383s  ntfs            Microsoft basic data  msftdata
 4      897126400s  897128447s  2048s                                             bios_grub
 5      897128448s  964339711s  67211264s   ext4
 6      964339712s  976771071s  12431360s   linux-swap(v1)



```

I have tried to make a USB with win10 iso but it always brings me to the grub, even if I choose the USB device as boot :(

Don't know what you mean with fast startup or hibernation! :s

---

### Post by oldfred on 2016-01-09
See links above on Windows fast start up. It must be off.
But you have converted system to gpt partitioning
> Tabella delle partizioni: gpt

Windows install is BIOS, but Windows only boots from gpt partitioned drives with UEFI.
You need to convert drive back to MBR.

       Converting to or from GPT
[http://www.rodsbooks.com/gdisk/mbr2gpt.html](http://www.rodsbooks.com/gdisk/mbr2gpt.html)

Backups required and you will have to reinstall grub to MBR afterwards.
      
 How to restore the Ubuntu/XP/Vista/7/8/10 BIOS bootloader 
[https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader](https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader)
[https://help.ubuntu.com/community/Grub2/Installing#Fixing_a_Broken_System](https://help.ubuntu.com/community/Grub2/Installing#Fixing_a_Broken_System)

---

### Post by leunam12 on 2016-01-09
If you have access to another computer with Windows 7 or 8 you can download the Windows 10 ISO and burn installation media to USB stick or DVD

---

