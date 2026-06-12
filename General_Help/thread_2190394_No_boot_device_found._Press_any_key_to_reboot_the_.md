---
title: "No boot device found. Press any key to reboot the machine?"
date: 2013-11-27
forum: General Help
---

### Post by Ashfaqur Rahman on 2013-11-27
Ubuntu 13.10 64 Bit And Windows 7 64 Bit are installed in my Laptop. Mostly I use ubuntu. And my laptop is Dell Inspiron 3521.
Today when I opened my laptop, got that error message ( Attached a photo of the message ).
At first I thought my HDD crashed. So I checked everything with Boot Menu's 'Diagnosis' option via ePSA Pre-boot System Assessment. And Everything passed.
Also checked HDD Partitions from an Live Environment. All files are OK.
But still showing that error message. Can't understand whats wrong.
Does Anybody know how can I restore and access my operating systems?

---

### Post by oldfred on 2013-11-27
PXE is the Internet boot choice from BIOS boot order. Is that first or above hard drive?
Hard drive should be first in boot order with flash or DVD next. And then you can use one time boot key to boot your Ubuntu live installer as a repair disk from USB or DVD.
Does BIOS show hard drive correctly?

From Ubuntu live installer, add Boot-Repair and post link.
       Post the link to the BootInfo report that this creates. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.

---

### Post by Ashfaqur Rahman on 2013-11-28
Problem solved using "recommended repair" option from boot-repair software (awesome software!!!).
But can't find my Windows OS. Here is link of my boot-info [http://paste.ubuntu.com/6490193/](http://paste.ubuntu.com/6490193/)
Thanks.

---

### Post by oldfred on 2013-11-28
You are missing a partition or two at the beginning of the drive. While your main Windows is in sda5 that is not bootable.
Windows only boots from a primary partition or sda1 thru sda4. And second installs of Windows move all boot files to the install in the primary partition with the boot flag. 
Grub does not use boot flag, and it needs to be on the primary partition with Windows boot files.
More info:
       Multibooters, Pictures here worth 1000+ words
[http://www.multibooters.co.uk/multiboot.html](http://www.multibooters.co.uk/multiboot.html)

Either use testdisk to restore sda1 and move boot flag to sda1. Or create a new NTFS boot partition as sda1 and put boot flag on it. You then will have to use a Windows repairCD or flash drive to restore the two missing boot files.

      
 Vista/7 (with 7 the first two files are usually in a separate 100MB boot partition)
[COLOR=#ff0000]/bootmgr /Boot/BCD[/COLOR] /Windows/System32/winload.exe 
You are missing the two in red.

---

