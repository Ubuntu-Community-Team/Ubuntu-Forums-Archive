---
title: "Installed Ubuntu on USB now I can't boot my windows 10"
date: 2019-09-05
forum: General Help
---

### Post by max1337 on 2019-09-05
Alright so downloaded ubuntu a couple of days ago and now I want to switch back to windows 10. When i restart my pc I can only choose ubuntu as OS. This is my boot repair if someone can take a look at it. [http://paste.ubuntu.com/p/FYJTP5R4BB/](http://paste.ubuntu.com/p/FYJTP5R4BB/) 
Would I be able to just turn my pc off, insert windows 7 cd in my external harddrive and then would I be able to boot it up? //100% computer noob. Thank you

---

### Post by Skaperen on 2019-09-05
do you have a Windows 10 rescue disk?

---

### Post by max1337 on 2019-09-05
No I do not, It's only a windows key cd. Had windows 10 preinstalled when I bought my pc.

---

### Post by Skaperen on 2019-09-05
your PC manufacturer should provide one.  but many require you to call support to get one.  i hope they don't delay sending it.  maybe someone else here has a better answer like maybe a grub command if there is a boot loader in the partition it can load and run.

---

### Post by max1337 on 2019-09-05
Alright thank you I will contact them. If anyone else got tips they are still appreciated! :)

---

### Post by oldfred on 2019-09-05
Script has not been updated to show all the details on NVMe drives.
And it looks like Ubuntu is in UEFI boot mode, but you rebooted and run Boot-Repair from a BIOS boot. Only use UEFI boot. 

But it looks like Windows is installed in UEFI boot mode on NVMe drive.
But first partition is missing, it should be FAT32 with boot flag or the ESP - efi system partition. That second partition is not shown is normal as that is required Microsoft System reserved partition that must be unformatted so normally shown as an error as unformatted. Do not know why software does not see it as Microsoft reserved, so error messages should be ignored.

Reboot Ubuntu live installer in UEFI mode and run these.
       sudo parted /dev/nvme0n1 unit s print 
      
 lsblk  -o NAME,LABEL,PARTLABEL,SIZE,UUID,MOUNTPOINT

---

