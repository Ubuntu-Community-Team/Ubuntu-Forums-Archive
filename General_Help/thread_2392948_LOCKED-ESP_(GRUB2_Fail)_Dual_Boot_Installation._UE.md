---
title: "LOCKED-ESP (GRUB2 Fail) Dual Boot Installation. UEFI"
date: 2018-05-27
forum: General Help
---

### Post by mrwednezday on 2018-05-27
I install windows on an SSD.
I then load live usb Ubuntu 18.04 and install on another harddrive HDD.
I have done "Install alongside Windows bootloader."
I have done manual partition install : EFI, /, swap, /home
I receive the same error.
"[grub-efi-amd64-signed failed"]("https://askubuntu.com/questions/789998/16-04-new-installation-gives-grub-efi-amd64-signed-failed-installation-target")

I have done what many have suggested such as:
 remove boot flags of the efi,
 go to windows and delete ubuntu folder,
 go to liveusb Ubuntu and use boot-repair 
uncheck secureboot
Install on HDD SDA1 (EFI)
But, the error now is, "LOCKED ESP. Please create a fat32 /boot/efi partition and retry."
and it keeps on doing the same thing and I am getting frustrated.
Please help.

Also: I have done this.
Install windows.
USBLive Ubuntu 18.04
Manually create /boot/efi
But, I receive the error, "another source already has a /boot/efi (windows)"

---

### Post by yancek on 2018-05-27
Go to the site below and download boot repair using the Ubuntu install media.  Select the option to Create BootInfo Summary and post the link here.  The message would indicate you created or tried to create an EFI partition when you already had one.  That isn't necessary.

   [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by SL0ltMJGyh on 2018-05-27
did you allocate the free space using the Windows Disk Management Tool? You can only install to the free space allocated by Windows previously (stupid UEFI). Then you boot into your installer and install alongside Windows.

---

### Post by mrwednezday on 2018-05-28
I have not tried the windows disk management, but i assume it would be the same thing as ubuntus gparted. I will try and then let you know.

By the way, windows is on an SSD, I plan to install ubuntu on a seperate HDD drive

---

### Post by yancek on 2018-05-28
The link below is the official Ubuntu documentation on dual booting with windows using UEFI.  I would suggest you read it carefully.

[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

---

### Post by oldfred on 2018-05-28
Never remove boot flag from ESP. 
That is how UEFI knows it is the efi system partition, or the FAT32 partition with .efi boot files. Otherwise UEFI will not be able to boot.

Do not use Windows to remove Linux partitions, only use it to resize NTFS partitions. And reboot into Windows and run chkdsk after any change to NTFS partitions. 
Use Windows tools for Windows & Linux tools for Linux in most cases.

Always make sure Windows fast start up is off. Windows on updates will turn it back on, and it often is updating.

---

### Post by mrwednezday on 2018-05-28
@oldfred ---Thank you. 

Solution: Disable UEFI Window's "Fast Startup" via control panel > power options

But, I do need help with something else now. How do i edit what I want to see on Grub's boot loader? 

For example, on Grub's bootloader there are these options:

*Ubuntu
Boot/efi
Something/efi
Something/something
Windows boot loader
Windows/something
*Windows

Only two of them work the one with the asterisk *

I would like to remove all other options off of boot and possibly rename Ubuntu and Windows. How may i do this?

---

### Post by oldfred on 2018-05-28
Are you looking at UEFI boot menu, often f10 or f12, or grub menu?
sudo efibootmgr -v
       # List entries in grub:
cat /boot/grub/grub.cfg  | grep menuentry 
    
If UEFI, you can often edit in your UEFI, often f2. Or with efibootmgr

If grub, there is the easy gui way, where you do not know what it is doing, and usually works but replaces most of the grub scripts with its own. If it does not work you have to boot live installer and totally uninstall/reinstall grub.
And the bit more complicated way to manually edit files.

---

### Post by mrwednezday on 2018-05-28
Thanks @oldfred . I am assuming this is Grub. No more liveUSB involved. I installed both my windows and ubuntu in its UEFI version.
And yeah all i want to do is reduce the options of what to boot woth only 2 to make it easy on the eyes.

---

### Post by oldfred on 2018-05-28
Post the output of the two commands in my previous post.

---

### Post by mrwednezday on 2018-05-29
Hello @oldfred here is the output for

Sudo efibootmgr -v

BootCurrent: FFFF
Timeout: 2 seconds
No BootOrder is set; firmware will attempt recovery
Boot0000* Windows Boot Manager	HD(2,GPT,56d005e3-264c-4de7-8068-a5cc4a863036,0xfa000,0x32000)/File(\EFI\Microsoft\Boot\bootmgfw.efi)WINDOWS.........x...B.C.D.O.B.J.E.C.T.=.{.9.d.e.a.8.6.2.c.-.5.c.d.d.-.4.e.7.0.-.a.c.c.1.-.f.3.2.b.3.4.4.d.4.7.9.5.}...o................

---

### Post by oldfred on 2018-05-29
That does not even show an UEFI boot entry for Ubuntu.

       May be best to see details, you can run from your Ubuntu live installer or any working install, use ppa version not older Boot-Repair ISO:
Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info) and:
[https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/)

Some with locked ESP needed to run chkdsk from Windows for dosfcsk from Ubuntu. Others have had to backup ESP, delete ESP, and recreate ESP as FAT32 with boot flag & restore from backup.

       
 dosfstools - dosfsck (aka fsck.msdos and fsck.vfat) utilities
Must be unmounted, change example with sdb1 to your ESP, usually sda1 or sda2 but varies.
sudo dosfsck -t -a -w /dev/sdb1
The -a seems to help in clearing dirty bit
[https://bbs.archlinux.org/viewtopic.php?id=164185](https://bbs.archlinux.org/viewtopic.php?id=164185)

---

### Post by mrwednezday on 2018-05-29
wow that is very strange-- because i am using ubuntus grub bootloader to boot into either ubuntu or windows

> **oldfred said:**
> That does not even show an UEFI boot entry for Ubuntu.

       May be best to see details, you can run from your Ubuntu live installer or any working install, use ppa version not older Boot-Repair ISO:
Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info) and:
[https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/)

Some with locked ESP needed to run chkdsk from Windows for dosfcsk from Ubuntu. Others have had to backup ESP, delete ESP, and recreate ESP as FAT32 with boot flag & restore from backup.

       
 dosfstools - dosfsck (aka fsck.msdos and fsck.vfat) utilities
Must be unmounted, change example with sdb1 to your ESP, usually sda1 or sda2 but varies.
sudo dosfsck -t -a -w /dev/sdb1
The -a seems to help in clearing dirty bit
[https://bbs.archlinux.org/viewtopic.php?id=164185](https://bbs.archlinux.org/viewtopic.php?id=164185)

Can you repeat this? As i stated on my first post I would always receieve the error "Locked ESP" with boot-repair
Or Ubuntu 18.04 x64 iso " grub2-amd64-signed failed."

---

### Post by oldfred on 2018-05-29
Did you run the dosfsck command.
And then run a Boot-Repair report and post link.

---

### Post by mrwednezday on 2018-05-29
```
 sudo dosfsck -t -a -w /dev/sda1
fsck.fat 4.1 (2017-01-24)
Logical sector size is zero.

```

---

### Post by oldfred on 2018-05-29
Post link to summary report from Boot-Repair.

---

### Post by mrwednezday on 2018-05-30
> **oldfred said:**
> Post link to summary report from Boot-Repair.

Now it is telling me something different.

[http://paste.ubuntu.com/p/SFW57z46HJ/](http://paste.ubuntu.com/p/SFW57z46HJ/)

```
You can now reboot your computer.
Please do not forget to make your BIOS boot on sda4/EFI/ubuntu/shimx64.efi file!


The boot files of [The OS now in use - Ubuntu 18.04 LTS] are far from the start of the disk. Your BIOS may not detect them. You may want to retry after creating a /boot/efi partition (FAT32, 100MB~250MB, start of the disk, boot flag). This can be performed via tools such as gParted. Then select this partition via the [Separate /boot/efi partition:] option of [Boot Repair].


If your computer reboots directly into Windows, try to change the boot order in your BIOS.
If your BIOS does not allow to change the boot order, change the default boot entry of the Windows bootloader.
For example you can boot into Windows, then type the following command in an admin command prompt:
bcdedit /set {bootmgr} path
```

---

### Post by oldfred on 2018-05-30
Turn UEFI Secure Boot off.

What brand/model system?
It is not registering a UEFI entry. Some other systems like HP need work arounds and booting the fallback or hard drive entry, but you do not show either as an entry.

Did you update UEFI from Vendor?
Does it show UEFI entries in UEFI menu?
You have two ESP, did you run the dosfsck on both? One on each drive.
It looks like ESP on sdb is Windows and sda is Ubuntu, but you also have ubuntu entries in sdb.

---

### Post by mrwednezday on 2018-05-30
```
     
Family: Core i7
Manufacturer: Intel(R) Corporation
SOX5810J.86A.5600.2013.0729.2250

```

Turn UEFI Secure Boot off of Boot-Repair or my BIOS?
There is no such thing as "Secure Boot" on my Bios options and I have UEFI set to on.

Also, When I start computer It loads to GNU Grub Bootloader and these are my entries.
```

*Ubuntu
Advanced Options for Ubuntu
EFI/BOOT/bkpbootx64.efi
EFI/BOOT/fbx64.efi
EFI/BOOT/ubuntu/mmx64.efi
Windows UEFI bootmgfw.efi
Windows Boot UEFI Loader
Windows Boot UEFI fbx64.efi
Windows Boot Manager (on /dev/sdb2) 
```

How can I remove Ubuntu entries on SDB?

---

### Post by oldfred on 2018-05-30
Microsoft still requires vendors to let users turn UEFI Secure Boot off.
Your system must have it somewhere.

What brand/model system?
some have unique settings.
My Secure boot is called "Windows" or "Other" and manual notes say to use "Other" with Windows 7 as it does not support UEFI Secure Boot.

---

