---
title: "How to enlarge Ubuntu LiveCD Disk space (4.1 GB total)"
date: 2012-12-01
forum: General Help
---

### Post by khurtsiya on 2012-12-01
When I boot Ubuntu LiveCD it only has 4.1 GB disk space. I need to increase this space. How can I do this?

I have 8 GB RAM and booting 64bit LiveCD. I also have 32 GB flash where this LiveCD exists. But I still have only 4.1 GB disk space.

---

### Post by ajgreeny on 2012-12-01
I am not quite sure what you mean with your query, but I suspect you are asking if you can make the persistence file, assuming you made one when you made the live USB, larger than 4.1GB.

If that is what you want, the answer is no, or not in a simple manner..  This is not the fault of Ubuntu, but simply the size limit for any file on a fat32 flash drive.

I think it may be possible to make a separate partition on the flash drive after making the live USB, and if you make it ntfs or better, ext2, you can use that for storage of files, and those files could be larger than 4.1GB, but I have no experience of this.

---

### Post by khurtsiya on 2012-12-01
My English is not very good so I probably did not get what you wrote.

Will try to explain other way:

I create LiveCD USB on 32 Gb flash.

Then I boot from it and choose TRY UBUNTU so it loads without installation.

Assume I want to download file larger than 4 Gb - I can not download it to my home dir, because free space is just 4.1 Gb

---

### Post by ajgreeny on 2012-12-01
> **khurtsiya said:**
> My English is not very good so I probably did not get what you wrote.

Will try to explain other way:

I create LiveCD USB on 32 Gb flash.

Then I boot from it and choose TRY UBUNTU so it loads without installation.

Assume I want to download file larger than 4 Gb - I can not download it to my home dir, because free space is just 4.1 Gb
You are correct in your assumption, but as I said, this is because the live USB is on a fat32 flash drive and fat32 limits file size to 4.1GB.  I have never tried, but I think you can download such a large file to a hard disk partition or to another partition on the USB flash drive, which is formatted to ntfs or ext2, ext3 or ext4.  You would need to mount the partition first, of course.

---

### Post by khurtsiya on 2012-12-01
Are you sure Ubuntu USB Disk Creator creates Ubuntu USB LiveCD on FAT32 and not EXT4?

I believe this is not the case. I mean problem is not that one file is more than 4 GB (in real there are two files of 2 GB) but that there are TOTAL space of 4 GB on this live system.

---

### Post by ajgreeny on 2012-12-01
The total space on your live USB system is not the USB itself but the **casper.rw** file that is made by the USB creator.  As **casper.rw** is a single, encrypted file within the live system, which really is on fat32, it can not be larger than 4.1GB.

Put your live USB into a computer running an OS that can read it and you will see the casper.rw file, and should be able to see what I am talking about.

---

### Post by dcstar on 2012-12-01
> **khurtsiya said:**
> When I boot Ubuntu LiveCD it only has 4.1 GB disk space. I need to increase this space. How can I do this?


[http://askubuntu.com/questions/138356/how-do-i-get-a-live-usb-to-use-a-partition-for-persistence](http://askubuntu.com/questions/138356/how-do-i-get-a-live-usb-to-use-a-partition-for-persistence)

---

### Post by monkeybrain2012 on 2012-12-01
You can install Ubuntu in a flash drive like you would in a hard drive (as oppose to running a live usb with persistence), that way you can use as much space as your flash drive permits (use Ext4 instead of FAT)

First you need a live CD or a live usb for installing (doesn't matter whether you use a CD or a flash drive this is just for installing Ubuntu, to avoid confusion I will call this the live CD even though you may actually use a usb flash drive)

You need a second flash drive to install Ubuntu into (this is the one you are going to use eventually)

Boot from the live CD, choose install Ubuntu, then choose "something else", now point the installer to your usb (usually something like /dev/sdb or /dev/sdc, sda is usually your computer's internal harddrive, don't choose that one or you will wipe everything)

Then  format the usb drive as ext4, you should also add a swap partition (size is about 1.5 times of ram, but since you can boot it off different computers, you may want to choose one that roughly works for all)

Then in the bottom on the page it asks where to install the boot loader, this is very important, make sure you choose the correct drive (sdb say, if you install it into the internal drive then your computer will not be bootable afterwords if your usb is unplugged)

Then just proceed normally as you would install Ubuntu. Afterwords you would be able to boot into Ubuntu with the flash drive in any computer if the hardware is supported.

The catch for a full installation  in a flash drive is that it may run a bit slow and also you can only write and rewrite onto a flash drive for a limited number of times. Otherwise it is a full blown Ubuntu installation.

---

### Post by khurtsiya on 2012-12-02
Thanks for responses. But as I see I explained smth wrong.

To make things easier lets assume I write LiveCD not to USB stick but to real CD.

All we know that when you start system from this live CD and do things (install software, download files) - after shutting it down all your work is vanished.

This is what I need - nothing can make changes in my LiveCD system.

In terms of USB creator:

[IMG]http://i024.radikal.ru/1212/4a/d2f92365ac31.png[/IMG]

---

### Post by khurtsiya on 2012-12-02
In this context I want this system on CD to have more than 4 GB space to download (file size is no matter, say I want download 10 files by 600 MB)

---

### Post by coffeecat on 2012-12-02
@khurtsiya, you are confusing things by referring to a live CD when you mean a live USB. Let's clarify a few things.

[list=1][*]If you burn the ISO to CD or DVD you cannot save anything, except for data files saved to another medium. You cannot save downloaded and installed applications or configurations - you cannot create persistence.
[br][/br]

[*]If you write the ISO to a USB and use that as your bootup medium you can create persistence by ticking the "Stored in reserved extra space" tickbox as shown in your screenshot in your post #9, but this is limited to 4GB. This is because of the limitations of the FAT32 filesystem as explained by ajgreeny. The filesystem on the live USB is FAT32 in which you have a single file - casper.rw - itself formatted ext2, but because the casper.rw file is a file in the FAT32 filesystem, it cannot be greater than 4GB.
[br][/br]

[*]If you want to use all the storage space on your 8GB USB stick, you need to follow the method in the link that dcstar posted.
[/list]

---

### Post by khurtsiya on 2012-12-02
Thanks for reply. What if I want to use all space but not create persistence like in burning CD?

---

### Post by Cheesemill on 2012-12-02
If you boot from a Live CD (without persistence) then your temporary home folder lives in the machines RAM.

This 4GB download limit you are coming across has nothing to do with filesystems, it is simply the limit imposed by the amount of RAM your machine has available for you temporary home directory.

---

### Post by khurtsiya on 2012-12-02
I thought so too. But! I have 8 GB RAM and 64-bit LiveCD - so why it is only half of that amount and how can I increase this?

---

### Post by Rebelli0us on 2012-12-02
For maximum use of the 32 GB flash drive: Create live CD with 4GB persistence. Then in gparted shrink partition to the smallest possible, ~5BG. Then format the rest in a single partition ~25GB. With USB 3.0 UHS card **and** reader you get speeds ~70 MB/sec so it feels just like an installation on hard disk.

---

### Post by khurtsiya on 2012-12-02
> **Rebelli0us said:**
> For maximum use of the 32 GB flash drive: Create live CD with 4GB persistence. Then in gparted shrink partition to the smallest possible, ~5BG. Then format the rest in a single partition ~25GB. With USB 3.0 UHS card **and** reader you get speeds ~70 MB/sec so it feels just like an installation on hard disk.

Please consider that I want LiveCD **[COLOR="Red"]without persistence[/COLOR]**!

---

### Post by Cheesemill on 2012-12-02
I've done a bit of research so I now think I know what's going on.

When you boot a Live CD the tmpfs is created using the default options of the mount command which is to create a filesystem with a fixed size of 50% of your RAM. Unfortunately there is no way of overriding this value on an existing Live CD.

What you would have to do is create a custom Live CD which isn't a straightforward process. In a nutshell you would have to follow the instructions [here]("https://help.ubuntu.com/community/LiveCDCustomization"), but editing the cow_mountopt= line in /usr/share/initramfs-tools/scripts/live from:
```
cow_mountopt="rw,noatime,mode=755"
```
to:
```
cow_mountopt="rw,noatime,mode=755,size=6144MB"
```
(for a 6GB /tmpfs)

Then you need to rebuild the initramfs before finishing the Live CD build process.

All in all I don't think the effort is worth it when you could just use a USB drive with your Live CD to save the large files directly on to.

---

### Post by khurtsiya on 2012-12-02
Well thank you very much for clearing this. I believe the thread is closed now.

---

### Post by Rebelli0us on 2012-12-02
> **khurtsiya said:**
> Please consider that I want LiveCD **[COLOR="Red"]without persistence[/COLOR]**!

ok then leave out the persistence, it will make your 2nd partition even larger.

---

### Post by khurtsiya on 2012-12-02
But will it be vanished after reboot?

---

### Post by ajgreeny on 2012-12-02
> **khurtsiya said:**
> But will it be vanished after reboot?
Will what be vanished?

The OS will be impossible to change in any way if there is no persistence, but files you download to the second partition on the USB drive will still be there.

If that is not what you want, and you wish any downloaded files to be removed when you shutdown, I am sure it could be done with a script which runs automatically at shutdown.

However, I will have to leave it to others to give you more details about how to do that if it is what you want.

---

