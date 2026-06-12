---
title: "Change permissions for external hard drive"
date: 2015-01-08
forum: General Help
---

### Post by petermartin2 on 2015-01-08
I have a hard drive that I can't do anything with. I've tried in discmanager and deleting it in Gparted but I can't and I've tried this command that I found somewhere
```
sudo mount -o remount,uid=1000,gid=1000,rw /dev/sdd
```
but it only says it can't find the desc

I've also tried this

```
w@w:~$ sudo mkdir go
w@w:~$ sudo mount -o rw,uid=1000,gid=1000,user,exec,umask=003,blksize=4096 /dev/sdd /media/w/go
w@w:~$ 
```

And

```
sudo gedit fstab
```

And adding

```
# line for mounting the external drive
UUID=D04A-0AE4   /media/w/GO  exfat   rw,uid=1000,gid=1000,user,exec,umask=003,blksize=4096   0   0
```Which didn't change the permissions either


In Gparted there's always a key on the drive and format is always greyed out! 
What should I do?

---

### Post by ajgreeny on 2015-01-08
With the disk attached let's see the output of** sudo fdisk -l** please, so we know exactly what we are dealing with in filesystem type.

I note you have used exfat in your fstab line; is that definitely what it is?

I am a bit out of date with fstab for mounting disks at boot-up, as I do not have any external disks other than ext4 which I use for backups and only attach when needed.

---

### Post by petermartin2 on 2015-01-08
> **ajgreeny said:**
> With the disk attached let's see the output of** sudo fdisk -l** please, so we know exactly what we are dealing with in filesystem type.

I note you have used exfat in your fstab line; is that definitely what it is?

I am a bit out of date with fstab for mounting disks at boot-up, as I do not have any external disks other than ext4 which I use for backups and only attach when needed.

Hello!

It looks like this:

```
Disk /dev/sdd: 698,7 GiB, 750156252672 bytes, 1465148931 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: gpt
Disk identifier: C250AB1B-4EE0-4862-A279-BD49122586AD

Device      Start        End    Sectors   Size Type
/dev/sdd1      40     409639     409600   200M EFI System
/dev/sdd2  409640 1464886751 1464477112 698,3G Apple HFS/HFS+
```

About your question - I really don't know I just googled the problem and tried to solve it through pages I found... I really don't know how to change permissions for a disc in Ubuntu, thankful for help!

I've formated it before in apple apparantly is it not compatible with Ubuntu maybe? Basically I want it to work on all OS with write permission all OS

---

### Post by coffeecat on 2015-01-08
Your partition is formatted HFS+ and if that is the journalled version, you will only be able to mount it read-only in Ubuntu, or in any Linux distribution. 

What do you want to do with the partition? Apple filesystems are always tricky in anything but MacOS.

---

### Post by petermartin2 on 2015-01-08
> **coffeecat said:**
> Your partition is formatted HFS+ and if that is the journalled version, you will only be able to mount it read-only in Ubuntu, or in any Linux distribution. 

What do you want to do with the partition? Apple filesystems are always tricky in anything but MacOS.

I want to move files from Ubuntu OS to mac OS and possibly to windows OS, is this possible?

---

### Post by petermartin2 on 2015-01-08
If I find windows and format it in windows will I be able to use it in Ubuntu?

---

### Post by coffeecat on 2015-01-08
> **petermartin2 said:**
> I want to move files from Ubuntu OS to mac OS and possibly to windows OS, is this possible?

> **petermartin2 said:**
> If I find windows and format it in windows will I be able to use it in Ubuntu?

So you need to move files between the three operating systems, Windows, MacOS and Ubuntu? That always causes problems.

The three main filesystems:
[B]
Microsoft's filesystem NTFS:[/B] Read-write (obviously) in Windows; Read-write in Ubuntu (which answers yes to your second question); and read-only out of the box in MacOS. There is a third party read-write ntfs-3g driver for MacOS but I have no recent experience of this.
[B]
MacOS's HFS+[/B] : Read write in MacOS. Read only for the journalled version in Ubuntu. If you remove the journal (not really recommended) you can read-write in Ubuntu but you will run into irritating ownership problems. There is a commercial HFS+ driver for some versions of Windows I believe.

**Linux ext4**: Read write in Ubuntu. For both Windows and MacOS there are 3rd party drivers, but some have limitations.

Summary: With the main native three filesystems for the three operating systems you will encounter complications with at least one of the other two.

What I would suggest:

1 - If the files you wish to transfer are less than 4GB, simply use FAT32. FAT32 is read-write out of the box in all three operating systems.

2 - If you need to transfer files > 4GB - say video files - then consider exFAT. ExFAT is a Microsoft filesystem but I believe it is fully supported in MacOS out of the box. For Ubuntu you need to install exfat-fuse and possibly exfat-utils. From what I have read on these boards, that seems to work but I have no direct experience of exFAT.

---

### Post by Morbius1 on 2015-01-08
If you format it in FAT32 you will have read / write access in all three operating systems although there are file size limitations with FAT32.

If you format it in NTFS ( which doesn't have the file size limitation ) you will have read / write access in Linux and Windows. Contrary to popular belief OSX can mount an ntfs partition as read / write natively without requiring any 3rd party software but you have to know how to make that happen. I can show you how if you choose that route.

---

### Post by petermartin2 on 2015-01-08
> **coffeecat said:**
> So you need to move files between the three operating systems, Windows, MacOS and Ubuntu? That always causes problems.

The three main filesystems:
[B]
Microsoft's filesystem NTFS:[/B] Read-write (obviously) in Windows; Read-write in Ubuntu (which answers yes to your second question); and read-only out of the box in MacOS. There is a third party read-write ntfs-3g driver for MacOS but I have no recent experience of this.
[B]
MacOS's HFS+[/B] : Read write in MacOS. Read only for the journalled version in Ubuntu. If you remove the journal (not really recommended) you can read-write in Ubuntu but you will run into irritating ownership problems. There is a commercial HFS+ driver for some versions of Windows I believe.

**Linux ext4**: Read write in Ubuntu. For both Windows and MacOS there are 3rd party drivers, but some have limitations.

Summary: With the main native three filesystems for the three operating systems you will encounter complications with at least one of the other two.

What I would suggest:

1 - If the files you wish to transfer are less than 4GB, simply use FAT32. FAT32 is read-write out of the box in all three operating systems.

2 - If you need to transfer files > 4GB - say video files - then consider exFAT. ExFAT is a Microsoft filesystem but I believe it is fully supported in MacOS out of the box. For Ubuntu you need to install exfat-fuse and possibly exfat-utils. From what I have read on these boards, that seems to work but I have no direct experience of exFAT.
Thank you so much for your answers. Then I will probably format it in exFAT as almost all my files are smaller than 4GB (although this explains my problems with moving big mkv-files).

My question now is - is there anyway I could do FAT32 in Ubuntu or do I need to do that in windows?

Tnx

---

### Post by coffeecat on 2015-01-08
> **petermartin2 said:**
> Thank you so much for your answers. Then I will probably format it in exFAT as almost all my files are smaller than 4GB (although this explains my problems with moving big mkv-files).

I hope exFAT is a typo there. exFAT supports filesizes larger than 4GB. FAT32 has a 4GB filesize limit.

Before you make your final choice, consider what Morbius1 said about making ntfs read-write in MacOS. I was aware that there was a hack to make the MacOS native ntfs driver read-write - something that Apple have not implemented out of the box - but as I didn't know the details or how reliable or otherwise this is I didn't mention it.

> **petermartin2 said:**
> My question now is - is there anyway I could do FAT32 in Ubuntu or do I need to do that in windows?

You can do it in either, and also in MacOS.

In Windows - or at least in Windows 8.1 - right click on whichever drive it appears in "This PC" -> Format -> Choose FAT32 from the File system drop-down.

In Ubuntu, use "Disks". Or you can use Gparted which you will have to install, and which I prefer.

In MacOS, you can use Disk Utility. I'm going from memory here but FAT32 is described as "MSDOS (FAT)" or similar in the options. If you do this, it's best to specify master boot record rather than GUID or Apple Partition Table (if they even still offer the last as an option).

---

### Post by petermartin2 on 2015-01-08
> **coffeecat said:**
> I hope exFAT is a typo there. exFAT supports filesizes larger than 4GB. FAT32 has a 4GB filesize limit.

Before you make your final choice, consider what Morbius1 said about making ntfs read-write in MacOS. I was aware that there was a hack to make the MacOS native ntfs driver read-write - something that Apple have not implemented out of the box - but as I didn't know the details or how reliable or otherwise this is I didn't mention it.



You can do it in either, and also in MacOS.

In Windows - or at least in Windows 8.1 - right click on whichever drive it appears in "This PC" -> Format -> Choose FAT32 from the File system drop-down.

In Ubuntu, use "Disks". Or you can use Gparted which you will have to install, and which I prefer.

In MacOS, you can use Disk Utility. I'm going from memory here but FAT32 is described as "MSDOS (FAT)" or similar in the options. If you do this, it's best to specify master boot record rather than GUID or Apple Partition Table (if they even still offer the last as an option).
I got it working in FAT32, could not select it in discs but it went fine in gparted once I choose new partition instead of format that was still greyed out. Thanks a bunch!

---

### Post by Morbius1 on 2015-01-09
> **coffeecat said:**
> I was aware that there was a hack to make the  MacOS native ntfs driver read-write - something that Apple have not  implemented out of the box - but as I didn't know the details or how  reliable or otherwise this is I didn't mention it.
Now that this topic is solved I thought I'd comment on your comment.

I have a usb stick which I formatted to NTFS with a label of NTFSusb. All I did was add the following line to /etc/fstab:
```
LABEL=NTFSusb none ntfs rw,auto,nobrowse
```
The next time the usb drive is inserted it mounts to /Volumes/NTFSusb fully writeable.

Granted, it doesn't come with the whole "daffodils and bunnies " user  experience that OSX users have become accustomed. There is no mount icon  on the desktop so there's no way to unmount it from there. In fact  there really isn't any indication that anything has mounted. Instead you  will have to use Finder to see it and unmount it:
[ATTACH=CONFIG]259123[/ATTACH]


** I didn't have to compile anything to the kernel or alter any configuration settings anywhere.
** You pretty much have to use nano to do the editing which comes with a learning curve if you've never used it.
** The syntax looks strange since I never specified a mount point.
** And as a long time Linux user you have to get over the initial shock  of an empty fstab file but Linux doesn't need to have the system's root  partition defined in fstab either.

I don't know if this constitutes a "hack" :D

But there is no denying it. FAT32 allows for an automatic and seamless experience.

---

### Post by coffeecat on 2015-01-09
> **Morbius1 said:**
> 
I don't know if this constitutes a "hack" :D


Opening a terminal and running nano in MacOSX? That would seem like a hack, and a scary hack too, to 99% of Apple users. :wink:

---

### Post by Morbius1 on 2015-01-09
> **coffeecat said:**
> Opening a terminal and running nano in MacOSX? That would seem like a hack, and a scary hack too, to 99% of Apple users. :wink:
Especially since 99% of them don't know there is a terminal in OSX :D

---

