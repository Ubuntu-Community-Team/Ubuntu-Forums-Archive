---
title: "NTFS won't go away! unable to install xubuntu"
date: 2007-07-05
forum: General Help
---

### Post by DoctorMO on 2007-07-05
Hi, problem with a hard drive on an old Dell laptop that had XP installed; every time it attempts to install the installer creates the ext3 partition at the start of the disk and then xubuntu i n the background mounts it as ntfs, the installer then dies because it can't format the disk as ext3.

Now the really magic part of this is that I used first gparted then parted then fdisk then dd to remove ALL patitions from the entire disk. with dd I simple zero'ed the entire start of the hard drive.

How the hell can this ntfs partition keep on magically appearing!! I know it does this because every time it auto mounts it loads up a file windows will all the bloody windows files still there.

do I have to zero the entire disk?

---

### Post by jrusso2 on 2007-07-05
Seems we are missing some important information here, are we trying to dual boot?  Do you have more then one hard drive?

Did you shrink the windows partition if your trying to dual boot?

---

### Post by DoctorMO on 2007-07-06
No duel boot, 1 hard drive, I don't want to keep anything.

---

### Post by MCSE_Crossover on 2007-07-06
are you using the LiveCD? If you do that, when it boots to the desktop and you double click on "install" the setup routine should get you to a point where it asks you about partitioning. You should have three options I believe...being "use remaining free space," "use entire disk," or "manual." If you choose manual, it will allow you to create a custom paritioning scheme. When using manual, you will see the familiar gparted-looking screne. You can right click on the NTFS partitions and hit delete and then create all your custom ext3 partitions.

Hope that helps.

---

### Post by DoctorMO on 2007-07-06
not really, I did that 5 times with 3 different programs.... I think it's working now I basically zeroed the entire disk

---

### Post by stchman on 2007-07-06
> **DoctorMO said:**
> Hi, problem with a hard drive on an old Dell laptop that had XP installed; every time it attempts to install the installer creates the ext3 partition at the start of the disk and then xubuntu i n the background mounts it as ntfs, the installer then dies because it can't format the disk as ext3.

Now the really magic part of this is that I used first gparted then parted then fdisk then dd to remove ALL patitions from the entire disk. with dd I simple zero'ed the entire start of the hard drive.

How the hell can this ntfs partition keep on magically appearing!! I know it does this because every time it auto mounts it loads up a file windows will all the bloody windows files still there.

do I have to zero the entire disk?

During the Ubuntu installation there is an "Erase Entire Hard Disk" option I believe.

---

### Post by DoctorMO on 2007-07-06
There is a use entire hard disk option, but not erase entire hard disk. besides it doesn't do anything until it's doing the install and by then the system is already confused about what it should be mounting when. I think perhaps this is a bug with the auto-mounter (a udev or hal problem) that the installer should just switch auto-mounting off for ide and scsi disks during install.

---

### Post by Jimmy_r on 2007-07-06
Perhaps a zero-fill would do the trick?

Edit: perhaps something like this:
```
dd if=/dev/zero of=/dev/hda bs=1M
```
[http://www.linuxquestions.org/linux/answers/Hardware/Clean_Hard_Drive_zero_fill](http://www.linuxquestions.org/linux/answers/Hardware/Clean_Hard_Drive_zero_fill)

---

### Post by smoker on 2007-07-06
hi, try this:
[http://dban.sourceforge.net/](http://dban.sourceforge.net/)

i would also maybe check in the bios and switch off any 'auto-recovery' features if you find any.

best of luck

---

