---
title: "SD Card/USB Drive Permissions Issue!!"
date: 2018-11-10
forum: General Help
---

### Post by alethri on 2018-11-10
I'm having a very annoying issue with SD cards/USB drives formatted on Ubuntu. When inserted into any other device the file system and files are read-only, and therefore in any other device besides my Ubuntu laptop they CANNOT create any new files or write anything new to the SD card/USB drive. When I've tried changing the permissions in Ubuntu for either the username group or "Others", it instantly switches back to "access files" or "read only", even when done with root access!!!! Even "Change Permissions for Enclosed Files" doesn't work, whether under the normal account or sudo. I just cannot change the contents or SD card itself to be anything other than read-only in other devices! 
I've tried a LOT of things suggested by Google searches, but absolutely nothing works. Chmod does absolutely nothing, even though the command seems to work fine.
This is driving me completely nuts and I have tried very hard to figure it out on my own. Ubuntu simply won't let me change the permissions. PLEASE suggest any ideas!!!!


Thank you!!

---

### Post by sudodus on 2018-11-10
- What  file systems are there in your SD cards and USB drives (for example Linux ext4 or Microsoft FAT32, NTFS or exFAT)?

- Which version of Windows or MacOS are you running? Are you running some other linux distro beside Ubuntu?

- What do you mean by other device? Do you mean computer, camera, smartphone ... ?

- Could it be that the computer with Ubuntu has some non-standard USB hardware? Maybe  things would be compatible, if you format the SD cards and USB drives in another computer (for example when booted from a live USB drive with Ubuntu)?

[hr][/hr]
I hope the following links can help you solve the problem (of compatibility both ways between operating systems).

[Postrequisites - restore the USB stick](https://help.ubuntu.com/community/Installation/FromUSBStick#Postrequisites_-_restore_the_USB_stick)

[Full compatibility with Linux, Windows and MacOS](https://askubuntu.com/questions/952673/how-do-i-copy-a-file-larger-than-4gb-to-a-usb-flash-drive/952706#952706) - Maybe you can try the UDF file system.

[Can't format my usb drive. I have already tried with mkdosfs and gparted](https://askubuntu.com/questions/144852/cant-format-my-usb-drive-i-have-already-tried-with-mkdosfs-and-gparted/933035#933035)

[Mount NTFS partition in a USB drive with custom permissions and owner](https://askubuntu.com/questions/11840/how-do-i-use-chmod-on-an-ntfs-or-fat32-partition/956072#956072)

---

### Post by trivanks on 2018-11-10
Install GParted Insert the SD Card or USB key. Now launch GParted. for using this tools to format the sd card... 

for example, follow the images

[https://itsfoss.com/wp-content/uploads/2012/12/GParted-Format-USB-Disk-Ubuntu-1.jpeg](https://itsfoss.com/wp-content/uploads/2012/12/GParted-Format-USB-Disk-Ubuntu-1.jpeg)

[https://itsfoss.com/wp-content/uploads/2012/12/GParted-Format-Disk-USB-Ubuntu-3.jpeg](https://itsfoss.com/wp-content/uploads/2012/12/GParted-Format-Disk-USB-Ubuntu-3.jpeg)

[https://itsfoss.com/wp-content/uploads/2012/12/GParted-Format-Disk-USB-Ubuntu-4.jpeg](https://itsfoss.com/wp-content/uploads/2012/12/GParted-Format-Disk-USB-Ubuntu-4.jpeg)

[https://itsfoss.com/wp-content/uploads/2012/12/GParted-Format-Disk-USB-Ubuntu-5.jpeg](https://itsfoss.com/wp-content/uploads/2012/12/GParted-Format-Disk-USB-Ubuntu-5.jpeg)

[https://itsfoss.com/wp-content/uploads/2012/12/GParted-Format-Disk-USB-Ubuntu-6.jpeg](https://itsfoss.com/wp-content/uploads/2012/12/GParted-Format-Disk-USB-Ubuntu-6.jpeg)

---

### Post by ajgreeny on 2018-11-10
Please do not add large images inline as you did; users on small screens or phones, and those with limited network bandwidth will find it a problem to load those pages.

You should use the attachment facility, a paperclip, in the Reply to Thread toolbar which then adds thumbnails to the thread which readers can choose not to open if they are a problem.

---

