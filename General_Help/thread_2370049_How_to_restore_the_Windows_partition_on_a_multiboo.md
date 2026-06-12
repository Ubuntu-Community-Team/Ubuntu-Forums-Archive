---
title: "How to restore the Windows partition on a multiboot system?"
date: 2017-08-30
forum: General Help
---

### Post by orthoducks on 2017-08-30
Until last night I had a test system that ran both Ubuntu and Windows 7. Then I accidentally deleted the first two partitions from the system disk (while trying to delete partitions from another disk). I found instructions for recovering a deleted partition with parted and tried to do that after booting from a live CD. Parted restored the first partition (GRUB) but didn't recognize the second one (Windows). So now I've got a disk with working GRUB and Ubuntu partitions, and a presumably intact but inaccessible Windows partition.

If I do a standard Windows installation, it will blow away GRUB. Then I'll have to reinstall Ubuntu, too. I might as well just wipe the disk. (I know it's theoretically possible to reinstall GRUB independently, but I've tried it before, and it was not a happy experience. Reinstalling Ubuntu would be easier.)

I've got three questions.

First, is there a way to recover the Windows partition that parted doesn't believe is there?

Second, if not, is there a way to reinstall Windows without blowing away GRUB?

Third, what are good ways to prevent this from happening again? I've looked for multi-boot backup solutions in the past, but the ones I found were unreasonably expensive or complex or both. My current plan is to clone the whole disk, run the clone, and keep the original as a backup.

---

### Post by wildmanne39 on 2017-08-30
*Thread moved to **General Help**.*

---

### Post by yancek on 2017-08-30
Windows has a restore option but that can only be used if you can boot windows.  You should be able to repair with the option on the windows install DVD or the Recovery CD but that re-sets to factory defaults and overwrites everything on the disk including Ubuntu.  Could you post the output of either/both of these commands:  sudo fdisk -l OR sudo parted -l  The output of these commands should show whether you still have windows partitions.  If you do show your windows partitions you could try running:  sudo update-grub if you have not done so yet.

If you deleted the first two partition on the drive with windows those were most likely the boot and system partitions for windows.  You might try using testdisk to try to recover but that won't be an easy task.
I don't believe there is any way to re-install windows and not overwrite Grub.

---

### Post by oldfred on 2017-08-30
Post this to see what parted/gparted currently sees:
       sudo parted /dev/sda unit s print 

Did you have any documentation on partitions & sizes from before.
Like Boot-Repair's summary report, bootinfoscript's report, or even partition table backup from sfdisk?

You can easily restore grub with Boot-Repair.
      
 How to restore the Ubuntu/XP/Vista/7/8/10 BIOS bootloader 
[https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader](https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader)
[https://help.ubuntu.com/community/Grub2/Installing#Fixing_a_Broken_System](https://help.ubuntu.com/community/Grub2/Installing#Fixing_a_Broken_System)

My one system with Windows, I do a full image backup of Windows with Macrium, and just backup my Ubuntu data, apps list & /home as I can easily reinstall Ubuntu.
 Backup windows before install - post by Mark Phelps
[http://ubuntuforums.org/showthread.php?t=2137439&p=12611710#post12611710](http://ubuntuforums.org/showthread.php?t=2137439&p=12611710#post12611710)
[http://www.macrium.com/reflectfree.asp](http://www.macrium.com/reflectfree.asp)
Many have posted clonezilla also works.

 [http://clonezilla.org/](http://clonezilla.org/)

---

### Post by orthoducks on 2017-08-30
Here's the current disk map from parted:

[FONT=courier new]Model: ATA WDC WD3200JS-55P (scsi)
Disk /dev/sda: 625142448s
Sector size (logical/physical): 512B/512B
Partition Table: msdos
Disk Flags: 

Number  Start       End         Size        Type      File system     Flags
 1      2048s       206846s     204799s     primary   ntfs
 3      167776256s  209717247s  41940992s   primary   ntfs
 4      209719294s  625141759s  415422466s  extended                  lba
 6      209719296s  616759295s  407040000s  logical   ext4
 5      616759296s  625141759s  8382464s    logical   linux-swap(v1)
[/FONT]
I don't have a record of the map from before the goof happened, but it's pretty easy to figure out. I deleted partitions 1 and 2, and parted restored partition 1. The hole between partition 1 and partition 3 was partition 2.

I'll look at the instructions for restoring grub, and see if they're more readable (and more useful) than the ones I tried to use the last time I faced a similar problem. But I think my next move will be to spend $40 for the paid version of MiniTool Partition Wizard, which will give me access to a bootable version. Since it's a Windows-centric tool, it may be better at recognizing a deleted Windows partition than parted was.

Thank you for the assistance. I probably won't return here for a few days because of the U.S. Labor Day holiday, but I'll be back after that.

---

### Post by oldfred on 2017-08-30
Have you tried parted rescue with the start as the last sector sector of sda1 and end as the start sector of sda3? Usually one or two sectors between partitions, so may be plus or minus a sector or two.

 Use parted rescue to restore missing partition details in post #22
[http://ubuntuforums.org/showthread.php?t=1775331](http://ubuntuforums.org/showthread.php?t=1775331)
[http://www.gnu.org/software/parted/manual/html_node/rescue.html](http://www.gnu.org/software/parted/manual/html_node/rescue.html)
[http://gparted.sourceforge.net/faq.php/#faq-22](http://gparted.sourceforge.net/faq.php/#faq-22)
Parted rescue seems easier than testdisk
[http://askubuntu.com/questions/665445/upgraded-to-windows-10-on-dual-boot-and-cant-boot-to-ubuntu-partition/665462](http://askubuntu.com/questions/665445/upgraded-to-windows-10-on-dual-boot-and-cant-boot-to-ubuntu-partition/665462)

---

