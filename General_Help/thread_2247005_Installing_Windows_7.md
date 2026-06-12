---
title: "Installing Windows 7"
date: 2014-10-04
forum: General Help
---

### Post by wyattwhiteeagle on 2014-10-04
When I installed Ubuntu 14.04 lts, I had the option to install along-side of Windows 7 Premium Home 64 bit. However, when I clicked to install along-side of Windows it told me there was not enough disk space; so I did a full install.

After running a few times, I learned that ubuntu doesnt support windows program install files and "*.exe" files unless you have wine and winetricks.

My issue is this...the windows program files and exe files are very unstable in wine and end up malfunctioning causing me to completely restart my system just to restart my comp due to repeat malfunctions.

Truth be told, I want my Windows 7 back...I could care less about my old files i had on Windows 7 before.

Will somebody please help me. I have a windows 7 image of install files on a flashdrive but im getting error messages like "not enough free disk space" and when i reboot ubuntu i clear up over a gig of space but the windows 7 install doesnt recognize that i had even cleared enough space to do the install. 

Another error i get is "required partition missing" and when it asks for the "volume label"?

I'm at a loss here...Please help me

---

### Post by QIII on 2014-10-04
Hello!

Do you want *only *Windows or are you still interested in dual booting?

---

### Post by wyattwhiteeagle on 2014-10-05
> **QIII said:**
> Hello!

Do you want *only *Windows or are you still interested in dual booting?

dual booting would be great :)

---

### Post by oldfred on 2014-10-05
Not sure exactly where you are at. The standard Windows installer for BIOS type installs on MBR(msdos) partitioned drives has to see a primary partition formatted NTFS with the boot flag. It will install in one NTFS partition although default install to a blank drive uses a 100MB boot partition and the main install.
If you have more than one drive make sure you have set BIOS to boot from Windows drive or it may install its 100MB boot partition to the BIOS boot drive and just overwrite what is there.

Do not make NTFS partition after an extended partition, but it can be any primary partition not just sda1. Windows does like to just erase the Linux partitions when it writes a new partition table. Best to back up partition table and you will need a working Live installer of Ubuntu to reinstall grub to MBR as Windows will install its boot loader.

After finalizing partitions but before Windows install backup partition table. Do not restore if you later change partitions. You may be able to recover missing partitions with testdisk but better to have backup.
 Backup partition table structure to text file & save to external device.
sudo sfdisk -d /dev/sda > PTsda.txt

 How to restore the Ubuntu/XP/Vista/7 bootloader 
[https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader](https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader)
[https://help.ubuntu.com/community/Grub2/Installing#Fixing_a_Broken_System](https://help.ubuntu.com/community/Grub2/Installing#Fixing_a_Broken_System)

And of course any major system change has some risk. So good backups are required.

---

### Post by wyattwhiteeagle on 2014-10-05
Looking at the info and links above, is it more simple and less confusing to just go Windows 7 only? If so, what are the simplest steps to install Windows 7?

---

### Post by Impavidus on 2014-10-05
> **wyattwhiteeagle said:**
> Will somebody please help me. I have a windows 7 image of install files on a flashdrive but im getting error messages like "not enough free disk space" and when i reboot ubuntu i clear up over a gig of space but the windows 7 install doesnt recognize that i had even cleared enough space to do the install.
Keep in mind there is a difference between "free space" and "unallocated space". Free space on a file system is space on your hard disk that has been allocated to a partition, but is currently unused by any files. This free space is available to store files. When you booted Ubuntu and cleared over a GB of space, this is the free space you got.

Unallocated space on the other hand is hard disk space that hasn't been allocated to any partition. It is not available for storing files and is not reported by your file manager or most other tools, but only by disk partitioning tools.

When the installer of an operating system (both Ubuntu and Windows) wants free space, that must be a continuous block of unallocated space.

Installing Ubuntu and then adding Windows isn't really easy. First installing Windows and then adding Ubuntu is easier. For now you can use the live disk you used for installing Ubuntu and boot from it. Open a program called gparted and use it to delete all partitions from your hard drive. This will erase all your files, so make sure you have them backed up. Then Windows should be willing to install. If you later decide you want to try Ubuntu again, use the Windows partitioning tool to make unallocated space (at least about 20GB) at the end of the drive. The Ubuntu installer can use that space.

---

### Post by MartyBuntu on 2014-10-05
What are the specs of your computer? How big is the hard drive?

---

### Post by buzzingrobot on 2014-10-05
> **wyattwhiteeagle said:**
> Looking at the info and links above, is it more simple and less confusing to just go Windows 7 only? If so, what are the simplest steps to install Windows 7?

Believe if you just delete all partitions that are on the disk and boot the Windows install image, you can select the unallocated space (which would be the entire drive), select  "New" and the Windows installer will be happy.

To delete the partitions, boot into a live Ubuntu image, choose the "Try" option, and run GParted. If the machine only has one drive, it will be designated /dev/sda.  Make sure you've selected it (upper right corner). Right click on the partition(s), select the delete option, and, then click the checkmark in the menubar to apply your choices.

Reboot, being sure to remove the DVD/USB. You should boot up to a blank screen, very likely with a grub bootloader error message. (Windows will overwrite this with its own bootloader.)

Insert or attach the Windows install image, boot, and the Windows installer should run.

---

### Post by wyattwhiteeagle on 2014-10-05
> **Impavidus said:**
> Open a program called gparted and use it to delete all partitions from your hard drive. This will erase all your files, so make sure you have them backed up. Then Windows should be willing to install.

gparted...hmmm...is there an easy to understand step-by-step guide on how to use gparted?


> **MartyBuntu said:**
> What are the specs of your computer? How big is the hard drive?

It's a HP 2000 notebook with a 500GB 5400RPM) hard drive

---

### Post by buzzingrobot on 2014-10-05
Here's the Gparted site: [http://gparted.org/](http://gparted.org/). (It's in the repos.) I'm sure there are posts about gparted scattered here in the forums and elsewhere on the net.  It's a partition editor.

As you can see by the image shown on the gparted site (click it to expand it), it lists the partitions on your drive(s). In Linux, a designation like "/dev/sda" identifies a drive, while a designation like "/dev/sda1" identifies a partition on a drive. The distinction is important. In the upper right of GParted's display is a menu to select the drive.  In a one-drive machine, it will be /dev/sda.  An attached USB and/or the DVD drive may also be listed as /dev/sdb, etc.

The partitions on the selected drive are listed. Highlight a partition, then click through the menu listings to see the options. Right clicking on a selected partition also pops up options. You want to highlight the partitions on your drive, select "Delete" for each in turn. Click the checkmark in the menubar and GParted will run the actions you've selected, e.g., delete partitions. (Nothing happens until you click that checkmark.) You want to end with a single "unallocated" item.

Operating systems typically won't see partition changes until after a reboot, hence the need to reboot to make sure the deletions worked.

---

### Post by Sef on 2014-10-05
Before attempting this dual boot, **back up**&#8203; your os first.

---

### Post by yancek on 2014-10-05
The link below has a very detailed tutorial on GParted with a Table of Contents so you can go to any section you need.

[http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html)

---

