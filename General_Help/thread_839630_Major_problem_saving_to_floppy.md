---
title: "Major problem saving to floppy"
date: 2008-06-24
forum: General Help
---

### Post by paddy1 on 2008-06-24
I am tryng to write an abi word file, saved as a microsoft word doc, to a floppy drive. I had Xubuntu on the system, and fearing a bad install, formatted the drive and reinstalled.

I save the file called "Test" to the user folder, and right click on the file and "send to floppy". It seems to copy, but when I open it in XP, the disk is blank. When I go to change the file permissions to read/write, I get an input/output error.

It says "Failed to open */media/floppy0/Test.doc* for writing (permission denied)"

Could this be a bug? My floppy drive is mounted. When I go to eject volume, it says "unable to eject floppy drive": eject: unable to eject, last error: invalid argument".

Any ideas please?

---

### Post by paddy1 on 2008-06-24
Am I wasting my time asking questions in this forum?

---

### Post by avtolle on 2008-06-24
[https://help.ubuntu.com/community/MakeFloppyDriveAvailableToEveryone](https://help.ubuntu.com/community/MakeFloppyDriveAvailableToEveryone) I don't know how helpful this will be, but here's something to look at.

---

### Post by paddy1 on 2008-06-24
Thanks Avtolle, but this didn't work. Would not allow me to save. Is it possible to modify and change in terminal window? and how?

---

### Post by VMC on 2008-06-24
It's been ages since I used my floppy drive, but I don't think the format of linux will work for Windows or DOS. If you put a DOS floppy in the drive can linux read it?

---

### Post by plucky on 2008-06-25
> Is it possible to modify and change in terminal window? and how? 


Open a terminal and insert a floppy disk ```
mkfs.vfat -F 32 /dev/fd0
```
This will format the floppy to vfat which can be read in linux and windows.
Again from the terminal window ```
mount /media/floppy0
```
That is a zero not a O.This will mount your floppy.
```
cp /path-to-file/filename /media/floppy
```
This will copy your file to the floppy.

To check if the file is copied ```
cd /media/floppy0
ls -l
```

You then have to dismount the floppy to make sure the file is written to the floppy.```
cd
umount /media/floppy0
```

This will change your directory back to /home and dismount the floppy,thus writing the files to disk.You need to change your directory or else the floppy will not dismount.The file or files should now be readable by linux and windows.

p.s I have found that double clicking on the icon on Xubuntu's desktop does not mount the floppy for the user to use.

Good Luck

---

