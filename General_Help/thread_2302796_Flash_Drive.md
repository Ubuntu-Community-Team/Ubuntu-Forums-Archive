---
title: "Flash Drive"
date: 2015-11-13
forum: General Help
---

### Post by shane_faulkinbury2 on 2015-11-13
I have both Ubuntu 15.10 and Windows 10 loaded on my PC.  I have this 64 GB flash drive it has two partitions on it somehow.  One partition is 3.2 GB and how it got on there I have no idea.  Every time I click on the F partition I get the following screenshot!  What I want to know is how I format the flash drive to be seen by both Ubuntu and Windows with one partition?

---

### Post by yancek on 2015-11-13
Do you have any data on the flash drive?  If you format it, the data will be deleted.  Can you access the partition from windows?  Did you try running the fuser command as suggested in the message?  What was the output?  The message also shows it is already mounted.  Have you accessed it in some other manner?

---

### Post by ajgreeny on 2015-11-13
Have you used the flash drive in Windows and not used the Remove properly system on that before unplugging it?  That would mean that it is still marked as "In use" in Linux and unmountable until you have attached it and removed it (unmount equivalent) as you should in Windows.

---

### Post by shane_faulkinbury2 on 2015-11-13
No I didn't!  Do I have to fix it in Windows are can it be done in Ubuntu?

---

### Post by yancek on 2015-11-13
I don't know if it can be 'fixed' in Ubuntu but since it is a proprietary microsoft windows format, I would certainly try it on windows.

---

### Post by shane_faulkinbury2 on 2015-11-13
Well I'm on Windows now and all File Explorer shows is a 3.2 GB flash drive!  When I click format my only options are for NTFS, FAT, or FAT32.  So I guess my only option would be in Ubuntu or just chuck it!  :evil:

---

### Post by ajgreeny on 2015-11-13
Try gparted in ubuntu live system.  It will be interesting to see what that can find.

---

### Post by yancek on 2015-11-13
If you want it to be accessible in both windows and Linux, you will have to format it either fat32 or ntfs as a default windows system is incapable of reading much less writing to a partition with a Linux filesystem.  Are you able to see the second partition from Ubuntu?  What do fdisk and parted commands show, is your disk shown?  Both partitions?

---

### Post by shane_faulkinbury2 on 2015-11-13
On the second partition I get this error!

I wonder how I use the fuser command?

This is all I see with Gparted!

---

### Post by Sweet_Baby_Jamie on 2015-11-14
There is USB formatting software available in the Ubuntu repositories. *Gnome Format* is the one I found searching in Synaptic Package Manager.  I'm not sure if that's what you were asking or not but maybe it'll help someone else.

I got this Flash drive... if I can just keep it (attached image):

---

### Post by Mike_Walsh on 2015-11-14
Hi, shane.

Assuming you have the flash drive in question plugged in, gParted should be able to find it. If you click on the up/down arrows beside '/dev/sda, etc...' top right corner, you'll get a drop-down that will show all drives that gParted can detect. You should find your flash-drive listed here.


Regards,

Mike. ;)

---

### Post by shane_faulkinbury2 on 2015-11-14
How do I find Gnome Format in Synaptic Package Manager?

Mike, as you see from my pic I had the flash drive in.  That's why Gparted was showing Microsoft reserved partition!

---

### Post by Mike_Walsh on 2015-11-14
Hi, Shane.

Hmm. Well; you say your flash drive is 64 GB, yes? I see the USB icon showing in the launcher to the left side of the Unity desktop, but the screenshot of gParted is showing me a 1 TB hard drive (sda).....with the Microsoft reserved partition on **that** highlighted....unless I'm very much mistaken (or you've attached the wrong screenshot). :lol:

Either **that,** or I need new specs!


Regards,

Mike. ;)

---

### Post by shane_faulkinbury2 on 2015-11-14
I don't understand, I have Windows 10 and Ubuntu 15.10 installed on my 1 TB hard drive, but why would the Windows 10 show up as 16 MB?

---

### Post by Mike_Walsh on 2015-11-14
Hi again, Shane.

I think you'll find (going from your screenie of gParted) that your layout is as follows:-

sdas**1**,**3** & **4** are the UEFI/boot-partition stuff for Windows 10.

sda**2** is the UEFI bootloader for Ubuntu. (I'm willing to be corrected on this one, since I've never had to use UEFI stuff myself.....but that's what I believe it to be).

sda**6** is the actual Win 10 system partition (166 GB).

sda**7** is your Ubuntu partition, and 

sda**8** is your Linux-swap partition. 

Now, I'll confess, **I **don't know quite what that 16MB sda**5** is, either; I haven't had anything to do with Windows, post Win 7. But I would hazard a guess that it's **something** to do with system recovery. As I understand it, since Microsoft have completely re-written the rules with Win 10, you don't actually keep the recovery stuff onboard any more.....I believe it's downloaded from the 'cloud' if, as & when it may be required.

That's **my **best estimate of what gParted is showing you, anyway.


Regards,

Mike. ;)

---

### Post by sandyd on 2015-11-14
Can you post the output of
```

sudo parted -l
```

Also, click on the red circled portion in the screenshot below, and choose "/dev/sdb", and then post a screenshot. Gparted only shows one drive at a time; the current one it is showing is simply your internal hard drive (/dev/sda)
[ATTACH=CONFIG]265574[/ATTACH]

---

### Post by shane_faulkinbury2 on 2015-11-15
Here they are!  Hope it helps!

---

### Post by carl4926 on 2015-11-15
Be careful this will wipe the disk
But should make it workable in gparted for format

```
sudo parted -l
```

Identify the usb device
eg /dev/sdb

```
sudo [COLOR=#333333]umount /dev/sdb[/COLOR]
```[COLOR=#333333]
[/COLOR]
```
sudo [COLOR=#333333][FONT=Verdana]dd if=/dev/zero of=/dev/sdb count=100[/FONT][/COLOR]
```

Now look at it in gparted and you should be able to create a partition and format it

---

### Post by shane_faulkinbury2 on 2015-11-15
But why does it say "unrecognized disk label"?

Sorry, didn't add the pic!

---

### Post by sandyd on 2015-11-15
> **shane_faulkinbury2 said:**
> Here they are!  Hope it helps!

Still not the right screenshot, please click on the red circled portion in the above screenshot and change the menu to '/dev/sdb'

---

### Post by shane_faulkinbury2 on 2015-11-15
Thanks Carl4926, that did the trick!  I still wasn't able to change anything on Ubuntu, but fired up Windows and there she was Capacity 64 GB, File system NTFS, Allocation file size 4096 bytes, so reformatted in Windows and fired up Ubuntu and everything is working now!  :D

One more thing, how do you mark a thread as solved?

---

### Post by carl4926 on 2015-11-15
> **shane_faulkinbury2 said:**
> Thanks Carl4926, that did the trick!  I still wasn't able to change anything on Ubuntu, but fired up Windows and there she was Capacity 64 GB, File system NTFS, Allocation file size 4096 bytes, so reformatted in Windows and fired up Ubuntu and everything is working now!  :D

One more thing, how do you mark a thread as solved?

No worries
Happy to assist

---

### Post by sudodus on 2015-11-16
> **shane_faulkinbury2 said:**
> ...

One more thing, how do you mark a thread as solved?


Please click on **Thread Tools** at the top of the page to mark this thread as SOLVED

---

### Post by shane_faulkinbury2 on 2015-11-16
Thanks sudodus!

---

