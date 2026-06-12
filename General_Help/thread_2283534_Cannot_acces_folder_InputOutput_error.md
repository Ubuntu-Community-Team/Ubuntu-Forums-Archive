---
title: "Cannot acces folder: Input/Output error"
date: 2015-06-22
forum: General Help
---

### Post by David4321 on 2015-06-22
I am trying to access a folder on a known good drive and always get the same error: This location could not be displayed. The directory was copied from a failing drive that was mirrored to this good drive. The directory contains a large archive of music in many folders, but the error message mentions an Input/Output error on a .txt file which was the only file loose in the Music parent folder I'm trying to open. The Music folder shows 256 items, 1.6 gb, so I know there's a lot in the folder if I could get past the error and enter it. I tried deleting this .txt file using terminal under sudo, but same i/o error. I also tried opening nautilus as root superuser, and same result.

Any suggestions? Thanks

[ATTACH=CONFIG]262788[/ATTACH]

---

### Post by jamesisin on 2015-06-22
Is it just for that one file or do you get this error for anything in the tree?  This can be a drive-failure related error.

---

### Post by wildmanne39 on 2015-06-22
Every time I have seen that error it is due to the drive failing.

---

### Post by David4321 on 2015-06-22
I can't even see any of the folders inside the "Music" folder, when I try to open that folder I get the i/o error shown, which only names that one .txt file which is the only file loose inside the Music folder. But there are clearly other folders inside the Music folder, and files inside those. When I rt. click the folder and read properties, I see it has 256 items, total 1.6 GB

The drive is definitely good, but that's the same result I was getting when I tried to open the folder on the original drive that was failing. This is the mirror copy on the new drive, which I made when the old drive started failing.

Wild Man, when you say drivers, I'm not sure what you mean. Are you saying system drivers for file handling? I get the same result using Nautilus or Nemo. Or did you really mean to say drive, not drivers?

---

### Post by nerdtron on 2015-06-22
Is this an NTFS drive? Then try to plug it in windows and run the disk checker. Don't forget to safely remove it afterwards.


I think you can also run disk checker for NTFS drives inside linux, I just forget the link where I got it but the initial task here should be to run the disk checker and look for file system error, that is, on a windows PC if it's a fat32 or ntfs drive.

---

### Post by wildmanne39 on 2015-06-22
Sorry I just meant drive, I have fat finger syndrome.

---

### Post by jamesisin on 2015-06-23
How did you mirror the failing drive to this drive?

nerdtron -- Could the OP just use fsck on Ubuntu?

---

### Post by matt_symes on 2015-06-23
Hi

What filing system are you using ? There is no way that anyone can help you unless you mention that.

I have seen this error,  due to hardware but also due to corrupted ext4, NTFS and FAT32 filing systems.

If your hardware is not failing and the problem is the filing system then the error you are seeing is a generic filing system error. I think it's at the VFS layer but don't quote me on that.

Kind regards

---

