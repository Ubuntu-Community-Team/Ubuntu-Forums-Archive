---
title: "Restore deleted home directory"
date: 2018-01-12
forum: General Help
---

### Post by ozramsay on 2018-01-12
I accidentaly deleted almost all home directory (the directory itself is remaining, but contains negligible amount of files). I interested in restoring my information, in parcticular in txt, py, ipynb files.

1. After deleteting I booted from the LiveUSB and didn't mount the Ubuntu parition (I did mount the partition containing the second OS - W7)
2. testdisks - advanced utils: restored some files, but not the ones I need
3. extundelete also didn't restored the needed files
4. scalpel failed with a mistake after a one hour of searching (unfortunately, I have not written down the error message: it was something like 'node did not found', and the laptop didn't react at all)

As far as I understand I could try GREP option with mentioning the initial string of the files (in my case it would be either '!#usr', ''', """ or 'import'). Could you please give me any advice about that option.

I also have read that I can restore the partition table via testdisk. But I don't know, is it fit for my case (as my partition table is apparently OK)?

Is there anything else I can do?

Isn't it strange, that none of the attempts successeded? Maybe I messed up something, as after only two minutes I rebooted the laptop from a liveUSB. I am quite new to Linux and I am very surprised that there is no way to restore the infomation. Hope, that I did something wrong:) and there is a way to redeem. 

Lubuntu 16.04, Acer Aspire 5750ZG

---

### Post by oldos2er on 2018-01-12
Did you delete them in a terminal, or in a GUI? If you used "rm" in a terminal, they're likely gone and unrecoverable. If you used a graphical file manager, the files might be in /home/$USER/.local/share/Trash

You can try [Photorec]("https://www.cgsecurity.org/wiki/PhotoRec") to retrieve files.

---

### Post by ozramsay on 2018-01-12
Yes, I tried Photorec - it returned a huge amount of data with broken names, I did not figure out how to handle it. I tried to narrow the search by opting out the type of files, but I found in the list of options only 'pyc' files but no 'py' files. Do you know how can I add it?

I removed it by running python script, so I assume that is the same as 'rm' in a terminal. 

I  have tried section testdisk -> analyse -> deep searh. It found  several version of the partition. Can it help me or is it dangerous?

---

### Post by dragonfly41 on 2018-01-12
If the files are very important you should really clone your disk and then use LiveUSB to work on recovering the cloned disk.
Then you will have a backup in case something more goes wrong.

Unfortunately Photorec will not restore filenames.

I would add R-Linux to the list of tools to try, but install it in your LiveUSB since if you install anything in your current disk you might overwrite files you are hoping to recover.   Another consideration is that when recovering files you will need somewhere to save them and this should not be on the disk you are recovering.   Get a USB flash drive for such recovery.

---

### Post by ozramsay on 2018-01-12
I suppose Photorec did restore my files, but I don't know how to find them in this mess. 

I have been saving restored files on another partition of the same physical hard drive (NTFS from my second OS). Is it OK?

I had Dropbox folder in the home directory, so I deleted it too. But the files has remained intact on the sever (it was outdated back up). I assume that it is because the Dropbox daemon was switched off, and it didn't syncronise my Dropbox folder (then empty) to the cloud. But if it were switched on, would I lost my files?

How do you think is it reliable enough sheme to backup in future?

---

### Post by dragonfly41 on 2018-01-12
[COLOR=#000000]> I have been saving restored files on another partition of the same physical hard drive (NTFS from my second OS). Is it OK?

This suggests to me that your "second OS" might be Windows.
The utility R-Linux which I listed earlier can install on Windows or Linux.
From Windows you can launch R-Linux to inspect your Ubuntu partition in an effort to recover ext4 partition.

I don't use Dropbox but I would ensure that sync is disabled before connecting again.
 Can you access DropBox account from Windows.

I use R-Linux in a dual-boot setup.

Regarding backup plan the basic approach is discussed in many threads in this forum.  Explore using rsync and grsync (the gui for rsync).


[/COLOR]

---

### Post by raleigh3 on 2018-01-12
> **ozramsay said:**
> I had Dropbox folder in the home directory, so I deleted it too. But the files has remained intact on the sever (it was outdated back up). I assume that it is because the Dropbox daemon was switched off, and it didn't syncronise my Dropbox folder (then empty) to the cloud. But if it were switched on, would I lost my files?

How do you think is it reliable enough sheme to backup in future?

There are several ways to backup.

I use bash scripts that copy impt files to another drive.

I also use Clonezilla. I put it on a flash drive. Faster than a CD.

It backs up your entire drive.
It can restore a un-bootable system to the last day that you made an image.

Highly recommend it.

---

### Post by ozramsay on 2018-01-12
I can access Dropbox via a webrowser, but there is an outdated backup

Tried R-Linux, no luck. I still do not understand how it's possible to restore a whole deleted partition but not some deleted files. However, it is as it is. 

OK, the damage has done. Do I need to reinstall my Xubuntu? 

By the way, some apps installed in my home directory (for example, Anaconda placed there not only config files but each of its files), do I need to force them to install in different place?

Thank you for suggestion!

---

### Post by Holger_Gehrke on 2018-01-12
> **ozramsay said:**
> [..]I still do not understand how it's possible to restore a whole deleted partition but not some deleted files. However, it is as it is.[...]


Removing a partition only changes the partition table, not the contents of the partitions. Erasing a file actually removes the name, decrements the reference counter in the inode, marks the inode as free if the counter has reached 0 and adds the blocks the inode referenced to the list of free blocks. So the best photorec or similar programs can do is look at free inodes which have a list of blocks that are all in the free block list and copy these blocks to some other file system with a new name.

Holger

---

### Post by raleigh3 on 2018-01-12
> **ozramsay said:**
> I can access Dropbox via a webrowser, but there is an outdated backup

Tried R-Linux, no luck. I still do not understand how it's possible to restore a whole deleted partition but not some deleted files. However, it is as it is. 

OK, the damage has done. Do I need to reinstall my Xubuntu? 

By the way, some apps installed in my home directory (for example, Anaconda placed there not only config files but each of its files), do I need to force them to install in different place?

Other than losing some files in your home dir, are there any other problems like programs no longer working?

Did you delete only files or were some dirs deleted?

If you do have to reinstall, I would do the following first.

1. Backup files you want to keep to another drive or pen drive
2. This will show you all packages you have installed. apt list --installed > Packages.txt

After the reinstall and after you have everything as you like, run Clonezilla and save to another drive.etc.

Good luck.

---

### Post by ozramsay on 2018-01-13
Moderator has combined two my posts, but they were addressed to two different people. So deleted the text from this post and placed two posts

---

### Post by ozramsay on 2018-01-13
> **raleigh3 said:**
> Other than losing some files in your home dir, are there any other problems like programs no longer working?

Did you delete only files or were some dirs deleted?

If you do have to reinstall, I would do the following first.

1. Backup files you want to keep to another drive or pen drive
2. This will show you all packages you have installed. apt list --installed > Packages.txt

After the reinstall and after you have everything as you like, run Clonezilla and save to another drive.etc.

Good luck.



[COLOR=#000000]I deleted almost everything in the home directory, including hidden file. Programmes seem to be working (excluding Anaconda and Dropbox which were installed there). [/COLOR]

[COLOR=#000000]Yet, the settings are gone, so I re-installed the system. 

[/COLOR]This time I installed apps in /opt/app_name folder. Which is the right way to give the apps permission to use these folders?

---

### Post by ozramsay on 2018-01-13
> **Holger_Gehrke said:**
> Removing a partition only changes the partition table, not the contents of the partitions. Erasing a file actually removes the name, decrements the reference counter in the inode, marks the inode as free if the counter has reached 0 and adds the blocks the inode referenced to the list of free blocks. So the best photorec or similar programs can do is look at free inodes which have a list of blocks that are all in the free block list and copy these blocks to some other file system with a new name.

Holger

Yes, now I see. Thank you.

I reinstalled the system and placed some files into the /opt/app_name folder. Which is the right way to give the app permission to use its folder?

---

### Post by ozramsay on 2018-01-17
OK, I have not restored the files, yet I have received all the needed information. Thanks for every participant in this thread!

---

