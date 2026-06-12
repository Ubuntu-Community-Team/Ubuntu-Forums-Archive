---
title: "usb data"
date: 2018-09-03
forum: General Help
---

### Post by trickshot on 2018-09-03
Hi, im new to ubuntu community, and because im used to using Windows i dont commonly use de disconnect safely option with pendrives, and withouth noticing i did the same thing on linux, when i reconnected the pendrive all data saved was lost, i just want to know if i can recover the data, its very important cause its not mine :c. thanks forward

---

### Post by yancek on 2018-09-03
Is the filesystem type on the usb a windows or Linux filesystem?
Were you using the usb on windows or Linux?
More details on exactly what and how you did whatever you did.  Might be able to recover data using testdisk.

---

### Post by Impavidus on 2018-09-04
Was the lost data already on the drive when it was plugged in (if so, it's probably still there), or have you lost the data that you copied to the drive just before pulling it out (if so, the data was probably never written to the usb drive)?

---

### Post by trickshot on 2018-09-04
> **yancek said:**
> Is the filesystem type on the usb a windows or Linux filesystem?
Were you using the usb on windows or Linux?
More details on exactly what and how you did whatever you did.  Might be able to recover data using testdisk.
i guess its windows because i borrowed it

---

### Post by trickshot on 2018-09-04
> **Impavidus said:**
> Was the lost data already on the drive when it was plugged in (if so, it's probably still there), or have you lost the data that you copied to the drive just before pulling it out (if so, the data was probably never written to the usb drive)?
i imagine that when i pulled out the drive it got the recent data deleted, it already said it had copied all info to the usb drive tho

---

### Post by oldfred on 2018-09-04
Have you tried chkdsk, if NTFS formatted or FAT32 formatted?
You can only run chkdsk from Windows.

With my flash drives, they continue flashing the LED for a minute or two after screen says done copying. Data is still in buffer waiting for slow flash drive write to finish. Or not all data has been copied. Running chkdsk may repair it.

---

### Post by trickshot on 2018-09-04
> **oldfred said:**
> Have you tried chkdsk, if NTFS formatted or FAT32 formatted?
You can only run chkdsk from Windows.

With my flash drives, they continue flashing the LED for a minute or two after screen says done copying. Data is still in buffer waiting for slow flash drive write to finish. Or not all data has been copied. Running chkdsk may repair it.
thanks for the idea, ill try using it, unfortunately mine hasnt got any led

---

### Post by trickshot on 2018-09-04
Got some files with chkdsk and the rest with recuva, still pretty sad im still relying on windows, but thanks for help

---

### Post by oldfred on 2018-09-04
It is pretty much Windows tools for Windows and Linux tools for Linux. 

Although a few Linux tools may work on a few Windows problems. I do not think any Windows tools work on Linux issues.

---

### Post by trickshot on 2018-09-05
> **oldfred said:**
> It is pretty much Windows tools for Windows and Linux tools for Linux. 

Although a few Linux tools may work on a few Windows problems. I do not think any Windows tools work on Linux issues.
so, just to know, how do i know if a usb drive is on linux format or windows format?

---

### Post by oldos2er on 2018-09-05
Look at it with gparted.

---

### Post by oldfred on 2018-09-05
NTFS or FAT or vfat when viewed from Linux.
The standard with Linux is now ext4, but there are many Linux formats.
Windows will not show Linux formats.
from Ubuntu
sudo parted -l
or
lsblk -f

---

### Post by trickshot on 2018-09-30
thanks for all

---

