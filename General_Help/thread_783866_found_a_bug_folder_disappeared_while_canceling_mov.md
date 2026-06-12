---
title: "found a bug: folder disappeared while canceling move"
date: 2008-05-06
forum: General Help
---

### Post by Gfy on 2008-05-06
I've got a Western Digital external hard drive: [WD2500XMS-00]("http://www.google.com/search?q=WD2500XMS-00")
250 GB, usb powered and formatted fat32 by default.
If you don't access the drive for a while, it stops spinning and starts spinning again when needed.

How it went:
[LIST]
[*]A Nautilus window was opened with a directory listing of the external hard drive. The drive wasn't spinning.
[*]I selected 2 folders and drag and dropped them on an other location on the same drive.
[*]A window popped up displaying the move process. I clicked cancel (because I released it on the wrong location) just before hearing the drive spinning up.
[*]The folder I clicked and dragged has disappeared and is nowhere to be found. The other selected folder still exists where it was originally.
[/LIST]
Here is the properties screen. It seems like the numbers don't fit? 

[[IMG]http://img87.imageshack.us/img87/4752/schermafdrukwdpassportejg6.th.png[/IMG]](http://img87.imageshack.us/my.php?image=schermafdrukwdpassportejg6.png)

edit: the values in windows seem more correct.
[[IMG]http://img166.imageshack.us/img166/4858/propertieswindowsmx2.th.png[/IMG]](http://img166.imageshack.us/my.php?image=propertieswindowsmx2.png)

Now, can someone confirm this and file a bug report.
And how do I get my data back?

---

### Post by danwood76 on 2008-05-06
I would run a checkdisk on the fat drive.
I bet the files are still there but theyve been removed from the fat.
A checkdisk should be able to get them back for you.

Linux has dosfsck to check fat file systems.

```

sudo dosfsck [device]

```
Replace the [device] above with the block device of the drive.
If unsure post the results of the following command with the USB drive mounted:
```

sudo fdisk -l

```

---

### Post by Gfy on 2008-05-07
I got this:

```
sudo dosfsck -lv /dev/sdb1
dosfsck 2.11 (12 Mar 2005)
dosfsck 2.11, 12 Mar 2005, FAT32, LFN
Checking we can access the last sector of the filesystem
There are differences between boot sector and its backup.
Differences: (offset:original/backup)
  67:75/47, 68:6d/3e, 69:1e/09, 70:70/14
1) Copy original to backup
2) Copy backup to original
3) No action
? 3

/dev/sdb1: 17221 files, 6769264/7629261 clusters

```

I tried both number 1 and 2, but the end result is the same:

```
...
Checking file /Recycled/.
Checking file /Recycled/..
Checking file /Recycled/DESKTOP.INI
Checking file /Recycled/INFO2
Checking for unused clusters.
Checking free cluster summary.
Leaving file system unchanged.
/dev/sdb1: 17221 files, 6769264/7629261 clusters

```

Unmounted, tried option 1, but it didn't help. I'm guessing I should have picked number 2?

Less free space, but I still can't find the folder or the files.
[[IMG]http://img362.imageshack.us/img362/6308/schermafdrukwdpassportequ5.th.png[/IMG]](http://img362.imageshack.us/my.php?image=schermafdrukwdpassportequ5.png)

---

### Post by danwood76 on 2008-05-07
If anything the bug you describe is more to do with the fat filesystem itself mixed with your USB drive (and your actions).
I would update the partition type to ntfs, this is far better and more robust than FAT.
I think there is a windows tool that will do the conversion.

If the data is still there on the disk you may be able to recover it with a free windows un-delete tool.
Like this one: [http://www.dtidata.com/free_data_recovery_software/fat_32_fast_file_undelete.htm](http://www.dtidata.com/free_data_recovery_software/fat_32_fast_file_undelete.htm)

I just had a go at recreating this on my fat USB disk, I wasnt able to make files dissapear.
I made half move and half not, or none move, but not dissapear.

---

### Post by Gfy on 2008-05-07
> **danwood76 said:**
> If anything the bug you describe is more to do with the fat filesystem itself mixed with your USB drive (and your actions).
Still, something like this may not happen. It's not like I pulled a plug or something. Dataloss may only occur by hardware failure or user stupidity. Not by a bug.

> **danwood76 said:**
> I just had a go at recreating this on my fat USB disk, I wasnt able to make files dissapear.
I made half move and half not, or none move, but not dissapear.

I think these steps are important: the drive may not be spinning and you must cancel the operation before it's on speed.

---

### Post by Gfy on 2008-05-11
I tried to recover using Ontrack EasyRecovery Professional. I used the delete and the format option, but neither could find my directory or files.

It's very strange, but I still got a backup on another pc, so I haven't lost anything.

Like you suggested, I think I'm going to format it to ntfs.

---

### Post by aero_super on 2008-06-12
Hello!
I know this thread is already old, but I have exactly the same problem!
It could be a bug: I dragged a folder from the hard disk to the desktop and since there was already an old version of that folder on my desktop it asked me what to do: Merge, Skip, ..., Cancel.
I clicked cancel and... the folder on the hd disappeared. =(
I'm very disappointed as I lost some of my source code...
I have a Western Digital MyBook external hard disk that is formatted with NTFS.
Hope somebody has a hint!
Maybe it was a problem handling two different file systems at the same time? (NTFS and ext3) Is this a problem of the NTFS driver or of GNOME?
Thank you.

---

### Post by danwood76 on 2008-06-13
Maybe its a bug with western digital external drives and linux?

---

