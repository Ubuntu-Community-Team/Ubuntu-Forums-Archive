---
title: "Cloning my Hard Drive"
date: 2015-12-29
forum: General Help
---

### Post by Kpenguin on 2015-12-29
Hi,
I'm not sure if this is the right place to post this, so please move to the appropriate sub-forum if it isn't. This doesn't directly pertain to Ubuntu, but I know I can get good help here.
I have a 750 gb HDD on my laptop and recently bought a 500 gb SSD. I would like to clone the data on the HDD to the SSD. The two main partitions are a ~130 gb for Ubuntu and a ~530 gb for Windows, plus several small partitions for swap, bios, etc, etc. The Windows partition only has about 250 gb of data on it and the Ubuntu partition only has about 50 gb of data on it. Is there a drive cloning utility that will let me clone the data to the smaller drive? I've tried clonezilla, but that didn't work.

Thanks!
Kpenguin

---

### Post by haplorrhine on 2015-12-29
It's probably similar to making a system back-up, but to another hard drive rather than a flash drive.  However it might be a problem that not all such back-ups are bootable.  You might have to set one drive as a slave drive.

---

### Post by monkeybrain20122 on 2015-12-29
> **Kpenguin said:**
> Hi,
  Is there a drive cloning utility that will let me clone the data to the smaller drive? I've tried clonezilla, but that didn't work.



Fsarchiver will clone to a smaller drive. It is in the repo.[http://www.fsarchiver.org/Main_Page](http://www.fsarchiver.org/Main_Page)

Since it doesn't support FAT if you use uefi you would have to create a FAT partition manually. I have not done uefi so not sure how the whole thing is done, but googling will help. I remember seeing posts about it and at least one poster on UF reported it worked, though he didn't get into any detail of how.

A more painful and slow way would be to shrink your partition with gparted first then clone it with clonezilla.

---

### Post by yetimon_64 on 2015-12-29
> **monkeybrain20122 said:**
> ...
A more painful and slow way would be to shrink your partition with gparted first then clone it with clonezilla.

+1 to that, however the Windows partition may not like the use of gparted, best to shrink a Win partition with Windows tools if the OP were to go with this (rather painful) method. I was going to suggest this earlier today but withheld because of the "messiness" of this (possible) solution.

@ OP, I think monkeybrain20122's fsarchiver idea may be the better one to check out/research first; it sounds more promising in this situation to me.

---

### Post by Kpenguin on 2015-12-29
> **yetimon_64 said:**
> +1 to that, however the Windows partition may not like the use of gparted, best to shrink a Win partition with Windows tools if the OP were to go with this (rather painful) method. I was going to suggest this earlier today but withheld because of the "messiness" of this (possible) solution.

Indeed, it doesn't like Gparted very much. I've already tried that. I'm going to try a Windows partition editor.

---

### Post by monkeybrain20122 on 2015-12-29
A gui version of fsarchiver claims to support uefi and gpt. You may want to check it out [http://sourceforge.net/projects/qt4-fsarchiver/files/Live-CD-DVD/](http://sourceforge.net/projects/qt4-fsarchiver/files/Live-CD-DVD/)
Here is the wiki in German. If like me, you don't read German just google translate. 
[https://translate.google.ca/translate?hl=en&sl=de&u=https://wiki.ubuntuusers.de/qt4-fsarchiver&prev=search](https://translate.google.ca/translate?hl=en&sl=de&u=https://wiki.ubuntuusers.de/qt4-fsarchiver&prev=search)

Also this old thread may help [http://ubuntuforums.org/showthread.php?t=2221842](http://ubuntuforums.org/showthread.php?t=2221842) At the time I thought it didn't work with gpt and uefi, but as I said if you search around there are some workarounds involving manually creating a FAT partition or something like that.

---

### Post by Kpenguin on 2015-12-30
Okay, so I went with the more painful path of resizing my partitions. All my partitions are now smaller in total size than my new SSD. The extra space is marked as unallocated. I tried clonezilla again, and it still didn't work. Do I need to use some advanced options? I've been using beginner local device to local device mode.

---

### Post by Kpenguin on 2015-12-30
I resized the partitions and used partclone on clonezilla to create an image of my partitions so I can put that on the SSD. However, when it was cloning my C: partition, it stopped when it was about 75% done and said that the disk had bad sectors. Does this mean I have to clone all the partitions over again (I saved them all as a single image)?

---

### Post by Kpenguin on 2016-01-01
No need to worry about this anymore... I decided to be a man and re-install.
But it was well worth it; this new SSD is blazing fast (Ubuntu boots in literally 1 second)!

---

### Post by leunam12 on 2016-01-01
Attaboy! 

The way I have done it in the past is resizing the partitions so they match the destination drive and then use clonezilla in expert mode and check the option that says not to check the partitions size on the destination drive. After that you have to expand the partitions and run chkdsk in all the NTFS partitions. The last step is to run boot-repair if there are booting problems.

---

