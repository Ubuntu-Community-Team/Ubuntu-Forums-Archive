---
title: "Is there a way to choose destination folder during installation?"
date: 2015-01-14
forum: General Help
---

### Post by KayeNg on 2015-01-14
Hi guys, I've used Lubuntu before but stopped, so I'm still considered a newbie.

In Windows, when I'm installing a program, I usually get to choose where I want it to be installed.  For example, there are two hard disks in my desktop computer.  Windows is installed in Drive C:, and when I install a program such as Adobe Photoshop, I would install it in the other (physical) hard disk, Drive F:.

So my question is, can I do this via Synaptic or Software Center or other package installer? 

If that's not possible, can I do it manually? (since Synaptic and Software Center are fully automatic, correct?)

Thank you for your time.

---

### Post by Gordonbp531 on 2015-01-14
Not an answer per se, but when you install an application on your F drive, it only installs SOME of it there. There's still parts installed on the C drive, and of course the Registry entries for that application are on the C drive.
may i ask why you are doiung this in the first place? If it's lack of space on the C drive, then get a bigger drive! they're pretty cheap these days.
If you think by doing this you won't need to re-install programs if and when you need to re-set Windows then I'm afraid you're wrong. You will still need to re-install, so why bother?

---

### Post by yknet-laurent on 2015-01-14
I think installling software in different place is not the best way (nor the right way) to use Ubuntu (or Linux in general). If you need space, the way to go is not moving the directories you install software to other drives like F: in windows as in your example. Using Ubuntu you can transparently change the drive or partition where the directory is physically stored keeping its "organizational" place in the tree structure (by mounting the partitions on the desired directory).
For example, you could make 2 or 3 partitions on your second physical drive (F) to mount them on the directories /home, /usr and /opt. This way your 1st drive could be smaller and would not grow very much. This is only an example of course and you have to choose a partitioning scheme adapted to your needs but a different partition is frequently used to store /home as it is the directory that has more chance to grow and you can find how to do it at [https://help.ubuntu.com/community/Partitioning/Home/Moving](https://help.ubuntu.com/community/Partitioning/Home/Moving)

---

### Post by Impavidus on 2015-01-14
Software centre will install the software in the directory where the software wants to be. You cannot modify this. You can mount a partition on your other hard drive at this directory where the software will be installed, and it will be installed on the other hard drive. But most software it pretty small, so I wouldn't take the trouble if your root partition is at least 15GB.

---

### Post by buzzingrobot on 2015-01-14
Even on Windows, all but the simplest applications contain a number of files, often very many files. Applications need to be able to find their components, many of which may not be loaded into memory until, or if, they are needed. While Windows may often allow you to determine the installation location of the single executable file that launches an application, the remaning files that make up that application will be installed where they need to be installed. 

Linux uses 'shared libaries":  Code libraries that all application can use are installed only once in a known location. If you install an application that requires a library that is not already installed, the package manager (Synaptic, Software Center, apt-get, etc.) will download and install that library as a dependency.  If you then install another application that also requires that library, it will not be installed again because it is already on the system in a known location.

Also, as you know, Linux doesn't deal with physcial drives the same way Windows does.  Windows users are accustomed to partitions as something confined to a single disk that is identified a C: or D:, etc.  In Linux, a partition can easily use an entire drive. So, if the '/' was created to take an entire drive, addressing the '/' partition is equivalent to addressing that physical drive. However, a single partition in Linux can extend over one or more physical drives.

---

### Post by vasa1 on 2015-01-14
> **buzzingrobot said:**
> ... While Windows may often allow you to determine the installation location of the single executable file that launches an application, the remaining files that make up that application will be installed where they need to be installed. 
...
When I used Windows, I liked to install software from portableapps.com. Of course, not all software is available there.

Here's one: [http://portableapps.com/news/2015-01-13--firefox-portable-35.0-released](http://portableapps.com/news/2015-01-13--firefox-portable-35.0-released)

---

### Post by KayeNg on 2015-01-15
[**[COLOR=#000000]Gordonbp531[/COLOR]**]("http://ubuntuforums.org/member.php?u=22727"), no particular reason why I'm doing this, I just want to know if I can do it in Lubuntu.  I want to know my way around the Linux system.  And yes I know that I would need to re-install programs if I re-set Windows.
My head is spinning.  First of all, can you tell me the significance of setting the mount as "/" when I installed Lubuntu on my computer? I believe another option is /home , correct? What's the difference? What would happen if I choose the mount as /home during the installation of the Linux OS? 
(That's it for now, I'll ask about mounting partitions on the directories /home, /usr and /opt later.)

---

### Post by Gordonbp531 on 2015-01-15
> **KayeNg said:**
> [My head is spinning.  First of all, can you tell me the significance of setting the mount as "/" when I installed Lubuntu on my computer? I believe another option is /home , correct? What's the difference? What would happen if I choose the mount as /home during the installation of the Linux OS? 
(That's it for now, I'll ask about mounting partitions on the directories /home, /usr and /opt later.)

Your best be would be to sign up for this on-line course - it's free!
[https://www.edx.org/course/introduction-linux-linuxfoundationx-lfs101x-2#.VLdpW131G1E]("https://www.edx.org/course/introduction-linux-linuxfoundationx-lfs101x-2#.VLdpW131G1E")

---

### Post by Holger_Gehrke on 2015-01-15
> **KayeNg said:**
> First of all, can you tell me the significance of setting the mount as "/" when I installed Lubuntu on my computer? I believe another option is /home , correct? What's the difference? What would happen if I choose the mount as /home during the installation of the Linux OS? 
(That's it for now, I'll ask about mounting partitions on the directories /home, /usr and /opt later.)

In a Unix-like OS the concept of drives or storage devices is hidden from the normal user. It all looks like one big tree of directories. One file system is set up as the root level of this tree, called '/' or 'root'. You always need a '/'. Other file systems can be mounted into this tree - meaning you have a sub directory in the tree and the contents of the file system are seen as the content of this sub directory. For example: you could have the home directories of your users on a partition on a completely different drive than the system and mount that partition in the directory '/home'. Or if you expect to have some really big database in mysql you could mount a big hard drive as '/var/lib/mysql'

---

### Post by Mike_Walsh on 2015-01-15
> **yknet-laurent said:**
>  ...This is only an example of course and you have to choose a partitioning scheme adapted to your needs but a different partition is frequently used to store /home as it is the directory that has more chance to grow and you can find how to do it at [https://help.ubuntu.com/community/Partitioning/Home/Moving](https://help.ubuntu.com/community/Partitioning/Home/Moving)

This is, broadly speaking, correct.

The O/S itself is of fixed size, and will change relatively little.....perhaps grow very slightly with each new kernel, as support for new devices and hardware are added. As long as you regularly 'clean house', and get rid of old, unwanted kernels, your system space will remain pretty much static. And [COLOR=#ff0000]buzzingrobot[/COLOR] has it right; the only thing that Windows actually allows you to do is to select the location of the .exe file that will launch any given program. By their very nature, shared libraries ( the MS equivalent is the 'dll' file) MUST be in an unmoving location, so that any program that needs to use them will automatically know where to find them.

Software programs, in the broad scheme of things, don't take up very much space. What DOES take up an ever-increasing amount of space is your /home directory, since this is where you will save any data you wish to keep. This is why many people DO like to set up their /home partition in a different physical location...for instance, on an external hard drive.  And if you are running more than one O/S, you then have the advantage of being able to access the same data from each one.


Regards,

Mike. :)

---

### Post by George_Hostler on 2015-01-15
> **KayeNg said:**
> Hi guys, I've used Lubuntu before but stopped, so I'm still considered a newbie. In Windows, when I'm installing a program, I usually get to choose where I want it to be installed.  For example, there are two hard disks in my desktop computer.  Windows is installed in Drive C:, and when I install a program such as Adobe Photoshop, I would install it in the other (physical) hard disk, Drive F:.

So my question is, can I do this via Synaptic or Software Center or other package installer? If that's not possible, can I do it manually? (since Synaptic and Software Center are fully automatic, correct?) Thank you for your time.

You cannot do this via Synaptic or via Software Center. It must be done through the installation CD/DVD.

You need a separate partition set up. Reason for this is each partition will have the respective operating system boot on it (Linux for the Linux partition, Windows for the Windows partition).

 If you have sufficient space on the hard drive, your best bet is to reinstall Windows first. Partition the hard drive into two partitions. Each partiton will appear to the system as two separate drives. Install Windows on one of the partitions.

Then install Lubuntu on the other partition. During installation, Lubuntu will detect the Windows installation and create a menu for you, which gives you the choice to boot into Lubuntu or into Windows.

If you are unfamiliar or uncomfortable with the process, it is not hard, but I would recommend finding a friend or co-worker or associate familiar with Linux, to walk you through the steps.

Good luck, George

---

### Post by Impavidus on 2015-01-15
In my Windows experience, which terminates in the early years of WinXP, the data files belonging to an application usually stayed with the executable in any directory (and therefore partition) the user chose, be it C or D. These data files are what takes most of the disk space, more than executables or shared libraries. On Linux, most of them end up in /usr/share. My /usr/share is about 5GB, my entire root partition slightly over 9GB. Applications using very much data can often be configured to find it somewhere else, useful for add-ons not coming from the repositories. Sometimes you might choose to move data of one particular application to somewhere else and symlink to that, or move it to another partition and mount that on the original data directory. Often this can be done without using a life disk, provided you have the partition or at least unallocated space ready.

But again, I never saw a need to move thing around in this way. I only keep the software (applications and add-ons) not coming from the repositories on a separate partition (some are accumulating automatically, and I don't want a full root partition) and have configured the applications to look there for their data. So there is another 5GB in /usr/local/share.

---

### Post by KayeNg on 2015-01-18
Thanks guys.

Mike_Walsh, when you say 
"This is why many people DO like to set up their /home partition in a  different physical location...for instance, on an external hard drive."

1. How do I do that? is that something I should have done during the installation of my Lubuntu? 

2. What goes in /home? is it the equivalent of C:\Windows ?  (Currently my C:\Windows is around 8.5GB, if it matters)

3.And while we're talking about installation, what should be the** mount point** in the beginning of the installation process? If I look in GParted, my hard disk is:
/dev/sda1 --- ntfs --- system reserved 
/dev/sda2 --- ntfs --- Windows
/dev/sda3 --- ext2 --- Lubuntu 
/dev/sda4 --- linux-swap

4.  With regards to booting, I preferred to have Windows do the booting.  So, for the "Device for bootloader installtion:", I chose sda3, the Lubuntu partition as shown above.  That left me without being able to boot into Lubuntu because during startup, it boots straight into Windows with no option of what OS to boot into.  I then used EasyBCD in Windows, and now I can choose which OS i want to boot into when I turn on my computer.  Is this method ok?

---

### Post by Impavidus on 2015-01-18
1: It can be done during installation, but it's quite easy to move /home to a different partition later. See [https://help.ubuntu.com/community/Partitioning/Home/Moving](https://help.ubuntu.com/community/Partitioning/Home/Moving)

2: The Windows equivalent of /home is My Documents. More or less.

3: Every partition you want to use on Ubuntu needs a different mountpoint. The swap partition is somewhat special, as it will be handled automatically. At the very least you have to use the mount point / for one of your partitions, which will be the root partition, where the most important parts of the system will be installed.

4: It's OK. Having Linux handle the dual boot menu is more reliable and easier, so most people prefer that. It should work though. Most of the time.

---

### Post by Holger_Gehrke on 2015-01-18
> **KayeNg said:**
> Thanks guys.

Mike_Walsh, when you say 
"This is why many people DO like to set up their /home partition in a  different physical location...for instance, on an external hard drive."

1. How do I do that? is that something I should have done during the installation of my Lubuntu? 

There's an option during installation to set up your own layout of partitions during installation. Of course you can do it after installation, too, but I'd wait with that until you're more used to and comfortable with the system. It involves partioning and formating the new harddisk, putting a copy of the subdirectories of '/home' on it, changing the file '/etc/fstab' to mount the new disk in the directory '/home', renaming the old '/home' (just to be safe and have a backup), making a new '/home' and rebooting.

> **KayeNg said:**
> 
2. What goes in /home? is it the equivalent of C:\Windows ?  (Currently my C:\Windows is around 8.5GB, if it matters)


/home is the equivalent of the 'Documents and Settings' directory in Windows XP or the 'Users' directory in Windows 7. There's a directory for every (normal) user there. Programs put their settings here, often in hidden files or directories. You're supposed to put all your files into your directory in '/home/<yourUserNameHere>'

> **KayeNg said:**
> 
3.And while we're talking about installation, what should be the** mount point** in the beginning of the installation process? If I look in GParted, my hard disk is:
/dev/sda1 --- ntfs --- system reserved 
/dev/sda2 --- ntfs --- Windows
/dev/sda3 --- ext2 --- Lubuntu 
/dev/sda4 --- linux-swap


That probably means the partition that's used as '/', in your case '/dev/sda3'

[> **KayeNg said:**
> 
4.  With regards to booting, I preferred to have Windows do the booting.  So, for the "Device for bootloader installtion:", I chose sda3, the Lubuntu partition as shown above.  That left me without being able to boot into Lubuntu because during startup, it boots straight into Windows with no option of what OS to boot into.  I then used EasyBCD in Windows, and now I can choose which OS i want to boot into when I turn on my computer.  Is this method ok?

If it works, it's ok. You might want to look into configuring GRUB to show it's menu before booting Lubuntu, you can access some repair and test tools from that.

---

### Post by SeijiSensei on 2015-01-18
I recommend reading [http://en.wikipedia.org/wiki/Filesystem_Hierarchy_Standard](http://en.wikipedia.org/wiki/Filesystem_Hierarchy_Standard) to get an understanding of how files and directories are organized in Linux.  It bears little resemblance to the structure of a Windows machine.  Essentially all executable programs are stored in /usr/bin, with associated libraries in /usr/lib, and supporting files in /usr/share.  It's possible to assign /usr to a different drive or partition than / if you're committed to having the programs on a separate drive.  Personally I don't see any value to that.  There is value to creating a separate partition for /home, though.  Then your personal files won't be touched if you choose to upgrade or replace the operating system.

---

### Post by KayeNg on 2015-01-22
Impavidus, you said
"You can mount a partition on your other hard drive at this directory  where the software will be installed, and it will be installed on the  other hard drive."
How do I do that? Does this page cover it? [https://help.ubuntu.com/community/Partitioning/Home/Moving](https://help.ubuntu.com/community/Partitioning/Home/Moving)

---

### Post by Impavidus on 2015-01-22
Yes, that page covers it. Just replace /home with whatever directory you're moving. A few remarks though:
1: If you try to move a directory containing files for an application that's currently running or may be started automatically at any moment, things may go wrong. Close the application or do it from a live disk.
2: A few directories cannot be moved away from the root partition. These are the directories that the system needs before it can mount other file systems or that you need to fix the system if it's unable to mount other file systems. The directories in case are /bin, /etc, /lib*, /root and /sbin. Moving the pseudo-filesystems in /dev, /sys and /proc is obviously impossible too.
3: If you move a directory belonging to a particular package installed by the package manager to a different partition, and later uninstall the package, the package manager won't remove the (empty) directory as it would normally do because it's in use as a mount point. In this case, fix it manually by removing the line from /etc/fstab, unmounting the partition (happens automatically on a reboot) and deleting the empty directory.

---

