---
title: "Making a DOS partition after uninstalling Ubuntu"
date: 2007-10-24
forum: General Help
---

### Post by gperk on 2007-10-24
Hi,
After installing Ubuntu I have decided to put it on another computer and want to restore Windows ME for the owner of the computer. I have created new dos partitions but the HP recovery CD says the media is not recognized or something like that. 
I know that linux is capeable of creating DOS partitions but I have already uninstalled it. 
Is there a bootable linux floppy I can download, boot off of and format a partion in fat32? 
Can anyone suggest anything else? 
I remember seeing something about a low level format when installing Ubuntu - did it really do that? 
Thanks very much for any help on this. 
Greg

---

### Post by Zackariah on 2007-10-25
Run this through WINE or on a Windows PC with a blank floppy disk, the best way for Windows to recognise a fat32 partition is for it to create one it's self, i've problems myself with Windows not accepting Linux created fat32 partitions.

Insert into the ME computer and boot from it, when booted type FDISK, hit enter and follow the on-screen instructions to delete all partitions on the drive, and then recreate a Primary DOS parition, restart the PC with the floppy still in the drive and type "format C:", hit enter and wait for it to finish, take out the floppy disk and restart the computer with the HP restore disk, hopefully this will work.
[HTML]http://www.dehning.com/download/utilities/bootdisks/boot98.exe[/HTML]

---

### Post by gperk on 2007-10-25
Hi, 
Thanks a lot for the reply. After two hours in chat sessions with HP support, they suggested trying to boot and install any other MS OS. So I tried with W2000 and it was able to recognize that the disk was not  fat or ntfs and do the formating in fat 32 for ME. Then I interrupted the 2000 installation and the ME disk was able to run. 
Thanks again, 
Greg

---

