---
title: "Install problem"
date: 2018-07-24
forum: General Help
---

### Post by holdingfire20 on 2018-07-24
Hi, 
    I have Window 10 and I would like to dual boot it with Ubuntu.  Here lies the problem.

 I would like to have Ubuntu on an external drive 1 Terabyte, independant of Windows 10. 
 
Is it possible to only have the grub on Windows 10.
 
thankyou for reading my post.

---

### Post by westie457 on 2018-07-24
Welcome to Ubuntu Forums.

Personally I have not tried this with Windows 10, however a few years ago I had some success using Windows 8. I cannot remember all of the details now apart from having to use the 'Something Else' option in the Installer.

One thing I do remember about this experiment is the computer would not boot at all if the external drive was not connected before the power button was pressed.

---

### Post by yancek on 2018-07-24
It is possible but you will need to do a little reading on the subject.  I would suggest the link below which is the official Ubuntu Documentation on the subject.  Pay particular attention to the General Principles section.  I'm not sure if you are familiar with Linux drive/partition naming conventions.  If not, you will need at least basic familiarity with it so you do not overwrite your windows and install on the correct drive.  The windows 10 system, if it was pre-installed, is almost certainly a UEFI system so you would need to install Ubuntu UEFI also.  If it is UEFI, Ubuntu will create a directory for its UEFI files on the windows drive which should already have an EFI/FAT32 partition.  This will contain the Grub/EFI files.  You can check your BIOS to see if the computer if UEFI.  If you have specific questions after reviewing the link below, post back.

[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

---

