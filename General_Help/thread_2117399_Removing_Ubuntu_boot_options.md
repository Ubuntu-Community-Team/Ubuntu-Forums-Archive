---
title: "Removing Ubuntu boot options"
date: 2013-02-18
forum: General Help
---

### Post by RugbyPlayer on 2013-02-18
Im having some trouble trying to remove an Ubuntu install. I am doing so because i partitioned my disks wrong, i ended up completely shrinking my windows drive to minimum instead of the ubuntu size. I deleted the partitions, expanded my windows one to fill the space.

Booted from my usb recovery stick, ran command prompt and did bootrec /fixmbr

I also ran bcdedit from windows 8 and it did not show a ubuntu partition anywhere. However when i boot with the yoga button it still shows me 2 ubuntu options. Also these boot option appear in my BIOS under the boot priority order.

On a side note just after installing ubuntu the bootloader would not let me boot into windows when selected and im not sure why.

I fixed that by changing the boot order to windows first, and then just using the yoga button if i wanted to get into ubuntu but this was rather cumbersome. Any help is greatly appreciate

---

### Post by fuorviatos on 2013-02-18
Boot into live mode and type:

> sudo su 

after becoming root do this and paste here the output:

> fdisk -l

---

### Post by Bucky Ball on 2013-02-18
*Thread moved to **General Help**.*

***Reason:*** Issue not related to desktop environments.

Better just:
```

sudo fdisk -l
```

No need to become root permanently in a terminal (better not to) but just for the one command.

---

### Post by RugbyPlayer on 2013-02-18
Disk /dev/sda: 128.0 GB, 128035676160 bytes
255 heads, 63 sectors/track, 15566 cylinders, total 250069680 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x800b876d

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1   250069679   125034839+  ee  GPT

Disk /dev/sdc: 1993 MB, 1993342976 bytes
255 heads, 63 sectors/track, 242 cylinders, total 3893248 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x9d84621a

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *         130     3893247     1946559    6  FAT16

---

### Post by RugbyPlayer on 2013-02-18
anybody see what is wrong?

---

### Post by oldfred on 2013-02-19
Windows will not boot Ubuntu.

You have Windows 8 preinstalled as you have gpt partitions. Did you turn secure boot off. Turn fast boot off and use 12.10 or the new 12.04.2?

       You will need to use the 64 bit version of 12.10 and from the UEFI menu boot the flash drive in UEFI mode. That way it will install in UEFI mode.
Systems need quick boot or fast boot turned off in UEFI settings. Vital for some systems. Best to backup efi partition and Windows partition first.
Use Windows Disk Tools to shrink Windows main partition, but not to create any new partitions, if installing on same drive.
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)
[https://wiki.archlinux.org/index.php/UEFI](https://wiki.archlinux.org/index.php/UEFI)
As of 12.04.2, it is possible to install on UEFI systems with Secure Boot enabled (using signed versions of Shim, GRUB, and the Linux kernel). This is only currently set up for Ubuntu (desktop, alternate, and server) and Edubuntu images due to pressures of time; we expect to enable it across the entire Ubuntu family for 12.04.3.  Details:
[https://wiki.ubuntu.com/PrecisePangolin/ReleaseNotes/UbuntuDesktop](https://wiki.ubuntu.com/PrecisePangolin/ReleaseNotes/UbuntuDesktop)

    
May be best to see details:
       Post the link to the BootInfo report that this creates. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.
Install in Ubuntu liveCD or USB or Full RepairCD with Boot-Repair (for newer computers) 
[http://sourceforge.net/p/boot-repair/home/Home/](http://sourceforge.net/p/boot-repair/home/Home/)
[https://help.ubuntu.com/community/UbuntuSecureRemix](https://help.ubuntu.com/community/UbuntuSecureRemix)

---

### Post by RugbyPlayer on 2013-02-21
> **oldfred said:**
> Windows will not boot Ubuntu.

You have Windows 8 preinstalled as you have gpt partitions. Did you turn secure boot off. Turn fast boot off and use 12.10 or the new 12.04.2?

       You will need to use the 64 bit version of 12.10 and from the UEFI menu boot the flash drive in UEFI mode. That way it will install in UEFI mode.
Systems need quick boot or fast boot turned off in UEFI settings. Vital for some systems. Best to backup efi partition and Windows partition first.
Use Windows Disk Tools to shrink Windows main partition, but not to create any new partitions, if installing on same drive.
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)
[https://wiki.archlinux.org/index.php/UEFI](https://wiki.archlinux.org/index.php/UEFI)
As of 12.04.2, it is possible to install on UEFI systems with Secure Boot enabled (using signed versions of Shim, GRUB, and the Linux kernel). This is only currently set up for Ubuntu (desktop, alternate, and server) and Edubuntu images due to pressures of time; we expect to enable it across the entire Ubuntu family for 12.04.3.  Details:
[https://wiki.ubuntu.com/PrecisePangolin/ReleaseNotes/UbuntuDesktop](https://wiki.ubuntu.com/PrecisePangolin/ReleaseNotes/UbuntuDesktop)

    
May be best to see details:
       Post the link to the BootInfo report that this creates. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.
Install in Ubuntu liveCD or USB or Full RepairCD with Boot-Repair (for newer computers) 
[http://sourceforge.net/p/boot-repair/home/Home/](http://sourceforge.net/p/boot-repair/home/Home/)
[https://help.ubuntu.com/community/UbuntuSecureRemix](https://help.ubuntu.com/community/UbuntuSecureRemix)


[http://paste.ubuntu.com/1698208/](http://paste.ubuntu.com/1698208/)

---

### Post by RugbyPlayer on 2013-02-21
> **RugbyPlayer said:**
> [http://paste.ubuntu.com/1698208/](http://paste.ubuntu.com/1698208/)

[http://paste.ubuntu.com/1698303/](http://paste.ubuntu.com/1698303/)

This is another link as well. the first one was made from my installed copy of ubuntu the second a live cd which is a pain to get working because wireless drivers are natively supported yet and its a chore to get wifi up on a live cd

That being said i am having a different issue now. When i try to boot into windows in grub im selecting Windows 8 (loader) (on/dev/sda5) it gives me the message
"error: cant fine command 'drivemap'.
error: invalid EFI file path."

---

### Post by oldfred on 2013-02-21
Grub has a bug and creates BIOS boot entires that do not work with UEFI. Boot-Repair has already added correct entries.

       grub2's os-prober creates wrong style (BIOS) chain boot entry
[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1024383](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1024383)
type of entry from Boot-Repair that should work.
'Windows UEFI loader'
Type of entry that does not work:
'Windows ...) (on /dev/sdXY)'

---

### Post by RugbyPlayer on 2013-02-21
> **oldfred said:**
> Grub has a bug and creates BIOS boot entires that do not work with UEFI. Boot-Repair has already added correct entries.

       grub2's os-prober creates wrong style (BIOS) chain boot entry
[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1024383](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1024383)
type of entry from Boot-Repair that should work.
'Windows UEFI loader'
Type of entry that does not work:
'Windows ...) (on /dev/sdXY)'

ive read through the link you posted and i see where they say how to fix it, but im not sure how to do it. all they say is add valid entries using boot repair

---

### Post by RugbyPlayer on 2013-02-21
i tried to run boot repair again and this is the link

[http://paste.ubuntu.com/1701010/](http://paste.ubuntu.com/1701010/)

---

### Post by RugbyPlayer on 2013-02-21
the issue has evolved to the point that i can no longer access my windows partition at all, no matter how i attempt to boot it. if i go to my boot menu and choose my windows boot loader it simply takes me to grub. This is rather urgent does anyone know how to fix this?

---

### Post by oldfred on 2013-02-21
Some systems only boot Windows, so Boot-Repair will rename the shim which has the Windows key to boot grub. Then grub boots the backup of the Windows file.
```

/dev/sda2        [COLOR=Red]D80B-A1BD [/COLOR]                             vfat       SYSTEM_DRV
```
Your sda2 is the efi partition. The other one must have efi files but be used for recover. Some titles seem to have recovery but should not.
```
menuentry "Windows UEFI recovery bkpbootmgfw.efi" {
search --fs-uuid --no-floppy --set=root [COLOR=Red]D80B-A1BD[/COLOR]
chainloader (${root})/EFI/Microsoft/Boot/bkpbootmgfw.efi
}

menuentry "Windows Boot UEFI recovery" {
search --fs-uuid --no-floppy --set=root [COLOR=Red]D80B-A1BD[/COLOR]
chainloader (${root})/EFI/Boot/bkpbootx64.efi
}

menuentry "Windows UEFI recovery LrsBootmgr.efi" {
search --fs-uuid --no-floppy --set=root 780B-D8B3
chainloader (${root})/EFI/Microsoft/Boot/LrsBootmgr.efi
}

menuentry "Windows Boot UEFI recovery bkpbootx64.efi" {
search --fs-uuid --no-floppy --set=root 780B-D8B3
chainloader (${root})/EFI/Boot/bkpbootx64.efi
}
```Then entries with [COLOR=Red]D80B-A1BD [COLOR=Black]should boot Windows.
[/COLOR][/COLOR]
 How Boot-Repair fixes a Ubuntu with grub-pc with efi Windows
[http://ubuntuforums.org/showpost.php?p=12205679&postcount=516](http://ubuntuforums.org/showpost.php?p=12205679&postcount=516)
Boot-Repair - Updated Jan 1, 2013 to not rename first time, but rename if first time Windows does not boot. Post 706 and 711
[http://ubuntuforums.org/showthread.php?t=1769482&page=71](http://ubuntuforums.org/showthread.php?t=1769482&page=71)
 Boot-Repair copied /EFI/ubuntu/grubx64.efi to /EFI/Boot/bootx64.efi (in case the BIOS is hard-coded to boot into /EFI/Boot/bootx64.efi or secure boot
signed GRUB file shimx64.efi.

    [COLOR=Red][COLOR=Black]
[/COLOR][/COLOR]

---

### Post by RugbyPlayer on 2013-02-21
> **oldfred said:**
> Some systems only boot Windows, so Boot-Repair will rename the shim which has the Windows key to boot grub. Then grub boots the backup of the Windows file.
```

/dev/sda2        [COLOR=Red]D80B-A1BD [/COLOR]                             vfat       SYSTEM_DRV
```
Your sda2 is the efi partition. The other one must have efi files but be used for recover. Some titles seem to have recovery but should not.
```
menuentry "Windows UEFI recovery bkpbootmgfw.efi" {
search --fs-uuid --no-floppy --set=root [COLOR=Red]D80B-A1BD[/COLOR]
chainloader (${root})/EFI/Microsoft/Boot/bkpbootmgfw.efi
}

menuentry "Windows Boot UEFI recovery" {
search --fs-uuid --no-floppy --set=root [COLOR=Red]D80B-A1BD[/COLOR]
chainloader (${root})/EFI/Boot/bkpbootx64.efi
}

menuentry "Windows UEFI recovery LrsBootmgr.efi" {
search --fs-uuid --no-floppy --set=root 780B-D8B3
chainloader (${root})/EFI/Microsoft/Boot/LrsBootmgr.efi
}

menuentry "Windows Boot UEFI recovery bkpbootx64.efi" {
search --fs-uuid --no-floppy --set=root 780B-D8B3
chainloader (${root})/EFI/Boot/bkpbootx64.efi
}
```Then entries with [COLOR=Red]D80B-A1BD [COLOR=Black]should boot Windows.
[/COLOR][/COLOR]
 How Boot-Repair fixes a Ubuntu with grub-pc with efi Windows
[http://ubuntuforums.org/showpost.php?p=12205679&postcount=516](http://ubuntuforums.org/showpost.php?p=12205679&postcount=516)
Boot-Repair - Updated Jan 1, 2013 to not rename first time, but rename if first time Windows does not boot. Post 706 and 711
[http://ubuntuforums.org/showthread.php?t=1769482&page=71](http://ubuntuforums.org/showthread.php?t=1769482&page=71)
 Boot-Repair copied /EFI/ubuntu/grubx64.efi to /EFI/Boot/bootx64.efi (in case the BIOS is hard-coded to boot into /EFI/Boot/bootx64.efi or secure boot
signed GRUB file shimx64.efi.

    [COLOR=Red][COLOR=Black]
[/COLOR][/COLOR]

nothing will boot into windows right now either through grub or using the bios boot menu

If i select the option you highlighted in red it tells me 

"error: file '/EFI/Microsoft/Boot/bkpbootmgfw.efi' no

I ran boot repair again and it gives me the usual startup screen for lenovo and seems to get completely stuck trying to load into windows 8. ive let it run for up to 10 minutes and it never seems to resolve

---

### Post by oldfred on 2013-02-21
You can always manually manage the boot files in the efi partition. I would always do a full backup of the efi partition. 

then rename the Window backup file to its correct name. You may also have a copy to the Windows efi file in your Main Windows install.

       Windows UEFI install should  have backup of bootmgrw.efi here:
C:\Windows\Boot\EFI\bootmgfw.efi from a working Windows x86_64 installation.

            Windows installs the efi bootloader to (ESP)/EFI/Microsoft/Boot/ which is identical to (WINDOWS_SYSTEM_PART)/boot/microsoft/ incase of BIOS systems.
The dir mainly consists of bootmgfw.efi, bootmgr.efi, memtest.efi and 'bcd'.

    
       Repair Windows 8 boot issues & repair CD or flash
[http://ubuntuforums.org/showthread.php?t=2105418](http://ubuntuforums.org/showthread.php?t=2105418)
[http://www.eightforums.com/tutorials/2855-system-repair-disc-create-windows-8-a.html](http://www.eightforums.com/tutorials/2855-system-repair-disc-create-windows-8-a.html)
[http://www.ms-windows.info/Help/bootmgr-not-found-bootrec-rebuildbcd-17554.aspx](http://www.ms-windows.info/Help/bootmgr-not-found-bootrec-rebuildbcd-17554.aspx)

    
       Users who manually moved efi files around:
[http://ubuntuforums.org/showthread.php?t=2101840](http://ubuntuforums.org/showthread.php?t=2101840)

---

