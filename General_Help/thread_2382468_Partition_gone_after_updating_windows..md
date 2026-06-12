---
title: "Partition gone after updating windows."
date: 2018-01-13
forum: General Help
---

### Post by FCNBYwP on 2018-01-13
Hi there, 

I had Windows and Ubuntu together installed and after windows automatic updates, the Partition where I had ubuntu installed was gone ! even when I use the live boot of Gparted is not detected anymore. Please let me know if it is possible to restore my lost Partition.

Regards,

---

### Post by TheFu on 2018-01-14
Perhaps contacting MSFT for this issue would be a good idea?

---

### Post by FCNBYwP on 2018-01-14
> **TheFu said:**
> Perhaps contacting MSFT for this issue would be a good idea?

I will do that now thank you for bringing that into my attention, but  for the time being I would like to have an answer for my problem.
Thnx again.

---

### Post by RobGoss on 2018-01-14
Did you make any changes to your Linux partition in any way shape of form? I've never heard of Windows just wiping out a Linux partition from just updating the system that is very odd

What version of Windows do you have installed?

---

### Post by TheFu on 2018-01-14
> **FCNBYwP said:**
> I will do that now thank you for bringing that into my attention, but  for the time being I would like to have an answer for my problem.
Thnx again.

The answer is "maybe" - it depends on what was actually done.  

If you can please post the cmd and output of **lsblk** and **sudo parted -l** run from a live-boot linux (CD/DVD/Flash drive) running some version of Linux/gparted, we'd get an idea of how much trouble there really is.

Having a backup of whatever has been lost would make things much easier.

But really, if it was MS-Windows patching that caused the problem, then MSFT will be the best source for data around
* what they did
* what can be done to correct it
* how to prevent it from happening again.

BTW, I've had Linux removed from the grub menu on a dual-boot Windows/Ubuntu system before.  It happened about once a year, whenever MSFT decided to fix their boot manager.  That would overwrite the current boot-manager and ignore non-MSFT OS installations.  It did not alter the partitions or delete any partitions. It just didn't put my linux OS installs into the boot menu.  Reinstalling grub into the MBR fixed it. It was a slight hassle.

If the partitions really have been removed, then somehow, the former layout needs to be know to be put back.  Part of my nightly versioned backups captures the partition layout (sudo parted -lm) in a file, for just this reason.

---

### Post by oldfred on 2018-01-14
Microsoft has had this bug for years. Windows 7 reinstalls, Windows 8 installs, updates and now Windows 10 updates or installs.
It does not write Linux partitions if system is BIOS/MBR and you have logical Linux partitions.

So you know sectors:
sudo parted /dev/sda unit s print

 backup partition table before any changes, so you can get back to current if changes not correct
sudo sfdisk -d /dev/sda > PT_sda.txt
  
Both parted rescue & testdisk have worked. Some now find if only one partition parted rescue seems a bit easier.
      
 [SOLVED] Windows 10 update, Stuck in grub rescue 
[https://ubuntuforums.org/showthread.php?t=2373061](https://ubuntuforums.org/showthread.php?t=2373061)
[http://askubuntu.com/questions/654386/windows-10-upgrade-lead-into-grub-rescue/655080#655080](http://askubuntu.com/questions/654386/windows-10-upgrade-lead-into-grub-rescue/655080#655080)
Windows 7 to Windows 10 MBR partition missing
[http://ubuntuforums.org/showthread.php?t=2288988](http://ubuntuforums.org/showthread.php?t=2288988)
[http://ubuntuforums.org/showthread.php?t=2290190](http://ubuntuforums.org/showthread.php?t=2290190)
[http://ubuntuforums.org/showthread.php?t=2292545](http://ubuntuforums.org/showthread.php?t=2292545)
Use parted rescue to restore missing partition details in post #22
[http://ubuntuforums.org/showthread.php?t=1775331](http://ubuntuforums.org/showthread.php?t=1775331)
[http://www.gnu.org/software/parted/manual/html_node/rescue.html](http://www.gnu.org/software/parted/manual/html_node/rescue.html)
[http://gparted.sourceforge.net/faq.php/#faq-22](http://gparted.sourceforge.net/faq.php/#faq-22)
Parted rescue seems easier than testdisk
[http://askubuntu.com/questions/665445/upgraded-to-windows-10-on-dual-boot-and-cant-boot-to-ubuntu-partition/665462](http://askubuntu.com/questions/665445/upgraded-to-windows-10-on-dual-boot-and-cant-boot-to-ubuntu-partition/665462)

---

### Post by yancek on 2018-01-14
There are a number of threads here at the forum with this exact problem.  Some windows (usually 8 or 10) updates modify the partition table and don't include any non-windows partitions in the new table.  This can usually be seen by running fdisk -l and looking at the begin sector and end sector of the output to find the missing partition.   I saw a post here a day or two ago with a proposed solution but haven't bookmarked it so you might try using the Search function here to find similar threads.

I seriously doubt you will get any help from microsoft but no harm in trying.

---

### Post by FCNBYwP on 2018-01-14
After windows finished upgrading the boot was corrupted and I used Boot repair from a ubuntu Live cd, but only windows was fixed ubuntu was gone, I reinstalled ubuntu from scratch and replaced it with windows I was surprised to see that only one partition is available and it is the one I had Windows installed on it. 
My HDD was 250 GB.

 ibrahim@ibrahim-HP-EliteBook-2540p:~$ lsblk
NAME   MAJ:MIN RM   SIZE RO TYPE MOUNTPOINT
loop1    7:1    0 135,5M  1 loop /snap/gimp/30
sr0     11:0    1  1024M  0 rom  
loop0    7:0    0  83,8M  1 loop /snap/core/3748
sda      8:0    0 149,1G  0 disk 
&#9500;&#9472;sda2   8:2    0     1K  0 part 
&#9500;&#9472;sda5   8:5    0   3,8G  0 part [SWAP]
&#9492;&#9472;sda1   8:1    0 145,3G  0 part /

ibrahim@ibrahim-HP-EliteBook-2540p:~$ sudo parted -l
[sudo] Passwort für ibrahim: 
Modell: ATA TOSHIBA MK1633GS (scsi)
Festplatte  /dev/sda:  160GB
Sektorgröße (logisch/physisch): 512B/512B
Partitionstabelle: msdos
Disk-Flags: 

Nummer  Anfang  Ende   Größe   Typ       Dateisystem     Flags
 1      1049kB  156GB  156GB   primary   ext4            boot
 2      156GB   160GB  4077MB  extended
 5      156GB   160GB  4077MB  logical   linux-swap(v1)

---

### Post by FCNBYwP on 2018-01-14
I didn't change anything, after windows finished upgrading the boot was corrupted and I used  Boot repair from a ubuntu Live cd, but only windows was fixed ubuntu was  gone, I reinstalled ubuntu from scratch and replaced it with windows I  was surprised to see that only one partition is available and it is the  one I had Windows installed on it. Gparted was unable to detect the missing partition.

---

### Post by oldfred on 2018-01-14
If sda is your only drive, you know only have Ubuntu installed.

When you  install any system and tell it to use entire drive, nothing else is saved.

Always best to install Windows first if re-installing.

Windows in BIOS mode only installs to a NTFS primary partition with the boot flag. Or it may install if a primary partition is available and you have enough unallocated space, but not what if then it keeps your Linux partition  or not.

There is nothing to fix, now. You have over installed Ubuntu on entire drive.

---

### Post by FCNBYwP on 2018-01-14
> **oldfred said:**
> If sda is your only drive, you know only have Ubuntu installed.

When you  install any system and tell it to use entire drive, nothing else is saved.

Always best to install Windows first if re-installing.

Windows in BIOS mode only installs to a NTFS primary partition with the boot flag. Or it may install if a primary partition is available and you have enough unallocated space, but not what if then it keeps your Linux partition  or not.

There is nothing to fix, now. You have over installed Ubuntu on entire drive.


I had 250 GB but after this problem I only have the 160 GB left, so the other partition is gone and I would like to have it back, not detected using Gparted or any another software!

---

### Post by TheFu on 2018-01-14
> **FCNBYwP said:**
> I had 250 GB but after this problem I only have the 160 GB left, so the other partition is gone and I would like to have it back, not detected using Gparted or any another software!

I looked up the characteristics of that drive model, TOSHIBA MK1633GS.  It is a 160GB 5400 RPM HDD.  Don't know what happened to the 250G you had before, but short of swapping a physical disk, I don't see how a 160G HDD could be a 250G HDD.

Regardless, it appears that MS-Windows is gone now.

---

