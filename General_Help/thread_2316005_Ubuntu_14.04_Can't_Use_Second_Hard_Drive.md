---
title: "Ubuntu 14.04 Can't Use Second Hard Drive"
date: 2016-03-04
forum: General Help
---

### Post by cheese3 on 2016-03-04
Hi All,

I installed Ubuntu 14.04.4 on my desktop with two hard drives.  Right now I can only use my main sda hard drive.  I can't save any files on my second hard drive, sdb.    When I go into the home folder on the second hard drive, there is this message:

> THIS DIRECTORY HAS BEEN UNMOUNTED TO PROTECT YOUR DATA.

From the graphical desktop, click on:
 "Access Your Private Data"

or

From the command line, run:
 ecryptfs-mount-private

I've clicked on the "Access Your Private Data" and run the command but nothing happened.  Any suggestions?

---

### Post by yancek on 2016-03-04
So you have a computer with only Ubuntu 14.04 installed and you have your /home partition on sdb in a partition there, is this correct?  Not sure why you would do that although it shouldn't be a problem.  Did you do this during the install or after?  Have you checked the /etc/fstab file to see if there is an entry for the /home partition?  Can you run ls -l command on that partition to chec the owner:group and permissions?

---

### Post by Bucky Ball on 2016-03-04
*Thread moved to **General Help**.*

Welcome. Did you click the option to encrypt your data and partitions during install???

Open a terminal and run this:

> ecryptfs-mount-private

What do you see? Is it asking for a password? 

(BTW, it may be you've made a typo and the command is) 

> encryptfs-mount-private

---

### Post by cheese3 on 2016-03-04
> **yancek said:**
> So you have a computer with only Ubuntu 14.04 installed and you have your /home partition on sdb in a partition there, is this correct?  Not sure why you would do that although it shouldn't be a problem.  Did you do this during the install or after?  Have you checked the /etc/fstab file to see if there is an entry for the /home partition?  Can you run ls -l command on that partition to chec the owner:group and permissions?

Hi and thanks for the reply. 

Yes, I only have Ubuntu 14.04 on my computer.  I have my home partition on sda but there is another home partition on sdb.  I didn't do anything intentionally, it somehow happened during the install process.  

I checked the /etc/fstab.d file on the partition and it is empty.  How do I run the ls -l command on the partition?  When I run it in the terminal I get the following output: 

```
b@b-MS-7817:~$ ls -l
total 68
drwxr-xr-x 2 b b 4096 Feb 14 19:08 Desktop
drwxr-xr-x 8 b b 4096 Feb 29 19:48 Documents
drwxr-xr-x 3 b b 4096 Mar  2 19:25 Downloads
-rw-r--r-- 1 b b 8980 Feb 13 09:51 examples.desktop
-rw-rw-r-- 1 b b    0 Feb 13 10:28 hello.c
drwxrwxr-x 4 b b 4096 Feb 13 16:20 mt7601
drwxr-xr-x 2 b b 4096 Feb 13 10:03 Music
drwxr-xr-x 2 b b 4096 Feb 13 10:03 Pictures
drwxr-xr-x 2 b b 4096 Feb 13 10:03 Public
drwxr-xr-x 2 b b 4096 Feb 13 10:03 Templates
drwxr-xr-x 2 b b 4096 Feb 13 10:03 Videos
drwxrwxr-x 3 b b 4096 Feb 22 18:45 VirtualBox VMs

```

---

### Post by cheese3 on 2016-03-04
> **Bucky Ball said:**
> *Thread moved to **General Help**.*

Welcome. Did you click the option to encrypt your data and partitions during install???

Open a terminal and run this:



What do you see? Is it asking for a password? 

(BTW, it may be you've made a typo and the command is)


Thanks for the reply.

Yes, I chose to encrypt my data during the install.  Unfortunately, I don't remember if I chose to encrypt the partition.

When I run the first ecrypt command I get this: ```
b@b-MS-7817:~$ sudo ecryptfs-mount-private 
Enter your login passphrase:
Inserted auth tok with sig [what's this sig here?] into the user session keyring
fopen: No such file or directory
b@b-MS-7817:~$ 

```

When I run the second command I get: ```
b@b-MS-7817:~$ sudo encryptfs-mount-private 
sudo: encryptfs-mount-private: command not found
b@b-MS-7817:~$ 

```

---

### Post by Bucky Ball on 2016-03-04
Yep, as I thought. The first command was right. You're going to need someone who knows something about encrypted data and how to get to it. Unfortunately, I've never used encryption so not much to add.

Until someone arrives, you might try researching on the net for what that sig there might be ...

Were you asked to provide a encryption password or other information different to your regular Ubuntu username and password when you clicked encryption or any other time during install?

---

### Post by cheese3 on 2016-03-04
> **Bucky Ball said:**
> Yep, as I thought. The first command was right. You're going to need someone who knows something about encrypted data and how to get to it. Unfortunately, I've never used encryption so not much to add.

Until someone arrives, you might try researching on the net for what that sig there might be ...

Were you asked to provide a encryption password or other information different to your regular Ubuntu username and password when you clicked encryption or any other time during install?

I figured out what I did.

By luck I was restarting my computer and noticed I have another copy of Ubuntu 14.04 installed on my second hard drive.  So right now I have:

[LIST]
[*]An encrypted 120gb ssd hard drive with Ubuntu 14.04 (Main) 
[*]An unencrypted 1TB disk hard drive with Ubuntu 14.04 (Secondary) 
[/LIST]

I don't know how I managed to do this when installing. #-o

Maybe this isn't the thread to ask, but is it possible to erase the secondary hard drive and mount it in the main copy of Ubuntu 14.04?  So I can have one copy of Ubuntu 14.04 with two hard drives?

---

### Post by Bucky Ball on 2016-03-04
Boot the OS you want to keep and launch Gparted (install from Software Centre if you haven't got it) and check for the drive and its partitions in there (drop down list top right should find you the drive). You can then delete the partitions on that drive.

Problem is, as they're encrypted, they may not show up in Gparted or will show up as something other than what you're expecting and won't let you delete.

Again, you will need to research how to delete encrypted drives to do this.

Other point: Depending on which OS you installed last, you may hammer your grub and thus your boot by doing this. That will be fixable using Boot Repair or another means. To avoid this, boot into the OS you want to keep, open a terminal and:

> sudo grub-install /dev/sda

That should give control of Grub to the OS you are keeping so things should work after you delete the encrypted one.

---

### Post by cheese3 on 2016-03-05
> **Bucky Ball said:**
> Boot the OS you want to keep and launch Gparted (install from Software Centre if you haven't got it) and check for the drive and its partitions in there (drop down list top right should find you the drive). You can then delete the partitions on that drive.

Problem is, as they're encrypted, they may not show up in Gparted or will show up as something other than what you're expecting and won't let you delete.

Again, you will need to research how to delete encrypted drives to do this.

Other point: Depending on which OS you installed last, you may hammer your grub and thus your boot by doing this. That will be fixable using Boot Repair or another means. To avoid this, boot into the OS you want to keep, open a terminal and:



That should give control of Grub to the OS you are keeping so things should work after you delete the encrypted one.

Thanks for the help!  I was able to figure it out.  I used gparted and went through this tutorial [https://help.ubuntu.com/community/InstallingANewHardDrive](https://help.ubuntu.com/community/InstallingANewHardDrive)

The biggest mistake I made was that I didn't assign myself permission to use the second drive.  All set now!

---

### Post by Bucky Ball on 2016-03-05
Good-o and thanks for sharing. Please mark thread as solved (see first link in my signature at bottom of this post). Thanks and enjoy. :)

---

