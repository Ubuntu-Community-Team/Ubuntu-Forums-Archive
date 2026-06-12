---
title: "Bricked kubuntu, live usb wont allow me to access files to backup"
date: 2024-02-16
forum: General Help
---

### Post by aloneandconfused on 2024-02-16
**Background (using kubuntu 22.04)**
I got some bad instructions online about the rm command (that it requires -f or -r to remove directories with files, which in my case it didnt) and i ended up deleting the bin and sbin folders without noticing, which bricked the OS, it wont boot, even into recovery mode. Trying search engines and asking ai bots for an answer just gives me solutions that give more errors. Im trying to reinstall the OS using kubuntus live usb without risking any of my files. Because of all the warnings about it deleting everything if the settings arent perfect i am first trying to get to my files to back them up. The live usb mounts my disk, but i cant access the home/user directory with all my files. It has a lock icon on it and doesnt ask for any password when i click on it. I have tried mounting it but its already mounted. Ive tried running the file manager as sudo but kubuntu wont allow it. My user account has a password but it is not encrypted. 
How can i access my files? On [https://help.ubuntu.com/community/LiveCdRecovery](https://help.ubuntu.com/community/LiveCdRecovery), it gives these instructions:
[FONT=inherit]sudo mount /dev/sda1 /mnt[/FONT]


[FONT=Verdana, Arial, Tahoma, Calibri, Geneva, sans-serif]Which gives the error "NTFS signature is missing". This drive is an EXT4 formatted drive, it has never been NTFS and theres no windows partitions on it. If i run "sudo fdisk -l", it gives me /dev/sda1 BIOS boot, /dev/sda2 EFI system, /dev/sda3 Linux LVM. There is nothing that says NTFS/FAT/EXFAT.  As previously stated, searching that error message gives alot of suggestions that end in more error messages. [/FONT][FONT=Verdana, Arial, Tahoma, Calibri, Geneva, sans-serif]

[/FONT]
[FONT=inherit]
[/FONT]
Perhaps this isnt necessary if i can just reinstall the OS files safely, what settings do i have to do in kunbuntu live usb installation to reinstall the OS and leave my files alone? 
If i use the guided option the 'next button' becomes 'install now', which makes it sound like its just going to wipe everything without asking.
If i use the manual option, it lists the entire disk, and under "format?" it is unchecked. The 'next button' becomes 'install now', is that all i have to do?

---

### Post by oldfred on 2024-02-16
The BIOS boot partition or bios_grub your sda1 is unformatted space used by grub for very old BIOS installs using newer gpt partitioning. You cannot mount it.
The ESP is FAT32 and required for UEFI boot, your sda2.
You typically only have one or the other UEFI or BIOS and then have system set to boot in that mode.
Which way did you install, or did you install a second time in other boot mode to get both versions. But only last install will work and system then has to be set to boot in that mode.
If UEFI system, better to be UEFI install.

Mount LVM - duckhook
[https://ubuntuforums.org/showthread.php?t=2383017&p=13733372#post13733372](https://ubuntuforums.org/showthread.php?t=2383017&p=13733372#post13733372)
[https://unix.stackexchange.com/questions/339011/how-do-i-mount-an-lvm-partition/339621#339621](https://unix.stackexchange.com/questions/339011/how-do-i-mount-an-lvm-partition/339621#339621)
For mounting encrypted see first few lines:
[https://askubuntu.com/questions/262211/how-do-i-resize-an-encrypted-lvm-to-install-another-copy-of-ubuntu](https://askubuntu.com/questions/262211/how-do-i-resize-an-encrypted-lvm-to-install-another-copy-of-ubuntu)

---

### Post by aloneandconfused on 2024-02-16
This answer was not helpful at all

---

### Post by yancek on 2024-02-17
If you ran the fdisk command, why did you not post the actual output?  You indicate that you get an error when you try to mount sda1 yet you indicate that it is a BIOS_Boot partition.  That partition is tiny which you can see in the fdisk output and absolutely does not contain any personal data.  The sda2 partition according to your post, is an EFI partition which contains only boot files and no personal data and is a windows (vfat) filesystem.  There are a number of reasons for the error message but we don't have enough information to do more than guess at it.

Since you chose to install using LVM, you should be familiar with it but if not, I guess you need to read through the first two links in the post above by oldfred regarding LVM.  Don't use it myself so have no suggestions.  Ordinarily when using a 'live' Linux system, a user would not have any problem accessing to read a Linux filesystem on an internal drive which would allow a user to copy data FROM that drive but not TO it.  Not sure why your are having a problem but again, you have chosen to use LVM and I don't use it.

Reinstalling would be simpler if you had created a separate partition for your /home/user directory.  You could then reinstall to the / filesystem partition and choose NOT to format the /home partition.  Since you have deleted significant files in the /bin and /sbin directory, you might have been able to reinstall the / filesystem to its partition and chosen not to format that partition and it should have reinstalled the proper directories and files and make the system usable.  I would not suggest this although I have done it successfully myself but again, I don't know what would happen with an LVM install.

---

