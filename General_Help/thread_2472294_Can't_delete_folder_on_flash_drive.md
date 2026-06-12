---
title: "Can't delete folder on flash drive"
date: 2022-02-23
forum: General Help
---

### Post by py-ohayo on 2022-02-23
Hello,

Can't delete folder 'System Volume Information' on flash drive.
Help, please.

```
root@ALABAMA:/media/pavel/FINA_32(1)# rm -rf 'System Volume Information'
rm: cannot remove 'System Volume Information/WPSettings.dat': Read-only file system
rm: cannot remove 'System Volume Information/IndexerVolumeGuid': Read-only file system
root@ALABAMA:/media/pavel/FINA_32(1)#
```

```
root@ALABAMA:/media/pavel/FINA_32(1)# cd 'System Volume Information'
root@ALABAMA:/media/pavel/FINA_32(1)/System Volume Information# ls -l
total 32
-rw-r--r-- 1 pavel pavel 76 janv. 28  2021 IndexerVolumeGuid
-rw-r--r-- 1 pavel pavel 12 janv. 28  2021 WPSettings.dat
root@ALABAMA:/media/pavel/FINA_32(1)/System Volume Information# rm IndexerVolumeGuid
rm: cannot remove 'IndexerVolumeGuid': Read-only file system
root@ALABAMA:/media/pavel/FINA_32(1)/System Volume Information# 
```

---

### Post by TheFu on 2022-02-23
```
Read-only file system
```
Mount it read-write and try again.

If you just want to wipe the storage, format it with a new file system.
If the format doesn't work, check that the read-only slider isn't enabled.
Sometimes flash storage wears out. Sometimes the first indication is read-only file systems.

I'm guessing this stick doesn't have a native Linux file system?  On Linux, the best flash storage file system to use is f2fs. Use that, if you can.  If not, I suppose you're stuck with exFAT or some other less-than-ideal choice.

---

### Post by py-ohayo on 2022-02-23
Thanks.
It's only this folder that causes problems.
The storage contain other useful data, I want them to be kept.
So, I can't format storage.
The origin of the problem - I can't move some files/folders under Windows 10.
Why I try to do it, nothing happens.
Searching on the web I found a solution, consisting in modifying security options of that folders.
But in this folders I the security TAB is absent.
Continuing to search I found another solution - delete  'System Volume Information' using Linux.
But I failed to remove it using Ubuntu.
Sincerely

---

### Post by TheFu on 2022-02-23
If the file system is mounted read-only, there is nothing that can be done to modify any contents. Period.
There are a number of reasons that a file system would be mounted read-only. If it is a Windows file system, that is almost always because Windows didn't correctly close the file system.

File systems matter. Which does it have?

---

### Post by ActionParsnip on 2022-02-23
What file system are you using on the USB stick? If it is FAT32 or some Linux based file system then you can fsck that in Ubuntu. Otherwise you can chkdsk NTFS in Windows. Make sure you use the safe removal feature in your OSes before you physically unplug the device. This will help stop things like this.

---

### Post by SeijiSensei on 2022-02-23
Also some USB storage devices have a physical read-only switch. Check if you have one and make sure it's disabled.

---

### Post by py-ohayo on 2022-02-23
The USB stick filesystem is FAT32, there is no read-only switch.
There is folder PHOTOS at this stick.
In this folder there are images (.jpg) and many sub-folders that also contain images.
I need to free space on this flash drive.
So I tried to move folder photos to other drive.
For images that located in PHOTOS (not in subfolders) it was Ok, I could move them.
For image files in sub-folders I couldn't do it.
Even when I first copy files, then try to delete them, deleting doesn't work.

---

### Post by ActionParsnip on 2022-02-23
Just run an fsck on the file system while it is unmounted.

---

### Post by TheFu on 2022-02-23
Looks like Windows corrupted your flash file system. Sorry.

You can copy the entire device and use some data recovery tools on the image of the drive while it is on different storage. Never touch the original files.  [https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)  

If stuff is important, always, have a backup.  If you do attempt using the data recovery tools, I think you'll quickly learn that backups are much cheaper compared to your time, even if you don't get paid.

If there were more than a few hundred files in any directory, when storage has any issues, it seems to lead to corrupt directories. Best to try to limit file counts to 100 or less in a single directory.  Learned that in the 1990s and I still live by it.  Took me until around 2005 to get backup religion. Even losing 80% of my data in 2002 didn't convince me. I'm stubborn/stupid in that way.

There is one more general run for fixing storage. Use the native OS to fix any file system for that OS.  I would never use Linux to try an fix NTFS or exFAT or FAT32/12/16.  The Linux tools are all reverse engineered - i.e. guesses.

---

