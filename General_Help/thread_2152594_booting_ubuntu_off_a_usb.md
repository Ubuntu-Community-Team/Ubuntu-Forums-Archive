---
title: "booting ubuntu off a usb"
date: 2013-06-08
forum: General Help
---

### Post by Hawkyrou on 2013-06-08
hi,

i have ubuntu on my usb to boot off but i am wondering will ubuntu save the files to the usb or will it save to my hard drive??

i would like it to save to the usb
if you could pls tell me how i would go about doing that

---

### Post by 2F4U on 2013-06-08
Which files are you talking about? By default, Ubuntu when run from USB doesn't save anything to either the hdd's or the USB drive. Only if you create the liveUSB with persistent option will you be able to save configuration changes or install applications permanently.

---

### Post by oldfred on 2013-06-08
How large is flash drive?
Persistence has limits on how much data you can save. You cannot update system, but can add some drivers. 
If you have a large flash drive a full install may be better.

 [https://help.ubuntu.com/community/LiveCD/Persistence](https://help.ubuntu.com/community/LiveCD/Persistence)
[https://wiki.ubuntu.com/LiveUsbPendrivePersistent](https://wiki.ubuntu.com/LiveUsbPendrivePersistent)

      
 Pros & cons of persistent install over direct install to flashdrives - C.S.Cameron
[http://ubuntuforums.org/showthread.php?t=2133067](http://ubuntuforums.org/showthread.php?t=2133067)
[http://ubuntuforums.org/showthread.php?t=1655412](http://ubuntuforums.org/showthread.php?t=1655412)

---

### Post by Hawkyrou on 2013-06-09
@2F4U any file that i make like if i make a text document

@oldfred the usb is 8 gb

i was also thinking if i got a 500gb hard drive that i can plug into my computer would i be able to fully install ubuntu into that???

(i am not very good with computers so sorry if i am being annoying)

---

### Post by oldfred on 2013-06-09
If 8GB and you only are saving a few files, then persistence should work.

I have a full install in 8GB, and then 8GB for data on a 16GB flash drive. An full install in 8GB does not have a lot of room but with some maintenance works.

If you can add a 500GB drive you will have lots of room for everything including the kitchen sink. :)

---

### Post by C.S.Cameron on 2013-06-09
Persistence size  is limited out of the box to 4GB due to the FAT32 file system.
You can replace the FAT32 casper-rw, (Persistence), file with a casper-rw partition of any  size, (ext2,3 or 4).

You can do a Full install to External HDD and take your O/S with you, Following is a step by step for external drive.
(You can also do this on an 8GB flash drive using smaller partitions).
All partitions except / are optional:

Turn off and unplug the computer. (See note at bottom)
Remove the side from the case.
Unplug the power cable from the hard drive.
Plug the computer back in.

Insert the Live CD or Live USB.
Start the computer, the CD/USB should boot.
Insert the target USB drive.
Select language
Select install Ubuntu.

Select Download updates while installing and Select Install this third-party software.
Continue

At "Installation type" select "Something else".
Continue

Confirm Device is correct.
Select "New Partition Table" 
Click Continue on the drop down.

(Optional partition for use on Windows machine)
Start with an external drive that has been formatted NTFS.
Click "Free space" and "Add".
Select "Primary".
Make "New partition size..." as large as required.
Location = Beginning.
"Use as:" = "do not use this partition".
Leave "Mount point" blank.
Make sure the "Format" box is not checked.
Select "OK"

Click "free space" and then "Add".
Select "Primary", "New partition size ..." = 5000+ megabytes, Beginning, Ext4, and Mount point = "/" then OK.

(Optional home partition)
Click "free space" and then "Add".
Select "Primary", "New partition size ..." = 5000+ megabytes, Beginning, Ext2, and Mount point = "/home" then OK.

(Optional swap space, allows hibernation)
Click "free space" and then "Add".
Select "Primary", "New partition size ..." = remaining space, (1000 to 8000 megabytes, or same size as RAM), Beginning and "Use as" = "swap area" then OK.

(Important)
Confirm "Device for boot loader installation" points to the USB drive. Default should be ok if HDD was unplugged.

Click "Install Now".
Select your location.
Continue.

Select Keyboard layout.
Continue.

Insert your name, username, password, computer name and select if you want to log in automatically or require a password.
Selecting "Encrypt my home folder" is a good option if you are worried about loosing your USB drive.
Select Continue.

Wait until install is complete.
Turn off computer and plug in the HDD.
Stick the side panel back on.

Note:
You may omit disabling the hard drive if, when partitioning you choose to install grub to the root of the usb drive you are installing Ubuntu to, (ie sdb not sdb1). Be cautious, many people have overwritten the HDD MBR.
You can revise grub later, if you wish.

---

### Post by Hawkyrou on 2013-06-10
ok thankyou but i cant disconnect my hard drive, im using a laptop and i paid for an extended warranty on so if i open it it will void the warranty which would be a waste 0f $250

how do i go about installing it to the usb without disconnecting the hard drive?? when i open boot manager to select the usb as boot device the install option automatically has it to install on my hard drive so how do i change that????

---

### Post by C.S.Cameron on 2013-06-11
Note:
You may omit disabling the hard drive if, when partitioning you choose to install grub to the root of the usb drive you are installing Ubuntu to, (ie sdb not sdb1). Be cautious, many people have overwritten the HDD MBR, (but it can be fixed).

---

