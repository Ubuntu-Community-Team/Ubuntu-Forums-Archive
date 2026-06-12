---
title: "Advice needed for external disk formmating"
date: 2008-05-04
forum: General Help
---

### Post by geo909 on 2008-05-04
Hello everybody,

I have an external disk, a 500GB seagate freeagent drive.
I use it mainly for backups, and I do them quite frequently
so it gets really fragmented because it's ntfs.

 So, I decided I should format it to something else, like ext3.

 The thing is that I also want to use it in Windows PCs and don't want FAT because I have huge files backed up.
 
 Do you know any filesystem that is good for my case (frequent backups, big files..) + there is a windows program that can be used (I could carry it in a mini CD) to read & WRITE to this filesystem?

 I would prefer a program that it is not required to be installed, so I could use my external disk in a friend's PC for example without asking him to install things on his computer..

 Any ideas?
Thanks in advance!

---

### Post by kellemes on 2008-05-04
> **geo909 said:**
> Hello everybody,

I have an external disk, a 500GB seagate freeagent drive.
I use it mainly for backups, and I do them quite frequently
so it gets really fragmented because it's ntfs.

 So, I decided I should format it to something else, like ext3.

 The thing is that I also want to use it in Windows PCs and don't want FAT because I have huge files backed up.
 
 Do you know any filesystem that is good for my case (frequent backups, big files..) + there is a windows program that can be used (I could carry it in a mini CD) to read & WRITE to this filesystem?

 I would prefer a program that it is not required to be installed, so I could use my external disk in a friend's PC for example without asking him to install things on his computer..

 Any ideas?
Thanks in advance!

As far as I know this is not possible without installing a driver..
[http://howtoforge.com/access-linux-partitions-from-windows]("http://howtoforge.com/access-linux-partitions-from-windows")

Personally I'd probably go NTFS or FAT32 and see to it files don't get bigger as 4G.. Split them if needed.

Maybe others have better ideas.

---

### Post by RetiredInMaine on 2008-05-04
Well, I have never tried this since I use only linux
, BUT, you could try partitioning the external drive with fdisk or parted, then format one partition for windows and one for linux. Be caredul if you use parted as it will carry out your commands immediately, fdisk will allow you to back out before writing the new partitions.

parted can remove, resize and create new logical or primary partitions. You can run parted interactivly from your terminal by entering" ? sudo parted /dev/sdb - assumming that sdb is your external drive.
 
Warning, do not use mkpartfs sub command as I understand it does not create ext3 partions correctly. Instead use mkpart sub command to make a new partition. 

A typical session will look something like this:
$ sudo parted /dev/sdb      !>again assuming sdb is your external drive
print        !>this will print out your partitions
rm 1        !>this will remove partition number 1, assuming it is the only partition
mkpart   !>this will start the interactive partitioning
response will be: Partition type?(logical?) PRIMARY
enter primary or logical. I would opt for 2 primary partitions but it is your choice if you want to use logical partitions
next response: File system type?(ext2)? ext3
enter the file system typefor that partition.If you enter an invalid partition type you will be promted with a list of valid types.
Next response: Start?  enter 1 to start at begining
Next response: End?  enter ending size in megabytes.
q will quit parted

parted is documented in the info system.

NOTE you can not create a ntfs file system with parted. You will need to either resize the existing ntfs partition ot format it from windows. If you resize your partition you can use parted to creat aa ext2/3 partion on the remaining portion of your disk. 

I have read that you can use ntfsresize command to resize your ntfs partition. This command is part of the ntfsprogs package. Since I don't run windows I have never used that command. However I have used parted to create partitions and file systems on external disk drives. 

This is all theory as I have never had to do this. But since it is a back up disk you can burn a permanent back up to a dvd and then try this out. I hope it helps

---

### Post by geo909 on 2008-05-04
Hello everyone,

@kellemes Thanks for the links!
Yes, it seems that write is not supported without installing drivers..
I would use write2fs if it had write support..

@RetiredInMaine Thanks for the advice, I had thought about partitioning too,but it doesn't have a point since I want to access the same files from both linux and windows.. 

Is there another (non-extX) filesystem that doesn't need defragmentation
and there is a tool for read&write from windows?

If not, here's my thoughts:

1)I could let it as ntfs and defragment it every now and then 
2)I could format it to ext3 and if I go to a friend and want to copy something, I could use a small distro live-cd, like puppy linux..

Are there any real benefits for changing to ext3, except no need for defragmentation?

---

### Post by ghost_ryder35 on 2008-05-04
[http://en.wikipedia.org/wiki/Comparison_of_file_systems](http://en.wikipedia.org/wiki/Comparison_of_file_systems)

---

### Post by DaddyX3 on 2008-05-04
What version of Windows do you have installed? If you run VISTA you can use disk management to shrink your parition and then create new or whatever you like. I don't think that it has an option to format to ext3 or xfs etc. The advise given by RetiredInMaine will not allow you to format or create an ntfs parition. It can however allow you to recognize ntfs paritions.

---

### Post by geo909 on 2008-05-04
> **DaddyX3 said:**
> What version of Windows do you have installed? If you run VISTA you can use disk management to shrink your parition and then create new or whatever you like. I don't think that it has an option to format to ext3 or xfs etc. The advise given by RetiredInMaine will not allow you to format or create an ntfs parition. It can however allow you to recognize ntfs paritions.

Hmm.. No, I was talking about an external disk.

---

### Post by DaddyX3 on 2008-05-04
I understood that you had an external 500GB drive. I'm sorry for my horrible writing skills. Sometimes only I can decipher what is meant:oops: You can still do all of the above mentioned with an external drive. So are you saying that you do not have a VISTA or XP OS installed on your computer? Are you just trying to maintain this type of file system (ntfs or FAT 16/32) for your friends that run Winblows? I have the same issue as you. I have a 640GB eSATA drive that is treated the same as an internal even though it is external, so I'm confused on how this is an issue? As far as I can tell, the only option that we have is to allow the drive to get fragmented and go in and defrag every now and again:evil: One of the many wonderful benefits to running Winblows. 
-ps sorry for the terrible writing skills. I know that my posts are a hard read sometimes.

---

### Post by geo909 on 2008-05-06
> **DaddyX3 said:**
> I understood that you had an external 500GB drive. I'm sorry for my horrible writing skills. Sometimes only I can decipher what is meant:oops: You can still do all of the above mentioned with an external drive. So are you saying that you do not have a VISTA or XP OS installed on your computer? Are you just trying to maintain this type of file system (ntfs or FAT 16/32) for your friends that run Winblows? I have the same issue as you. I have a 640GB eSATA drive that is treated the same as an internal even though it is external, so I'm confused on how this is an issue? As far as I can tell, the only option that we have is to allow the drive to get fragmented and go in and defrag every now and again:evil: One of the many wonderful benefits to running Winblows. 
-ps sorry for the terrible writing skills. I know that my posts are a hard read sometimes.

 No, actually it was me that I didn't read well.. Your post makes 100% sense now that I'm re-reading it!

 Yeah, I have to keep XP but I am maintening the ntfs for my friends, that's indeed my case.

 I think I'll keep defragment it from XP every now and then.. ..except if there is a ntfs defragment tool for linux..

---

### Post by mannheim on 2008-05-07
I've never used it this way, but I've read of UDF being suggested for this purpose. I think XP can read UDF natively, and Vista can read and write it. In Ubuntu, you need the udftools package I think. You can try it out with:

```

sudo apt-get install udftools
sudo mkudffs /dev/sdd22     # assuming sdd22 is a partition to be reformatted
sudo mkdir /media/new
sudo mount -t udf /dev/sdd22 /media/new

```

I've no idea what the pros and cons of UDF are, as far as reliability, performance, and so on. No one seems to use it much in this context, so perhaps there are good reasons not to ...

---

### Post by bingoUV on 2008-05-07
Create two partitions. One very small FAT32 to store ext3 driver for windows. Second taking most of the space will be ext3 to store actual data.   

No fragmentation worth speaking of. Universal accessibility.

---

### Post by linuxisfree on 2008-05-07
> **geo909 said:**
> Hello everybody,

I have an external disk, a 500GB seagate freeagent drive.
I use it mainly for backups, and I do them quite frequently
so it gets really fragmented because it's ntfs.

 So, I decided I should format it to something else, like ext3.

 The thing is that I also want to use it in Windows PCs and don't want FAT because I have huge files backed up.
 
 Do you know any filesystem that is good for my case (frequent backups, big files..) + there is a windows program that can be used (I could carry it in a mini CD) to read & WRITE to this filesystem?

 I would prefer a program that it is not required to be installed, so I could use my external disk in a friend's PC for example without asking him to install things on his computer..

 Any ideas?
Thanks in advance!

I'd definitely suggest NTFS format... its what i use for my external drive. (Only 80GB but it has my data in it.)

---

### Post by geo909 on 2008-05-07
> **bingoUV said:**
> Create two partitions. One very small FAT32 to store ext3 driver for windows. Second taking most of the space will be ext3 to store actual data.   

 So, can I install the drivers and access the whole disk through the small FAT32 partition?! 

 So, are the steps below correct? 

(1) Create a new partition table, format the majority of the space as ext3
and leave a tiny FAT32.

(2) Boot to XP.

(3) Download [this little tool]("http://www.fs-driver.org/") and run the installer.

(4) When it comes to the location that it will be installed, I will choose the tiny partition in FAT, on my external drive.

(5)The next time I go to my friend's house and carry my external disk, then.. ..what? :-{

How will access my main ext3 partition from his windows machine? 

> No fragmentation worth speaking of. Universal accessibility.
Forgive my English.. What do you want to say with that? Do you recommend it or not?
 

> **linuxisfree said:**
> I'd definitely suggest NTFS format... its what i use for my external drive. (Only 80GB but it has my data in it.)

Well, I'm not a Linux hardcore, so I'm not doing this just to use a non MS format, but the disk is getting REALLY fragmented... I make backups in a very regular basis with very big files (from isos to disk images) and from the defragment utility of XP, the whole bar is red every time I run it!

---

### Post by bingoUV on 2008-05-07
Steps 1, 2 and 3 are correct. Store the installer in the FAT partition in the external disk. Also install in your XP machine internal disk (maybe in c:\program files). 

Now when you go to your friend's place, plug the external hard disk. Windows will say the hard disk has two partitions. One small FAT32 and one unknown. Say ok, and access the FAT partition. You will find your file system driver installer in this FAT partition. Install it on his machine. Now the windows machine will be able to see the other larger ext3 partition. Mount it in windows, access your files. 

Sorry, when I said No fragmentation worth speaking of. Universal accessibility, I meant
  1. Fragmentation will be almost negligible as you are storing all your data in ext3 partition. 

2. Since you carry the driver installer along with the external drive, you can access on all windows machine after installation of the driver from the same disk. 

Of course I recommend this. ext3 is much more well documented. If you have any problems with data corruption (hope not, but failing hard drives can cause anything), come to this forum and someone will be able to guide you to data recovery.  

In NTFS, only microsoft knows how to get back your data. Unless you have an expensive support program, you may not be able to recover your data from a corrupted file system in the external hard drive(hope not).

---

### Post by geo909 on 2008-05-07
Oh, I would like to avoid installing things in other people's computer, but I'll think about it..  There's also the other live tool for read purposes
(ext2fs).

@mannheim
It's the first time I hear about the UDF filesystem. I'll check it out..

---

### Post by geo909 on 2008-05-08
Ok, I did a big ext3 partition and let a small fat32.
But now when I plugin the disk it doesn't automount.
Is that normal?!
Should I start configuring fstab etc?

---

