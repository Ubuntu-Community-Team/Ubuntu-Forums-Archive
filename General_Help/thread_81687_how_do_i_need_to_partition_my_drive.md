---
title: "how do i need to partition my drive"
date: 2005-10-24
forum: General Help
---

### Post by Specialsauce on 2005-10-24
I'd apreciate any help on telling me how to partition my drives so i can install ubuntu alongside windows.

---

### Post by michael_salcher on 2005-10-25
create 2 partitions. install windows on the first one and ubuntu on the second one.

you should probably install windows before you install ubuntu.

---

### Post by Beggar on 2005-10-25
personally I would have at least 3 partitions, windows has to be the first, otherwise it wont work. Then you want a linux partition and a swap partition.

---

### Post by landotter on 2005-10-25
You want at a minimum, 4. If Windows is already installed, defrag it and find out how much space you have to work with, the installer can shrink the partition (please do a backup).

For any Linux I like to do the following:

/ 5g this is where your programs, kernel and temp files live
swap same as your memory, if you've got 256mb memory do the same in swap. more or a bit less probably never hurt anybody much
/home ? however much space you've got left, this is for your personal stuff.

You really really really want to have a seperate /home partition-cannot emphasise this enough. Get sick of Ubuntu or want to do a fresh install? If /home is separate, you can install a flavor of Linux w/o messing with your personal data and settings. A good thing.

You can get fancier. As I've got two HDDs in my box, I put /tmp and swap on a seperate drive--it makes things run smoother when I'm using an app such as Audacity, that makes a lot of use of the /tmp directory for raw audio.

---

### Post by Brent Dax on 2005-10-25
[QUOTE=Specialsauce]I'd apreciate any help on telling me how to partition my drives so i can install ubuntu alongside windows.[/QUOTE]

I know that it's possible to resize an existing Windows partition with the Ubuntu installer, but I haven't done it myself.  Make sure you defragment your Windows partitions before trying--the shrinking will work better.  There's a chance it won't be able to do it, in which case you'll need to use a program like PartitionMagic; it's also theoretically possible it may damage the partition, so be sure to back up any important data.

On the other hand, if you have a *tabula rosa*--or want to reinstall Windows anyway--here's my recommendation:

1. Boot up with the Windows install CD first.  If you're installing 2000 or XP (and you should probably be installing one of these), early on you'll be allowed to partition your hard drive.  Split all but a gigabyte or so between two partitions, and turn the remaining gigabyte into a third partition.

2. Format the first partition with FAT (**not** NTFS!) and continue installing Windows in it.  Linux can only read NTFS drives, but it can both read and write FAT drives.

3. Once Windows is installed, you'll want to install Ubuntu.  I don't remember the exact procedure, but you'll need to be careful--the default behavior is to overwrite the entire hard drive, which isn't what you want.  At some point, though, you'll be able to set up a partitioning scheme.  Use the big partition for Ubuntu's data and the small one for swapping.

4.  Finish installing Ubuntu.  From now on, grub (the boot loader) should allow you to choose between Ubuntu and Windows.

---

