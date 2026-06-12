---
title: "Problems to uninstall grub2"
date: 2013-03-15
forum: General Help
---

### Post by unconcrete on 2013-03-15
Hi all,
I have accidentally installed grub2 in my mbr and now i cant use win8.

Can I use my ubuntu 12.10 live to uninstall completely grub from my system? You know that i ve done the following actions:

First I ve installed boot-repair and from advanced i ve chosen top fix mbr. Once it removed correctly grub2. 
Not this time. At reboot appairs the grub2 minimal command line.


Secondly I have tried the win8 command line bootrec.exe /fixmbr, but at reboot appairs the grub2 minimal command line. That has happened three times.

Any suggestion?

unconcrete

---

### Post by oldfred on 2013-03-15
Was this Windows 8 pre-installed. If so it does not use MBR, but efi partition.

May be best to see what is where:
 Post the link to the BootInfo report that this creates. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.
Install in Ubuntu liveCD or USB or Full RepairCD with Boot-Repair (for newer computers) 
[http://sourceforge.net/p/boot-repair/home/Home/](http://sourceforge.net/p/boot-repair/home/Home/)
[https://help.ubuntu.com/community/UbuntuSecureRemix](https://help.ubuntu.com/community/UbuntuSecureRemix)

Also do you have hibernation on. Unless you specifically turned off fast boot it is on.
      
 WARNING for Windows 8 Dual-Booters
[http://ubuntuforums.org/showthread.php?t=1953674](http://ubuntuforums.org/showthread.php?t=1953674)
It defaults shutdown to a hybrid hibernation/off state for fast boot 
[http://www.kapilarya.com/how-to-enable-disable-fast-start-up-in-windows-8](http://www.kapilarya.com/how-to-enable-disable-fast-start-up-in-windows-8)
But then files may be corrupted similar to Windows 7 Hibernation:
[http://ubuntu-with-wubi.blogspot.ca/2012/09/windows-8-fast-start-and-hybrid-sleep.html](http://ubuntu-with-wubi.blogspot.ca/2012/09/windows-8-fast-start-and-hybrid-sleep.html)
[http://superuser.com/questions/144720/missing-files-when-windows-7-returns-from-hibernate-w-dual-boot](http://superuser.com/questions/144720/missing-files-when-windows-7-returns-from-hibernate-w-dual-boot)

---

### Post by unconcrete on 2013-03-15
> **oldfred said:**
> Was this Windows 8 pre-installed. If so it does not use MBR, but efi partition.

May be best to see what is where:
 Post the link to the BootInfo report that this creates. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.
Install in Ubuntu liveCD or USB or Full RepairCD with Boot-Repair (for newer computers) 
[http://sourceforge.net/p/boot-repair/home/Home/](http://sourceforge.net/p/boot-repair/home/Home/)
[https://help.ubuntu.com/community/UbuntuSecureRemix](https://help.ubuntu.com/community/UbuntuSecureRemix)

Also do you have hibernation on. Unless you specifically turned off fast boot it is on.
      
 WARNING for Windows 8 Dual-Booters
[http://ubuntuforums.org/showthread.php?t=1953674](http://ubuntuforums.org/showthread.php?t=1953674)
It defaults shutdown to a hybrid hibernation/off state for fast boot 
[http://www.kapilarya.com/how-to-enable-disable-fast-start-up-in-windows-8](http://www.kapilarya.com/how-to-enable-disable-fast-start-up-in-windows-8)
But then files may be corrupted similar to Windows 7 Hibernation:
[http://ubuntu-with-wubi.blogspot.ca/2012/09/windows-8-fast-start-and-hybrid-sleep.html](http://ubuntu-with-wubi.blogspot.ca/2012/09/windows-8-fast-start-and-hybrid-sleep.html)
[http://superuser.com/questions/144720/missing-files-when-windows-7-returns-from-hibernate-w-dual-boot](http://superuser.com/questions/144720/missing-files-when-windows-7-returns-from-hibernate-w-dual-boot)
I-ll try to use ubuntu secure remix64 bit with a new usb flash. I-ll tell you the results tomorrow.
Thank you.
Unconcrete.

---

### Post by unconcrete on 2013-03-22
For network problems, I have not downloaded the ubuntu-secure-remix iso. I've used an iso i downloaed sometimes ago Ubuntu 12.10 Gnome Desktop. The installation has at first successful. Since my system is Uefi I've installed Grub2 in the original Dell partition, /dev/sda1 for Linux.
Unfortunately now I can use only ubuntu.
The windows partition /dev/sda5 -ntfs is still resident but not avalaible.
At reboot the computer don't display the grub menu but go to ubuntu directly. Just before the system displays this warning: "empty security header".
I've never heard a similar error.
:(
tired unconcrete.

    If it can be useful, this my bootlog of boot-repair:
    [http://paste.ubuntu.com/5637627/](http://paste.ubuntu.com/5637627/)
    Bye soon.

---

### Post by oldfred on 2013-03-22
You can only have one efi partition per drive. Gparted uses the boot flag to define the efi partition but it has a totally different meaning with UEFI. Removed boot flag from your main Windows in sda5.

Do you have secure boot on? Does Ubuntu boot ok? Some UEFI only boot Ubuntu with secure boot off and Windows with secure boot on. But Ubuntu should boot with secure boot on or off, with its shim file which has the same Microsoft key as Windows. But some UEFI are modified to only boot Windows. Boot-Repair then may rename files to make UEFI think it is booting Windows but really booting shim.

Grub does not create correct entries for Windows but Boot-Repair will or you can manually add entries as shown in the bug's work arounds.
         grub-update fails to detect windows bootloader on a uefi system
[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/807801](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/807801)
grub2's os-prober creates wrong style (BIOS) chain boot entry
[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1024383](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1024383)
type of entry from Boot-Repair that should work.
'Windows UEFI loader'
Type of entry that does not work:
'Windows ...) (on /dev/sdXY)'

Best to backup efi partition before making lots of changes.
      
 Boot-Repair - Updated Jan 1, 2013 to not rename first time, but rename if first time Windows does not boot. Post 706 and 711
[http://ubuntuforums.org/showthread.php?t=1769482&page=71](http://ubuntuforums.org/showthread.php?t=1769482&page=71)
 Boot-Repair copied /EFI/ubuntu/grubx64.efi to /EFI/Boot/bootx64.efi (in case the BIOS is hard-coded to boot into /EFI/Boot/bootx64.efi or secure boot signed GRUB file shimx64.efi.
I disabled secure boot, and unchecked it in boot-repair. It now bypasses Grub and goes straight in to Windows. 
/EFI/Boot/bkpbootx64.efi
/EFI/Microsoft/Boot/bkpbootmgfw.efi 

   To perform this, just run Boot-Repair --> Adv options --> tick "Backup and rename EFI files" --> Apply
Then reboot the PC to UEFI/BIOS and chose ubuntu,  and please tell us what you observe.
Please enable SecureBoot in your BIOS, then run Boot-Repair --> Advanced Options --> "GRUB options" tab --> tick "SecureBoot" --> Apply.

You can undo the renaming by unchecking the secure boot in Boot-Repair and rerunning it, if need be.

---

