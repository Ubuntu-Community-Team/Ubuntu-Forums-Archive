---
title: "External HDD info is wrong"
date: 2024-07-22
forum: General Help
---

### Post by klundermann on 2024-07-22
I don't know how I did this, but I'm pretty sure it took some pretty sophisticated idiocy on my part....

I wanted to reformat 2 external HDDs. One of them was a 320-GB Hitachi. Everything went fine with that.

Then I reformated a 1-TB LaCie HDD. That seems to have worked too, except that whenever I plug it in I'm told that it is a 320-GB Hitachi HDD. Maybe I forgot to unmount the Hitachi before plugging in the LaCie?  I don't know, but the question is, how to I get back the 680 GB of space that have gone missing? I've tried **disks** and **gparted**, but there seems to be no way of convincing them that the drive actually has a full terabyte of space.

I've also tried the Windows 10 disk-management tool, but no luck there either.

Does anyone have any suggestions?

---

### Post by TheFu on 2024-07-22
Did you create a new partition table (GPT), then create new partitions, then format with the file system type you want AND give the file system a "LABEL"?

BTW, don't bother with Gnome-Disks.

---

### Post by yancek on 2024-07-22
How are you 'told' that it is an Hitachi?  Do you see this in your file manager?  Do you see it under /media/username?  What filesystem did you format it, ntfs?  You indicate tried to change it in windows and that wouldn't do anything with a Linux filesystem.  You indicate you 'tried' gparted, disks and windows Disk Management but give no information.  Exactly what did you try to do?  What happened when you tried to unmount the filesystem?  Since you don't have any data on the drive the suggestion above to create a new partition table should do the job.

---

### Post by klundermann on 2024-07-22
Well, I just tried **fdisk /dev/sdc** and then ran commands g (which told me I'd created a new GPT disklabel) and then w to write the changes. **disks** still tells me it's a 320-GB Hitachi HDD.

---

### Post by klundermann on 2024-07-22
**disks** tells me it's a Hitachi 320-GB hard disk.

---

### Post by TheFu on 2024-07-22
> **klundermann said:**
> **disks** tells me it's a Hitachi 320-GB hard disk.

Ignore "disks".  Use **gparted**.  

Is there any chance that you cloned 1 of the drives to the other?

---

### Post by tea for one on 2024-07-23
Attach both external HDDs
Identify the disks with this command:-
```
sudo parted -l
```
Then run this command for each external disk:-
```
sudo parted /dev/nvme0n1 print free [COLOR="#0000FF"]# Change nvme0n1 to your disk identity e.g. sda or sdb or sdc etc
```[/COLOR]
Example below
```
redact@gmktec:~$ sudo parted /dev/nvme0n1 print free 
Model: KINGSTON SA2000M8250G (nvme)
Disk /dev/nvme0n1: 250GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt
Disk Flags: 

Number  Start   End     Size    File system  Name  Flags
        17.4kB  1049kB  1031kB  Free Space
 1      1049kB  1075MB  1074MB  fat32              boot, esp
 2      1075MB  44.0GB  42.9GB  ext4
 3      44.0GB  76.2GB  32.2GB  ext4
 4      76.2GB  184GB   107GB   ext4
        184GB   250GB   [COLOR="#0000FF"]66.4GB  Free Space[/COLOR]

redact@gmktec:~$ 
```
My disk is nvme0n1, but, I suspect your external HDDs will be sda or sdb or sdc - change the command accordingly

Please post the output for each external disk within code tags

---

### Post by yancek on 2024-07-23
> Well, I just tried **fdisk /dev/sdc** and then ran commands g (which told me I'd created a new GPT disklabel)  

What commands?  You have been asked a number of specific questions and respond with general statements.  You are making note of the specific commands you run and their sequence as well as the result.  That is what you should post not general statements.    I asked earlier what happened when you unmounted or tried to unmount the drive filesystem and you have not responded.  After using whatever commands you used with fdisk, did you reboot before checking 'disks' again and do you have only the Lacie drive attached?

---

### Post by klundermann on 2024-07-27
> **TheFu said:**
> Is there any chance that you cloned 1 of the drives to the other?

Though I do not know how to clone a disk, I suppose it's possible I did it accidentally.

I presume that cloning entails not just partitioning and formatting the disks identically but also copying all of the data. In this case, it would have involved to copies, since I did not connect the two disks simultaneously. Especially since the LaCie has just a USB 2.0 connector, I would think that a full cloning would have taken quite a bit longer than that the total time that I had one disk or the other plugged into my laptop.

---

### Post by klundermann on 2024-07-27
> **tea for one said:**
> Attach both external HDDs
Identify the disks with this command:-
```
sudo parted -l
```
Then run this command for each external disk:-
```
sudo parted /dev/nvme0n1 print free [COLOR=#0000FF]# Change nvme0n1 to your disk identity e.g. sda or sdb or sdc etc[/COLOR]
```
For the Hitachi, the result is:
```

Model: ST320LT0 07-9ZV142 (scsi)
Disk /dev/sdc: 320GB
Sector size (logical/physical): 512B/4096B
Partition Table: loop
Disk Flags: 

Number  Start  End    Size   File system  Flags
 1      0.00B  320GB  320GB  ntfs

```

For the LaCie, it's:
```

Model: Hitachi HTS545032B9A300 (scsi)
Disk /dev/sdd: 320GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos
Disk Flags: 

Number  Start  End  Size  Type  File system  Flags

```

It seems really odd to me that **parted print free** shows the name "Hitachi" *only* for the LaCie drive, but I am certain I have correctly identified the drives: before plugging in the LaCie, I plugged the Hitachi in and ran **parted -l**, which told me that the Hitachi was /dev/sdc.

---

### Post by tea for one on 2024-07-27
This disk ST320LT0 07-9ZV142 is a Seagate identity and, according to a quick web search
> LaCie, the premium brand of Seagate technology

Have you misidentified the disks?

---

### Post by klundermann on 2024-08-02
> **tea for one said:**
> This disk ST320LT0 07-9ZV142 is a Seagate identity and, according to a quick web search


Have you misidentified the disks?

Misidentification would seem the probable solution of the conundrum, but I have connected the LaCie alone (the Hitachi disk is not even in the same room!) and still see it identified as a 320-GB Hitachi:
```

~ > sudo parted /dev/sdc print free
Model: Hitachi HTS545032B9A300 (scsi)
Disk /dev/sdc: 320GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt
Disk Flags: 

Number  Start   End     Size    File system  Name  Flags
        17.4kB  1049kB  1031kB  Free Space
 1      1049kB  320GB   320GB   ntfs               msftdata
        320GB   320GB   335kB   Free Space

```

To drive the point home, I have tried to attach a photo showing both the physical connection of the LaCie to my laptop and, on screen, the output of `sudo parted /dev/sdc print free`, but the forum software throws an error.

---

### Post by tea for one on 2024-08-02
From your post no. 10
```
Model: Hitachi HTS545032B9A300 (scsi)
Disk /dev/sdd: 320GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos
Disk Flags: 

Number  Start  End  Size  Type  File system  Flags
```
From your post no. 12
```
~ > sudo parted /dev/sdc print free
Model: Hitachi HTS545032B9A300 (scsi)
Disk /dev/sdc: 320GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt
Disk Flags: 

Number  Start   End     Size    File system  Name  Flags
        17.4kB  1049kB  1031kB  Free Space
 1      1049kB  320GB   320GB   ntfs               msftdata
        320GB   320GB   335kB   Free Space
```
Why is the information now different?
It seems that you have now used GPT and added a partition?

From post no. 10
```
Model: ST320LT0 07-9ZV142 (scsi)
Disk /dev/sdc: 320GB
Sector size (logical/physical): 512B/4096B
Partition Table: [COLOR="#0000FF"]loop[/COLOR]
Disk Flags: 

Number  Start  End    Size   File system  Flags
 1      0.00B  320GB  320GB  ntfs

```
Why do you have Partition Table loop?

In post no. 1, you indicated that you wanted to format both disks, therefore attach this Lacie/Seagate and allocate GPT.
Then, create partitions to see if you now have 1TB?

---

### Post by klundermann on 2024-08-11
> **tea for one said:**
> From your post no. 10
```
Model: Hitachi HTS545032B9A300 (scsi)
Disk /dev/sdd: 320GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos
Disk Flags:

Number  Start  End  Size  Type  File system  Flags
```
From your post no. 12
```
~ > sudo parted /dev/sdc print free
Model: Hitachi HTS545032B9A300 (scsi)
Disk /dev/sdc: 320GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt
Disk Flags:

Number  Start   End     Size    File system  Name  Flags
        17.4kB  1049kB  1031kB  Free Space
 1      1049kB  320GB   320GB   ntfs               msftdata
        320GB   320GB   335kB   Free Space
```
Why is the information now different?
It seems that you have now used GPT and added a partition?

I'm sorry, but I do not recall what I may have done between post nos. 10 and 12 to alter the output of parted. I can, however, report that at present parted's output is identical to that reported in post no. 10.

> 
From post no. 10
```
Model: ST320LT0 07-9ZV142 (scsi)
Disk /dev/sdc: 320GB
Sector size (logical/physical): 512B/4096B
Partition Table: loop
Disk Flags:

Number  Start  End    Size   File system  Flags
 1      0.00B  320GB  320GB  ntfs

```
Why do you have Partition Table loop?

"Partition Table: loop" means nothing to me, unfortunately. If it is the result of something I've done, it was an accident.

> 
In post no. 1, you indicated that you wanted to format both disks, therefore attach this Lacie/Seagate and allocate GPT.
Then, create partitions to see if you now have 1TB?

OK, here's a **parted** session:
```

~ 331> sudo parted /dev/sdc
GNU Parted 3.4
Using /dev/sdc
Welcome to GNU Parted! Type 'help' to view a list of commands.
(parted) mklabel gpt                                                      
Warning: The existing disk label on /dev/sdc will be destroyed and all data on
this disk will be lost. Do you want to continue?
Yes/No? yes                                                               
(parted) mkpart primary ntfs 0 1000GB
Error: The location 1000GB is outside of the device /dev/sdc.
(parted) mkpart primary ntfs 0 500GB                                    
Error: The location 500GB is outside of the device /dev/sdc.
(parted) mkpart primary ntfs 0 321GB                                   
Error: The location 321GB is outside of the device /dev/sdc.
(parted) mkpart primary ntfs 0 320GB                                     
Warning: The resulting partition is not properly aligned for best performance:
34s % 2048s != 0s
Ignore/Cancel? i                                                          
(parted) print free                                                       
Model: Hitachi HTS545032B9A300 (scsi)
Disk /dev/sdc: 320GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt
Disk Flags: 

Number  Start   End    Size   File system  Name     Flags
 1      17.4kB  320GB  320GB  ntfs         primary

(parted) 
 
```

It seems I still can't create a partition larger than 320 GB,

---

### Post by yancek on 2024-08-11
>  "Partition Table: loop" means nothing to me

The below information explains the when a loop is used.  This is a quote from the GPArted online manual.  This is what you likely did whether you did it deliberately or knowlingly. 

>  To use a disk without a partition table, choose               loop to create a virtual               partition that spans the disk.  Then format to the               desired file system.               

I see you have tried Disk Management from windows and had no success.  It would seem to me that would work better as you are using or trying to create a windows filesystem on the partition.  If you don't meet with success, you might try a windows forum or the miscrosoft support site. 

The link below is to the Red Hat site and explains in detail how to create a partition table and then verify that it was created and then how to create partitions.  From a quick review of the site, it looks to me like you missed a few steps.  I'd review it and any other tutorial or site you were using.  I generally use gparted so am not really familiar with the steps.

 
[URL="https://www.redhat.com/sysadmin/partitions-parted"]https://www.redhat.com/sysadmin/partitions-parted

[/URL]

---

### Post by tea for one on 2024-08-11
> **klundermann said:**
> 
```
                                               
(parted) print free                                                       
Model: [COLOR="#0000FF"]Hitachi[/COLOR] HTS545032B9A300 (scsi)
Disk /dev/sdc: [COLOR="#0000FF"]320GB[/COLOR]
Sector size (logical/physical): 512B/512B
Partition Table: gpt
Disk Flags: 

Number  Start   End    Size   File system  Name     Flags
 1      17.4kB  320GB  320GB  ntfs         primary

(parted)  
```
It seems I still can't create a partition larger than 320 GB,
It's no surprise that you can only create a 320GB partition on your 320GB Hitachi disk.

We seem to be going around in circles at the moment.

Attach the disk Model: ST320LT0 07-9ZV142 (scsi) (with the "loop" partition table) and create a new partition table GPT.
Then, create your partitions.

---

### Post by klundermann on 2024-08-12
> **tea for one said:**
> It's no surprise that you can only create a 320GB partition on your 320GB Hitachi disk.

We seem to be going around in circles at the moment.

Attach the disk Model: ST320LT0 07-9ZV142 (scsi) (with the "loop" partition table) and create a new partition table GPT.
Then, create your partitions.

Believe it or not, the **parted** session I reported in my previous post took place with the 1-TB LaCie/Seagate drive attached. The Hitachi drive was not even in the same room at the time, nor were any other external drives attached.

I know this seems very strange, but it's true. The LaCie/Seagate drive seems to have been brainwashed into believing it is a Hitachi.

---

### Post by tea for one on 2024-08-12
> **klundermann said:**
> Believe it or not, the **parted** session I reported in my previous post took place with the 1-TB LaCie/Seagate drive attached. The Hitachi drive was not even in the same room at the time, nor were any other external drives attached.I know this seems very strange, but it's true. The LaCie/Seagate drive seems to have been brainwashed into believing it is a Hitachi.
It's become an episode of X-Files..............I don't know what to suggest now.

Ah, I know
Send me the disks by Fedex, I'll sort it ;)

---

