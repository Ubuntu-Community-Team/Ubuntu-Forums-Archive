---
title: "Ubuntu deletes file on NTFS partition"
date: 2013-06-05
forum: General Help
---

### Post by tigerjack89 on 2013-06-05
Don't know if this is the right forum.
I have a partition (called "Data"), shared from both Ubuntu & Windows; the partition is formatted as NTFS and is mounted at Ubuntu startup.
BTW, it seems that sometimes many random files are deleted when I use Ubuntu. I had the same problems with an old hard disk and I decided to buy a new one, but the problem is still here.
I know that there isn't a perfect compatibility with OperatingSystemDifferentFromWindows & NTFS, but isn't there any way to solve the problem?
If the NTFS can't be the right solution, what kind of file system I have to choice? The bad FAT?

Thanks in advance :)

---

### Post by Impavidus on 2013-06-05
Do you hibernate windows? That may cause those symptoms.

---

### Post by mastablasta on 2013-06-05
perhaps they are not deleted but only disk is not unmounted safely on turning off the maschine?

why would an operating system randomly delete files? who would use such an OS?

---

### Post by Mark Phelps on 2013-06-05
The question about Hibernation is important -- because when it hibernates, MS Windows saves the partition information for all NTFS partitions that are open at the time.  When MS Windows then restarts later, it replaces the current partition information with the information it saved.

It is not "randomly deleting files"; instead, it is doing what hibernation is supposed to do -- returning the machine (and its partitions) to the state it was in when it was hibernated.

---

### Post by tigerjack89 on 2013-06-05
No way guys, I've still thought to hibernation and it's consequences when I had the old disk, and for this reason now I never open Ubuntu when Windows is hibernated (especially with Windows 8).
And yes, it randomly deleted my files; unfortunately, it's what happens to my files.
IDK what is the problem to be honest. My only thought is that I used the NTFS partition to save all the documents and the default Ubuntu folders (like Videos, Pictures and Download) are on this partition.
So, maybe writing new files on this kind of partition could broken the File Table or something like that, idk.

---

### Post by tigerjack89 on 2013-06-05
Fortunately, I had a backup of my files (not all the files, but that's it).
Here is an example of what I mean
[IMG]http://img196.imageshack.us/img196/2198/screenshotfrom201306051.png[/IMG]

---

### Post by mastablasta on 2013-06-06
> **tigerjack89 said:**
> . My only thought is that I used the NTFS partition to save all the documents and the default Ubuntu folders (like Videos, Pictures and Download) are on this partition.
.


wait, wait, WAIT!

so, you installed ubuntu /home to NTFS?


or is everything that belongs to Ubuntu on ext (or some other Linux file system) and you just have a separate NTFS parittion for data?

again, the OS is not deleting any files by itself.

i am curious if you boot into windows and run checkdisk does it find and recover the "deleted" files?


edit: want to trouble shoot? show us your partitioning scheme:

```
sudo fdisk -l
```

that is small letter L in the end.

---

### Post by tigerjack89 on 2013-06-06
> **mastablasta said:**
> wait, wait, WAIT!

so, you installed ubuntu /home to NTFS?


or is everything that belongs to Ubuntu on ext (or some other Linux file system) and you just have a separate NTFS parittion for data?

No way, it's on an ext4 partition :) But all the documents folders (like video, pictures, public, ...) are on the Data partition; this folders are shared from Ubuntu and Windows.



> again, the OS is not deleting any files by itself.

i am curious if you boot into windows and run checkdisk does it find and recover the "deleted" files?
No, I also used a specific revorery program (Recuva) and it finds only a little of them. It's why I think it's Ubuntu (and not Windows) to delete files.
I mean, in Windows files are deleted only by adding a '\0' to the first "letter" (purists will forgive me), so it's quite impossible to don't find any of these files.
On linux, instead, the files just deleted are immediately overwrited, and it's why it's so difficult to recover them.


> edit: want to trouble shoot? show us your partitioning scheme:

```
sudo fdisk -l
```

that is small letter L in the end.
Not at home right now, but this is a scan made yesterday for the disk A.
The data partition is on disk B btw, but it's only one NTFS partition of about 1GB.

```

[COLOR=#555555][FONT=Monaco]sudo parted -l[/FONT][/COLOR]
[COLOR=#555555][FONT=Monaco]Model: ATA M4-CT256M4SSD2 (scsi)[/FONT][/COLOR]
[COLOR=#555555][FONT=Monaco]Disk /dev/sda: 256GB[/FONT][/COLOR]
[COLOR=#555555][FONT=Monaco]Sector size (logical/physical): 512B/512B[/FONT][/COLOR]
[COLOR=#555555][FONT=Monaco]Partition Table: gpt[/FONT][/COLOR]

[COLOR=#555555][FONT=Monaco]Number  Start   End     Size    File system     Name                          Flags[/FONT][/COLOR]
[COLOR=#555555][FONT=Monaco] 1      1049kB  316MB   315MB   ntfs            Basic data partition          hidden, diag[/FONT][/COLOR]
[COLOR=#555555][FONT=Monaco] 2      316MB   420MB   105MB   fat32           EFI system partition          boot[/FONT][/COLOR]
[COLOR=#555555][FONT=Monaco] 3      420MB   555MB   134MB                   Microsoft reserved partition  msftres[/FONT][/COLOR]
[COLOR=#555555][FONT=Monaco] 4      555MB   75,2GB  74,6GB  ntfs            Basic data partition[/FONT][/COLOR]
[COLOR=#555555][FONT=Monaco] 5      75,2GB  180GB   105GB   ntfs            Basic data partition[/FONT][/COLOR]
[COLOR=#555555][FONT=Monaco] 6      180GB   188GB   8389MB  linux-swap(v1)[/FONT][/COLOR]
[COLOR=#555555][FONT=Monaco] 7      188GB   241GB   52,4GB  ext4[/FONT][/COLOR]
[COLOR=#555555][FONT=Monaco] 8      241GB   251GB   10,5GB  ext4[/FONT][/COLOR]
[COLOR=#555555][FONT=Monaco] 9      251GB   256GB   4736MB  ntfs[/FONT][/COLOR]

```

---

### Post by Mark Phelps on 2013-06-06
> and for this reason now I never open Ubuntu when Windows is hibernated (especially with Windows 8).

Unfortunately, the default with Win8 is to have hibernation activated. So, even though you may think you shut it down, in reality, you put it into hibernation.  To prevent this, you have to go into Win8 and deactivate fast startup.  The link (from the Windows 8 forums) shows you how to do this:  [http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.html]("http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.html")

---

### Post by tigerjack89 on 2013-06-06
> **Mark Phelps said:**
> Unfortunately, the default with Win8 is to have hibernation activated. So, even though you may think you shut it down, in reality, you put it into hibernation.  To prevent this, you have to go into Win8 and deactivate fast startup.  The link (from the Windows 8 forums) shows you how to do this:  [http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.html](http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.html)
Thanks man, I read this some time ago but I completely forgot!! Maybe this could be the problem!!

---

