---
title: "Making multiple uses of mass storage: Windows and Linux"
date: 2015-08-21
forum: General Help
---

### Post by jerry49 on 2015-08-21
I purchased a 1.5T Western Digital USB hard drive.  The main purpose is to save Images of Windows 7 and Windows 8.1 before I take advantage of the Windows 10 update.  
Facts as I understand or don't.
1) Windows Image requires NTFS format, Windows Backup works with FAT32... tried to image on a Flash Drive, would not as not NTFS.
2) I have made backup, transfer, Image of Windows 7, as well as a wide based folder savings of my selection from my W7 computer.  
3) I am considering making partitions, and believe that will make the HDD appear as multiple storage devices to both Windows and Linus (Ubuntu and Xubuntu are my current selections)
4) Here' a possible partition family:  150 GB for W7 and related already stored on the HDD before any partitioning is done (including Image and Backup capabilities), 200 GB for future work on a Windows 8.1 for similar uses, 50 GB for an XP machine.  This leaves (minus a few GB overhead from Western Digital which may best be on its own partition). This done there is still over 1T of storage capacity.  I plan to make several more partitions in the 100 GB size range.
5) A purpose for the unassigned partitions is use by Ubuntu.  I believe I can plug the mass storage device into a USB on a computer currently running Windows XP and using an ISO Xubuntu DVD install Xubuntu on one of the unassigned partitions.  First, I assume Xubuntu will reformate only the partition is as been assigned.  Other partitions will remain NTFS until changed by some other action/need.
6) If step 5 works, I plan to run the XP machine in either XP, regular boot, nothing done to change the boot loader, or I can plug the mass storage with Xubunto into the USB  and if selected before the internal HDD Xubuntu will be loaded into RAM.  Further, the mass storage is read/write so it can/will carry over user data across boot cycles. I have already received some help on the question of running Ubuntu from a USB storage.  

I think the fundamental unknown to me, following above my lack of experience in partitioning an HDD, is can I have a single physical device with different file formats on different partitions of a single physical device.

---

### Post by SeijiSensei on 2015-08-21
The answer to your basic question is yes, every partition can and often does have different types of file systems. However I wouldn't try booting from a USB drive, though I suppose it's possible as long as you let grub install itself on the primary drive.  Perhaps someone else here can speak to that.

My current hard drive has partitions with ext2, ext4, and NTFS.  I've also had some with other types of filesystems included like XFS and FAT32.

---

