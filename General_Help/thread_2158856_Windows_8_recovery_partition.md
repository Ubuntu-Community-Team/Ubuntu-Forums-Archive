---
title: "Windows 8 recovery partition"
date: 2013-06-30
forum: General Help
---

### Post by ericwwheeler on 2013-06-30
After disabling fastboot, secureboot, and other nefarious bs in the bios of my Asus k55a I managed to get Ubuntu 12.04 installed. However Windows 8 didn't survive the process. I originally wanted to dual boot. Now that I have Ubuntu installed and only have the recovery partition of Windows 8 left, I would like to make a bootable usb from that recovery partition. My problem is that I can only find tutorials on how to do this from within Windows and this is not longer an option. Is there a way to create a bootable usb of Windows 8 from my recovery partition using Ubuntu or a livecd? I need Doze for GoToMeetng and Turbotax-and figured I would just run it in Virtualbox. I feel my Google Ninja skills are lacking to find the right howto:confused:

---

### Post by fantab on 2013-06-30
It is not uncommon for Windows 8 to not boot after installing Ubuntu. To fix this you can use '[Boot-Repair]("https://help.ubuntu.com/community/Boot-Repair")' utility.

> Windows 8 didn't survive the process. I originally wanted to dual boot.  Now that I have Ubuntu installed and only have the recovery partition of  Windows 8 left,

Now, this is a tricky part.
Did you erase/delete/format the Windows8 Partition? Its important you tell us how you installed Ubuntu. Did you use the option 'Replace Windows', or 'Alongside Windows' or 'Something Else'?

If you formatted/deleted windows partition then it may be possible to recover that partition but its improbable that you may recover all the files/data on it. Its worth a try considering the other option. You can have a look at [http://www.minitool-partitionrecovery.com/](http://www.minitool-partitionrecovery.com/) (You will have to buy a licence to recover your partition).

The other option will be to re-install Windows 8 (as the recovery partition may not work). You can contact Asus and tell them that you accidentally deleted/formatted Windows8 partition and that you cannot recover it. They may offer you a better solution.

Once you get your Windows back, then you can re-install ubuntu carefully without affecting your Windows.

My two cents....

---

### Post by oldfred on 2013-07-01
Depends on how much you overwrote.

Some have UEFI entries to directly boot into recover. But if you erased efi partition also then those are gone also.

If you go into UEFI and look at its boot menu, is a recovery boot an option?

---

### Post by ericwwheeler on 2013-07-01
> **fantab said:**
> It is not uncommon for Windows 8 to not boot after installing Ubuntu. To fix this you can use '[Boot-Repair]("https://help.ubuntu.com/community/Boot-Repair")' utility.



Now, this is a tricky part.
Did you erase/delete/format the Windows8 Partition? Its important you tell us how you installed Ubuntu. Did you use the option 'Replace Windows', or 'Alongside Windows' or 'Something Else'?

If you formatted/deleted windows partition then it may be possible to recover that partition but its improbable that you may recover all the files/data on it. Its worth a try considering the other option. You can have a look at [http://www.minitool-partitionrecovery.com/](http://www.minitool-partitionrecovery.com/) (You will have to buy a licence to recover your partition).

The other option will be to re-install Windows 8 (as the recovery partition may not work). You can contact Asus and tell them that you accidentally deleted/formatted Windows8 partition and that you cannot recover it. They may offer you a better solution.

Once you get your Windows back, then you can re-install ubuntu carefully without affecting your Windows.

My two cents....

I can assure you when I said Windows 8 didn't survive-the whole install is gone. I tried all of the above and tried the Windows utilities, etc, etc. I will have to try copying the contents of the partition and then make it an iso-Will report back

---

### Post by ericwwheeler on 2013-07-01
> **oldfred said:**
> Depends on how much you overwrote.

Some have UEFI entries to directly boot into recover. But if you erased efi partition also then those are gone also.

If you go into UEFI and look at its boot menu, is a recovery boot an option?

I'm not sure where the UEFI is located. I did upload a picture of the files in the Recovery Partition that I am trying to use to make an install disk for Windows 8.

---

### Post by oldfred on 2013-07-01
You have an efi folder which should have efi boot files. But UEFI only boots from the efi partition which then has to have the efi boot files. 

Run this, it should show all efi bootable files. Or you may have to manually copy files from efi recovery into efi partition, but I am not sure of entire path. Some boot scripts show lots of boot files in efi partition and other show the separate partition with boot files, but I have not seen how they boot. System may copy file or set which partition is efi for recovery?

See post #4 in this thread. If you do not have the same entries copy efi files from recovery into efi partition.
[http://ubuntuforums.org/showthread.php?t=2088499](http://ubuntuforums.org/showthread.php?t=2088499)
 Asus x55u UEFI change to BIOS
[http://www.canbike.ca/information-technology/2013/03/12/asus-uefi-boot-from-cd-dvd-x55u.html](http://www.canbike.ca/information-technology/2013/03/12/asus-uefi-boot-from-cd-dvd-x55u.html)



       Post the link to the BootInfo report that this creates. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.
LighterWeight (Lubuntu based) Boot-RepairCD
[http://sourceforge.net/projects/boot-repair-cd/files/](http://sourceforge.net/projects/boot-repair-cd/files/)
Full Ubuntu 13.04 liveDVD or USB Install with Boot-Repair included (for newer computers) 
[https://help.ubuntu.com/community/LinuxSecureRemix](https://help.ubuntu.com/community/LinuxSecureRemix)

---

### Post by ericwwheeler on 2013-07-02
Okay, I did the boot-info from the live-cd and the info is at [http://paste.ubuntu.com/5835093](http://paste.ubuntu.com/5835093)

---

### Post by fantab on 2013-07-02
> 
=================== parted -l:  
Model: ATA ST750LM022 HN-M7 (scsi) 
Disk /dev/sda: 750GB 
Sector size (logical/physical): 512B/4096B 
**Partition Table: gpt  **

Number  Start   End    Size    File system     Name                  Flags 
3      17.4kB  315MB  315MB   **fat32                                 boot** 
2      316MB   945MB  629MB   ntfs            Basic data partition  hidden, diag 
1      945MB   741GB  740GB   ext4 
4      741GB   750GB  9211MB  linux-swap(v1)

The fat32 partition is your efi partition. And yes you seem to have erased Windows8 partition. If you want to get back your Win8 then contact the manufacturer Service to reinstall. I am not sure if partition recovery will work, you can try using the tool recommended in post #2.

Good Luck...

---

### Post by oldfred on 2013-07-02
I cannot tell by the size which recovery you have. Both Windows and the vendor call partitions recovery. 

The Windows recovery is a repair partition with Windows repair tools. 
The vendor recovery is an image of hard drive to allow restore to as purchased.

The files you posted before seem to be vendor related, but you have no vendor boot files in the efi partition as it is just grub's version.

---

### Post by ericwwheeler on 2013-07-02
I called Asus and they can sell a Recovery DVD for God knows how much. They also cannot or will not provide me with my Windows 8 product key saying I need to contact Microsoft for the key. I downloaded and installed Windows 8.1 developer version with their developer key and then reinstalled Ubuntu 12.04 in a dual boot situation. However when I called Microsoft to get my original Windows 8 key they told me that Asus is required to provide that (and they claim Microsoft had them embed the key in the files in the Recovery Partition-which are not viewable) Needless to say I will NEVER purchase another Asus product. I guess it will all come to a head when the developer trial is up and they ask me to purchase Windows 8.1 then I'll get to make the Asus/Microsoft round of calls again. All of this to have a choice of which OS I want to run on my hardware-that I purchased. I had no idea secureboot, fastboot, etc. was going to be such a pain in the *ss! Should have known

---

### Post by oldfred on 2013-07-02
If you install with UEFI, it should automatically add the product key.

 Product key now in UEFI/BIOS
[http://reviews.cnet.com/8301-33642_7-57554240-292/windows-8-moves-to-bios-based-product-keys/](http://reviews.cnet.com/8301-33642_7-57554240-292/windows-8-moves-to-bios-based-product-keys/)
[http://answers.microsoft.com/en-us/windows/forum/windows_8-windows_install/bipass-uefi-provided-product-key-to-install/a271067b-d655-4b46-8b52-b3f191b9370c](http://answers.microsoft.com/en-us/windows/forum/windows_8-windows_install/bipass-uefi-provided-product-key-to-install/a271067b-d655-4b46-8b52-b3f191b9370c)

---

### Post by fantab on 2013-07-03
If I need Windows8 then I think I would consider buying OEM 'Recovery DVD'. Its not just ASUS all OEMs sell recovery media for a price AFAIK.

And yes your product key will be in the OEM recovery partition or efi partition, I am not sure where exactly. 

This is why we always strongly recommend good Backup of your Windows partitions before you venture out to dual boot with any OS.

If you let me then I would suggest that you do consider buying that 'recovery DVD'. 

Good Luck.

---

