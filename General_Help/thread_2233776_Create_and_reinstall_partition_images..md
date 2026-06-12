---
title: "Create and reinstall partition images."
date: 2014-07-10
forum: General Help
---

### Post by jferhid on 2014-07-10
Hello there, 
After messing around with windows 8.1 and the UEFI nightmare, I seem to have both windows 8.1 and ubuntu, dual booting and living peacefully in the same hard drive. But what I want is to create an image, for a possible situation where something breaks somewhere (as it happened before) and I cant boot neither of the OS. So for that case I would like to be able to pull the image, install it and back to the same state as it was when I took the image. 
I have been told that Macrium Reflect will do the imaging for windows, but I would like something that will do now for Windows, Linux and the dual booting mechanism (a real nightmare)
Will Redo do that? I mean will redo create an image of all the partitions and when restoring it, everything will be in the right place and will boot? 
Thanks in advance,

Javi

---

### Post by Bucky Ball on 2014-07-10
*Post moved to own thread.*

Welcome. As was discussed in the other thread, Clonezilla will do what you are asking. It can image a partition, Windows or Ubuntu, and reinstall it identical to how it was on another partition of the same or larger size.

Once the images are reinstalled you may need to tweak the boot process a little.

Clonezilla will also clone an entire drive and reinstall as it was. More here:

Create image:
[http://rbgeek.wordpress.com/2013/04/14/how-to-use-clonezilla-to-backup-hard-drive-and-create-recovery-iso-image/](http://rbgeek.wordpress.com/2013/04/14/how-to-use-clonezilla-to-backup-hard-drive-and-create-recovery-iso-image/)

Create recovery ISO:
[https://rbgeek.wordpress.com/tag/using-clonezilla-to-create-iso-image/](https://rbgeek.wordpress.com/tag/using-clonezilla-to-create-iso-image/)

Partition cloning step by step:
[http://cdonner.com/partition-cloning-with-clonezilla.htm](http://cdonner.com/partition-cloning-with-clonezilla.htm)

Create Live media (with pics):
[http://clonezilla.org/fine-print-live-doc.php?path=./clonezilla-live/doc/04_Create_Recovery_Clonezilla/01-clonezilla-boot-menu.doc#01-clonezilla-boot-menu.doc](http://clonezilla.org/fine-print-live-doc.php?path=./clonezilla-live/doc/04_Create_Recovery_Clonezilla/01-clonezilla-boot-menu.doc#01-clonezilla-boot-menu.doc)

---

### Post by jferhid on 2014-07-11
Hey Bucky Ball,

Thanks for the answer and for the links. 

So you wrote that you can image/backup the individual partitions and then restore them. You said "Once the images are reinstalled you may need to tweak the boot process a little" and then you also said "Clonezilla will also clone an entire drive and re install as it was". So, do I understand right that if I clone partition at the time, then I can have the boot problems, but if I do clone the whole disk, then should boot without problems?
That is the part that scares me, I have read here and there, people saying that afterwards it never boots, but I guess I am missing something,  shouldn't it boot just fine, since it is copying everything and dumping it into a new drive (or old one but formatted clean) and that should include the MBR and the EFI partition.
As in the story of the guy in one of your links, I have wasted so much time to get the system working fine with windows, ubuntu and lenovo stuff (and feels so tricky..) that I would like to be able to get back to it, if things go wrong at some point.

---

### Post by Bucky Ball on 2014-07-11
If you, say, cloned the Windows partition, cloned the Ubuntu partition then put them back in EXACTLY the same partitions they were cloned from without touching the MBR, yes, it might boot without incident.

If not, you need only boot from a LiveUSB once both partitions are replaced and run Boot Repair. Very simple and nothing to panic about:

Get Boot Repair:
[https://help.ubuntu.com/community/Boot-Repair#Getting_Boot-Repair](https://help.ubuntu.com/community/Boot-Repair#Getting_Boot-Repair)

Yannbuntu's thread:
[http://ubuntuforums.org/showthread.php?t=1769482](http://ubuntuforums.org/showthread.php?t=1769482)

Just choose the 'Recommended Repair' option.

If you clone the entire drive, yes, I think it does also clone the MBR and should go back and boot as was. Again, if not, Boot Repair is your friend. ;)

---

### Post by sudodus on 2014-07-11
> **Bucky Ball said:**
> ...
If you clone the entire drive, yes, I think it does also clone the MBR and should go back and boot as was. Again, if not, Boot Repair is your friend. ;)

I have restored a full drive backup (using Clonezilla). A full backup (of the entire drive) clones the head of the drive (including the MBR), not only the partitions.

@*jferhid*: It is a good idea to ***test that your backup is good***. Without testing you do not know, if there is something wrong with it, and it is too late to find that out, when your drive is failing. To test that a compressed image is good, you need another drive of the same size as or bigger than the original drive. Remove the original drive and restore from the image to the other drive (make a clone). Then test that things work properly, when booted from the clone.

---

### Post by jferhid on 2014-07-11
Thank you guys,

I want the full drive backup, with the MBR and everything, at the moment the hard drive has "zillion" partitions due to the weird partition scheme Lenovo choosed.

@sododus, yes that is a very good point, I have learned it the hard way, when I trusted the horrible recovery system that Lenovo included in their machines. The first thing I did when I got the Laptop was to create a recovery image, and then installed Ubuntu in dual boot with the windows 8. The problem came when one day, something went wrong in the Linux part and when trying to use boot-repair, got even worse :) It was then when I discovered that the Lenovo recovery crap, only works if things work just fine, but if your drive crashes or gets messed up, you are out of luck...who needs recovery when things go wrong, right?

I need to think about how to test it, because it is a laptop still under warranty and I am afraid that if I remove the hard drive to put another, I may void the warranty (it is all nicely closed under the metal case, so would need to open it, to be able to access the hard drive)

Thanks guys for the replies.

 > **sudodus said:**
> I have restored a full drive backup (using Clonezilla). A full backup (of the entire drive) clones the head of the drive (including the MBR), not only the partitions.

@*jferhid*: It is a good idea to ***test that your backup is good***. Without testing you do not know, if there is something wrong with it, and it is too late to find that out, when your drive is failing. To test that a compressed image is good, you need another drive of the same size as or bigger than the original drive. Remove the original drive and restore from the image to the other drive (make a clone). Then test that things work properly, when booted from the clone.

---

### Post by sudodus on 2014-07-11
Often the warranty allows you to open the lid to add or replace RAM and internal disk, but you should read very carefully the conditions for your particular computer.

I think it is impossible or at least very hard to test that Windows works from an external drive, but linux will work (for example from a USB drive, and if no proprietary drivers, even in another computer).

---

### Post by jferhid on 2014-07-11
Thanks Sudodus.
One last question :) If I have a disk of 1TB, from which at the moment only used something like 39GB, with the basic Windows and Ubuntu installations (plus the recovery partition), how big will be the image file? Is it something around the 39GB size (or smaller) or will it be the 1Tb?
And I guess I can put the resulting image in an external USB HDD containing other stuff, just for storage/backup purpose.

I feel now more confident with Clonezilla, and I guess as soon as I have some free time, Ill jump on it, before installing more stuff, gives you peace of mind :)

---

### Post by sudodus on 2014-07-11
Clonezilla makes a compressed image of the part of the drive, that contains data. Free space is not imaged. Swap is not imaged. This means that ***the image will be smaller than what is used in all partitions***, in your case smaller than 39 GB. But when you restore from the image to a drive (for testing: a second drive, to become a clone), 1 TB will be used.

Yes, you can put the resulting image in an external USB HDD containing other stuff, just for storage/backup purpose.

---

### Post by jferhid on 2014-07-11
thank you guys for the replies, clonezilla time will be :)

---

### Post by Bucky Ball on 2014-07-11
PS: You haven't got an external drive so you don't need to open your computer and swap the drives out?

---

### Post by jferhid on 2014-07-11
I have one for storing the image, but I don't have a second one (actually I have two external HDD but they contain the same information, just in case one crash). Also, don't know if would boot from there, would windows boot from an external hard drive? would Linux?
Are you saying that you could, in theory, have a laptop without hard drive, and using a USB hard drive you could be booting from there?

Interesting thought, maybe for companies and security, though doesn't make sense for laptops, but maybe for desktops, companies with people working in shifts, they could have desktops and people would bring their own hard drive. I guess it is like what some people do with Linux in USB stick

---

### Post by yancek on 2014-07-11
> Are you saying that you could, in theory, have a laptop without hard  drive, and using a USB hard drive you could be booting from there?

I'm not speaking for Bucky Ball, but yes you can do that.  You can have a desktop or laptop with nothing more than a flash drive, size would be the big difference.

---

### Post by sudodus on 2014-07-12
It works well with linux. But there is a problem. It is not possible to boot Windows from a USB drive.

---

### Post by Bucky Ball on 2014-07-12
> **sudodus said:**
> It works well with linux. But there is a problem. It is not possible to boot Windows from a USB drive.

How about if it's booted from the grub list so it boots to grub first, or am I talking some kind of madness? ;) :-k

---

### Post by sudodus on 2014-07-12
I [s]think[/s] thought that Microsoft does not *want* Windows to boot from USB, but I don't know the details (and if there are differences between the versions).

Edit: I found this link, it seems possible using the right version of Windows and or the right tools.

[http://lifehacker.com/how-to-run-a-portable-version-of-windows-from-a-usb-dri-1565509124](http://lifehacker.com/how-to-run-a-portable-version-of-windows-from-a-usb-dri-1565509124)

---

