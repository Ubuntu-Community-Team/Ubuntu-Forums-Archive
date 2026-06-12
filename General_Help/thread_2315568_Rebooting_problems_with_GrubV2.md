---
title: "Rebooting problems with GrubV2"
date: 2016-02-29
forum: General Help
---

### Post by Bryant_Holt on 2016-02-29
I recently downloaded ubuntu 15.10 but before downloading it I created a partitian in windows 10 for 60 GB. After experiencing crash problems I decided I no longer wanted the Ubuntu 15.10. So, I went back to my disk management in windows and deleted the patrician i originally set for ubuntu 15.10 and created 80GB partician for ubuntu 14 lts. 

After booting up the system screen take me straight to a blank GNU GRUB terminal. It dosent even show the option to boot windows. I than booted Ubuntu from my flash drive. After i did that i checked the system hardrive disk space and seen that it only has 6GB worth of memory. Is there anyway I can fix this problem?

---

### Post by yoshii on 2016-02-29
If you still have your Windows install CD you can boot up with it and perform a recovery or do a bootfix.  Unfortunately I can't remember the details of how to do it. 
But essentially there's a normal procedure for reinstalling the Windows boot loader and reinstating the system file status and stuff like that.  If you don't have the Windows install disc, you could maybe borrow it from a friend.  I do remember that on the Windows install disc there are some command files that can be manually run.  I think one of them is called FIXMBR, but I don't remember for sure, and the last time I did it, I was on Windows 7.  I also did it for Windows XP.  But it's been so long ago I can't remember the details... sorry.  Also, I don't know if Windows 10 works the same way.  And it's probably different with UEFI/GPT instead of BIOS/MBR.  

But I do know that typically the Windows install discs can be booted into and have a few different techniques available in Recovery mode.  Just be careful that you don't accidentally do a normal Windows install and accidentally your old Windows install.  It's still there, it just needs the boot area fixed.

---

### Post by oldfred on 2016-02-29
Did you also delete Windows partitions, that you thought you maybe did not need?

Or if Windows is hibernated or fast start up on, you will not correctly see NTFS partitions in Linux.

Best to see details:
 Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)

If just uninstalling Ubuntu, you have to change UEFI to boot Windows first before removing Ubuntu partition. But you still should be able to go into UEFI and change it now.
And you need to remove the /EFI/ubuntu folder in the ESP - efi system partition and remove the ubuntu boot entry(s) in UEFI. UEFI saves in its NVRAM all boot options and may even add then back if in ESP.

      
 Really UEFI boot menu 
[http://askubuntu.com/questions/63610/how-do-i-remove-ubuntu-in-the-bios-boot-menu](http://askubuntu.com/questions/63610/how-do-i-remove-ubuntu-in-the-bios-boot-menu)

---

