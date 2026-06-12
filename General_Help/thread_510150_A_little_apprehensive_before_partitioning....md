---
title: "A little apprehensive before partitioning..."
date: 2007-07-26
forum: General Help
---

### Post by Penguin246 on 2007-07-26
Hello all. I've had quite a bit of experience with Linux and Ubuntu.

I love Ubuntu but I use Windows for gaming. When my hard drive went bottoms up I reinstalled windows then Ubuntu. I gave the Ubuntu partition too much space. I only have 5gigs left in my Windows partition and thats not much in a 200 gig HD.

I used GParted live cd to successfully shrink my Ubuntu ext3 partition. I am really nervous about expanding my windows partition. I keep hearing about data loss. I cant really back up anything and I dont want to have to reinstall windows/ubuntu AGAIN!
 
Is it safe to fill the allocated sapce with windows?

I have no winxp install cd only my shity emachines restore cd.

Here is a screenie of my gparted info:

[IMG]http://img377.imageshack.us/img377/6647/gpartedfinalsi4.jpg[/IMG]

P.S. i'm no noob but dont speak IT guy:).


EDIT: Yeah I know I need to scoot the ext3 Ubuntu partition over.

---

### Post by LaRoza on 2007-07-26
The safest course of action would be to make a new partition of the unallocated space, and use it in Windows and Linux.

I wouldn't mess with the Windows partition, or the Ubuntu. Having a seperate partition is safer also, and you will be able to keep data seperate from the OS, which is always a good idea.

---

### Post by MrHippocampus on 2007-07-26
Ive personally never had a problem with doing this, however I always back up when doing things like this simply as a precaution.

In the end its your call, is the risk of loosing everything worth the extra 46.93GB of space? do you have anything you really really cant afford to loose on your windows partition, or is it just the fact you don't want the bother of reinstalling?

---

### Post by tszanon on 2007-07-26
> **LaRoza said:**
> The safest course of action would be to make a new partition of the unallocated space, and use it in Windows and Linux.

I wouldn't mess with the Windows partition, or the Ubuntu. Having a seperate partition is safer also, and you will be able to keep data seperate from the OS, which is always a good idea.
I second that. I don't know the issues about resizing a NTFS partition under Ubuntu, but, anyway, it's best to keep your files away from the system partition. It keeps the system faster when accessing the disk.

---

### Post by Penguin246 on 2007-07-26
If I made a new partition could I install windows stuff on it? I dont want it for storing files or music.

---

### Post by LaRoza on 2007-07-26
Yes.

-EDIT You must make sure the installer installs to the partition, the installer will then install the program as usual.

---

### Post by Penguin246 on 2007-07-26
> **LaRoza said:**
> Yes.

-EDIT You must make sure the installer installs to the partition, the installer will then install the program as usual.

Will ext3 work or does it have to be ntfs?

---

### Post by LaRoza on 2007-07-26
It just has to be writeable from Windows, I would use FAT32. This is less secure, because any user will be able to run those programs, but if you don't need such restrictions, it is fine.

You could make it NTFS, then map it as a file folder, so it will look like a folder in Windows.

---

### Post by Penguin246 on 2007-07-26
> **LaRoza said:**
> 

You could make it NTFS, then map it as a file folder, so it will look like a folder in Windows.

How would I do that?

---

### Post by LaRoza on 2007-07-26
First, do you plan on using this partition in Linux also? If so, use FAT32, you will be able to install programs here, but it will keep its own drive letter in Windows, probably D: or E:.

If you plan on using this in Windows, NTFS is fine. To do this:

0. Format the partition, in Windows, go to "Computer Management" and select "Storage Devices". You will see the partitions, and format the unallocated space, NOT the Ubuntu partitions, which Windows won't be able to read.

1. After formatting, right click the drive and map it. I forget the exact menu/procedure, but it is simple.

---

### Post by tszanon on 2007-07-26
There is a driver that you install in Windows so you have read/write access to ext2 and ext3 partitions. You can download it in [http://www.fs-driver.org/](http://www.fs-driver.org/). Then, you will be able to read and write the partition under both windows and linux.

---

### Post by Penguin246 on 2007-07-26
> **LaRoza said:**
> First, do you plan on using this partition in Linux also? If so, use FAT32, you will be able to install programs here, but it will keep its own drive letter in Windows, probably D: or E:.

If you plan on using this in Windows, NTFS is fine. To do this:

0. Format the partition, in Windows, go to "Computer Management" and select "Storage Devices". You will see the partitions, and format the unallocated space, NOT the Ubuntu partitions, which Windows won't be able to read.

1. After formatting, right click the drive and map it. I forget the exact menu/procedure, but it is simple.
EDIT: Never Mind!!!

---

### Post by Penguin246 on 2007-07-26
When making the NTFS partition it asks me to either assign a drive letter or mount it in a C drive folder. I wanna make it hte program files folder. Bad ting is it has to be in a empty folder. Is there any possibility of getting around this? I thought of putting the program files stuff in a folder while in safe mode, mounting the partition in program files folder the putting the files back in. Would that work????

---

### Post by tszanon on 2007-07-27
> **Penguin246 said:**
> When making the NTFS partition it asks me to either assign a drive letter or mount it in a C drive folder. I wanna make it hte program files folder. Bad ting is it has to be in a empty folder. Is there any possibility of getting around this? I thought of putting the program files stuff in a folder while in safe mode, mounting the partition in program files folder the putting the files back in. Would that work????
Never tried, but it seems to be a good choice.

---

