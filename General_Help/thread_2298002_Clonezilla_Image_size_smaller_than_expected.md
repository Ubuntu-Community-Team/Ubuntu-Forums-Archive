---
title: "Clonezilla: Image size smaller than expected"
date: 2015-10-08
forum: General Help
---

### Post by Fiksdal on 2015-10-08
Hey guys


This may have been asked before, but I couldn't find any old threads. I hope you guys can help me.


I just used Clonezilla for the first time today. It seemed to go well, but the resulting image is smaller than I expected.


The parition that I wanted to clone has about 21GB of space used on it, yet the image is only about 12GB. Is this normal? Shouldn't the image be about the same size as the space used on the partition?


I have 3 partitions on my drive. A Windows partition, an Ubuntu partition and a storage partition.


This is the partition that I tried to clone , sda5 (Ubuntu partition).

[IMG]http://i208.photobucket.com/albums/bb124/Fiksdal/Screenshot%20from%202015-10-08%20160408.png[/IMG]






This is the details of the image that was created by Clonezilla:


[IMG]http://i208.photobucket.com/albums/bb124/Fiksdal/Screenshot%20from%202015-10-08%20160448.png[/IMG]


Here is some info on all my partitions:


[IMG]http://i208.photobucket.com/albums/bb124/Fiksdal/Screenshot%20from%202015-10-08%20160619.png[/IMG]






What's going on here? Why is my image smaller than the space consumed on the partition? I would really appreciate some help.


Thanks!

---

### Post by howefield on 2015-10-08
By default Clonezilla will compress the image, The level of compression is user definable depending on the combination of speed and file size that you want.

Just checked one of mine done a few days ago, 6.7 gigabytes of disk space used with an image size of 3.1 gigabytes.

---

### Post by Fiksdal on 2015-10-08
> **howefield said:**
> By default Clonezilla will compress the image, The level of compression is user definable depending on the combination of speed and file size that you want.

Just checked one of mine done a few days ago, 6.7 gigabytes of disk space used with an image size of 3.1 gigabytes.

Alright, thanks a lot for the confirmation. Much appreciated. Here are some [other answers I got.]("http://askubuntu.com/questions/682968/clonezilla-image-size-smaller-than-expected")

Again, thanks.

---

### Post by howefield on 2015-10-08
You're welcome, if you get a chance to create another image might be worth taking the expert option rather than the beginner, you don't have to change anything just accept the defaults on each screen as they come up in front of you, which will be the same as taking the beginner option but will let you see exactly what it is doing "under the hood" and the options that are available, eg the level of compression to be applied.

---

### Post by David_Ramsay on 2015-10-08
Clonezilla is my god now.

link:-
ubuntuforums.org/showthread.php?t=2281308&highlight=remastersys+suddenly+works

Accept the defaults but partition backups require the Expert Option -( Not so expert) when
backing up partitions vs whole hard disks..

Dos Ghost was freelancer b4 norton company baught out that coders code..
Clonezilla can do more than.... I have never tried and tested most options.

IF -Clonezilla backup windows, always delete the hiberfil.sys and pagefile.sys files b4
backup.  A waste of space and always re-created on next windows boot.

For me, I always run the BleachBit App linux to clean up things b4 I do clonezilla backup.
Some hate BleachBit. I still like it..

---

### Post by Fiksdal on 2015-10-09
> **howefield said:**
> You're welcome, if you get a chance to create another image might be worth taking the expert option rather than the beginner, you don't have to change anything just accept the defaults on each screen as they come up in front of you, which will be the same as taking the beginner option but will let you see exactly what it is doing "under the hood" and the options that are available, eg the level of compression to be applied.

Great idea, thanks. I will do that next time I make an image.

Is it now easy to clone this image over to a second computer? That second computer has a hard drive of a different size, which is unpartitioned and NTFS formated with Windows installed. Can I simply clone the image over to that, and then boot Ubuntu with all the same programs and configurations? (I realize the previous OS and files will be deleted if I do this, that is what I want.)

---

### Post by howefield on 2015-10-09
> **Fiksdal said:**
> Great idea, thanks. I will do that next time I make an image.

Is it now easy to clone this image over to a second computer? That second computer has a hard drive of a different size, which is unpartitioned and NTFS formated with Windows installed. Can I simply clone the image over to that, and then boot Ubuntu with all the same programs and configurations?

You mean cloning over the windows installation ?

That should be fine as long as the second computer has a hard drive of the same size or larger than the original source, eg the source drive in your image above is 150.90 gigabytes, let's say the second drive is 320 gigabytes, you are good to go *but* the clone will only use 150.90 gigabytes on the new drive, the rest of the drive will appear as unallocated and to use all the space you would use something like gparted to resize the disk after cloning. 

If however, the second drive is smaller than your source, ie, < 150.90 gigabytes - it won't work. 

Hope that makes sense :)

---

### Post by Fiksdal on 2015-10-09
> **howefield said:**
> You mean cloning over the windows installation ?

That should be fine as long as the second computer has a hard drive of the same size or larger than the original source, eg the source drive in your image above is 150.90 gigabytes, let's say the second drive is 320 gigabytes, you are good to go *but* the clone will only use 150.90 gigabytes on the new drive, the rest of the drive will appear as unallocated and to use all the space you would use something like gparted to resize the disk after cloning. 

If however, the second drive is smaller than your source, ie, < 150.90 gigabytes - it won't work. 

Hope that makes sense :)

Sure, that's great. Resizing in Gparted sounds fine.

Does the second computers drive have to be larger than the whole drive of the image-computer, or does it just have to be larger than the partition I cloned? As you can see in OP, the whole drive of the original computer is 465 GB, whereas the partition that was cloned was 152,9 GB, with 21 GB of data on it.

Are you saying that the Windows computer I want to erase and clone to needs to have a hard drive of 152.9 GB or more?

---

### Post by howefield on 2015-10-09
> **Fiksdal said:**
> Are you saying that the Windows computer I want to erase and clone to needs to have a hard drive of 152.9 GB or more?

Yes, that's correct :)

---

### Post by Fiksdal on 2015-10-09
> **howefield said:**
> Yes, that's correct :)
Cool. Thanks for being helpful!

---

### Post by David_Ramsay on 2015-10-13
Only thing missing in clonezilla vs now Norton Ghost is auto resize to fill
partitions - but do we want that? Probably yes..  but Gparted Linux and 
AIOMI NTFS or just good old windows partition magic apps                                               do this.

---

