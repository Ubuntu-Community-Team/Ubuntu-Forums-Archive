---
title: "DD Image - What does NOT get copied?"
date: 2016-02-02
forum: General Help
---

### Post by Alan5127 on 2016-02-02
I recently posted a [question]("http://ubuntuforums.org/showthread.php?t=2309377") about losing my GRUB2 menu after restoring from a DD image - that has now been solved.

My followup question is:  Why would a restore of a full disk image not bring my machine back into exactly the state it was in when I created the image?  Does DD not copy 'everything'?

For reference, this is the situation I described in the linked thread:

> I decided to move my laptop Windows install from Win8.1 to Win10 last week.

Before doing so, I created a full disk image of the HDD (/dev/sda) using DD.

I then clean installed Win10, followed by Ubuntu 15.10, and as expected  when the laptop booted, I got the GRUB2 menu, from where I could choose  either Win10 or Ubuntu 15.10.

While configuring Win10, I realised I wanted to replicate some settings  from Win8.1, so I imaged the HDD with Win10 / Ubuntu 15.10 on it using  DD, restored the Win8.1 image, booted into Win8.1 and copied the  settings I wanted, then restored the Win10 / Ubuntu 15.10 image of the  HDD.

The restore seemed to work perfectly, but when I boot the laptop, it  boots straight into Win10, without the GRUB2 menu coming up.


As mentioned - the situation is resolved, I am now asking 'out of interest', and so that I can make sure I am creating images in the best, most robust way.

Thanks,

Alan.

---

### Post by LostFarmer on 2016-02-02
I suspect that your hdd is GPT partitioned.  When you installed Win10 , did you delete and then remake the  EFI partition or format it ?  If so, that likely caused the problem.   when Win10 and Ubuntu was installed it rewrote the firmware boot entire and the efi partition , start sector # ,size and UUID # is recorded, if that information becomes wrong (when you put the image back)  the firmware likely deleted the ubuntu entire and rewrite the Windows entire.  All computer companies do things different so not sure.

---

### Post by sudodus on 2016-02-03
There are also some general problems with cloning:

- A drive with an MSDOS partition table can be cloned to another drive of at least the same size (not smaller).

- A drive with a GUID partition table (GPT) has a second partition table at the tail end of the drive. This means that there will be some corruption if the target drive has not exactly the same size.

In other words,

- it is not straightforward to clone a drive with GPT into a larger drive (but it might work after some repair)

- you cannot expect cloning to work to a smaller drive.

---

### Post by Alan5127 on 2016-08-03
Hi Guys,

Firstly, apologies for not responding earlier.  I have no idea how I missed this.


@LostFarmer:

Yes - My drive is GPT not MBR (?) I think.  If I do a 'sudo gdisk -l' it works, whereas 'sudo fdisk -l' does not.

I am not sure if I deleted and then remade the  EFI partition or formatted it.  Likely I accepted whatever Win10 had as default.  However, I was expecting that restoring the image would just completely put everything back the way it was before.


@sudodus:

I was restoring the image to the exact same hardware, so I don't think that disk sizes could have come into it?


Thanks,

Alan.

---

### Post by carl4926 on 2016-08-03
Restoring an image has never failed for me, but I can't recall if it involved GPT

And FYI I use ddrescue with ionice to both copy and restore

An example of a copy would be
```
ionice -c3 ddrescue /dev/sda /media/sdc1/laptop.iso
```

Of course, your source and target may vary

The target must be as big or bigger than the original HDD/SSD

---

### Post by Alan5127 on 2016-08-03
Hi Carl,

Given you are using ionice, am I correct in thinking that you are running this while the machine is in use, or am I misunderstanding that?

I always tend to image my machine from a boot cd, and image the entire disk to an external USB HDD.

I use:

dd if=/dev/sda conv=sync,noerror bs=64K of=/media/...../sda.img


What do you see as the advantages (and disadvatages) of ddrescue over dd?


Thanks,

Alan.

---

### Post by 4kh3RAm on 2016-08-03
> **carl4926 said:**
> Restoring an image has never failed for me, but I can't recall if it involved GPT

And FYI I use ddrescue with ionice to both copy and restore

An example of a copy would be
```
ionice -c3 ddrescue /dev/sda /media/sdc1/laptop.iso
```

Of course, your source and target may vary

The target must be as big or bigger than the original HDD/SSD

When you mentioned "restoring an image" it got me thinking.

How does it differ from doing a disk image ?

Does it make an exact copy letting you revert to a previous state ?

---

### Post by Alan5127 on 2016-08-03
> **4kh3RAm said:**
> When you mentioned "restoring an image" it got me thinking.

How does it differ from doing a disk image ?

Does it make an exact copy letting you revert to a previous state ?



Hi 4kh3RAm,

Yes - in theory, if you create a disk image, it is an exact copy of the disk at the point in time that the image was created.

In the event that you want to revert your disk to that state, you can restore the image.

I use the expression 'in theory' as the starting point of this thread is that it appears that there are potentially some 'bits' of a system that are not captured and / or restored when doing a full disk image using, at least, dd.

In my reply to Carl, I also asked if he is creating the image from a running system.  This is something I have never been comfortable with, since it seems to me that to get a fully coherent image, the disk that is being imaged must be in the same state throughout the entire process of creating the image - something that does not seem possible if I run the image creation form the disk being imaged, and hence why I always create my images from a live boot cd.

Having said all that - I am no expert on this subject!

HTH,

Alan.

---

### Post by 4kh3RAm on 2016-08-03
> **Alan5127 said:**
> Hi 4kh3RAm,

Yes - in theory, if you create a disk image, it is an exact copy of the disk at the point in time that the image was created.

In the event that you want to revert your disk to that state, you can restore the image.

I use the expression 'in theory' as the starting point of this thread is that it appears that there are potentially some 'bits' of a system that are not captured and / or restored when doing a full disk image using, at least, dd.

In my reply to Carl, I also asked if he is creating the image from a running system.  This is something I have never been comfortable with, since it seems to me that to get a fully coherent image, the disk that is being imaged must be in the same state throughout the entire process of creating the image - something that does not seem possible if I run the image creation form the disk being imaged, and hence why I always create my images from a live boot cd.

Having said all that - I am no expert on this subject!

HTH,

Alan.

I hear you.

```
I use the expression 'in theory' as the starting point of this thread is  that it appears that there are potentially some 'bits' of a system that  are not captured and / or restored when doing a full disk image using,  at least, dd.
```

dd is good, but does not always work with isos.

When I was running Windows XP, I used a disk image program that was flawless.

If I got malware or a virus, or my system got corrupted, I just booted from a rescue disk and restored to a previous state.

**Never** any failures.

I have been using Clonezilla.

I will be shortly restoring an image to see if it works.

Wish me luck. :-)

---

### Post by Alan5127 on 2016-08-04
> **4kh3RAm said:**
> I hear you.

dd is good, but does not always work with isos.



Just to clarify - do you mean ISOs (for example, a DVD image)?

If so, good to know, but I am never creating ISOs of CDs or DVDs - I am only ever using DD to image a HDD.


> **4kh3RAm said:**
> I hear you.

When I was running Windows XP, I used a disk image program that was flawless.

If I got malware or a virus, or my system got corrupted, I just booted from a rescue disk and restored to a previous state.

**Never** any failures.

I have been using Clonezilla.

I will be shortly restoring an image to see if it works.

Wish me luck. :-)


This was my first experience of ever having an issue in probably 15 years of using dd to create backup images.  It is an unusual situation - I have never run an upgrade on Windows from one version to another, and certainly not with a UEFI or GPT setup (too new) before.  All my previous Windows upgrades have been installed to a completely blank HDD then install Linux afterwards.

It would be interesting to know if other software such as CloneZilla would exhibit the same problem in the same scenario.

Alan.

---

### Post by oldfred on 2016-08-04
The issue may not be dd, but UEFI.
But with gpt, you should only image the entire drive as gpt has GUID in both partition and both main & backup partition tables. If they get out of sync it can cause issues, but may be repairable with sgdisk.

But UEFI forgets NVRAM issues if a drive is disconnected. 
So if you boot with blank drive or remove ESP - efi system partition, or install another system, it may forget old entries and use a new default in boot order. And many UEFI seem to always find the Windows entry and make it first in boot order.

---

### Post by carl4926 on 2016-08-04
> **Alan5127 said:**
> Hi Carl,

Given you are using ionice, am I correct in thinking that you are running this while the machine is in use, or am I misunderstanding that?

I always tend to image my machine from a boot cd, and image the entire disk to an external USB HDD.

I use:

dd if=/dev/sda conv=sync,noerror bs=64K of=/media/...../sda.img


What do you see as the advantages (and disadvatages) of ddrescue over dd?


Thanks,

Alan.
Not in use
Running Parted Magic live from RAM

---

### Post by carl4926 on 2016-08-04
> **4kh3RAm said:**
> When you mentioned "restoring an image" it got me thinking.

How does it differ from doing a disk image ?

Does it make an exact copy letting you revert to a previous state ?

It's an exact copy of sda
The entire HDD

Once restored, everything works as it did with the original

---

### Post by Alan5127 on 2016-08-04
Hi Carl,

> **carl4926 said:**
> Not in use
Running Parted Magic live from RAM

In that case, what is the benefit of running ionice, and would those benefits also apply to running dd (rather than ddrescue)?

Thanks,

Alan.

---

### Post by Alan5127 on 2016-08-04
> **carl4926 said:**
> It's an exact copy of sda
The entire HDD

Once restored, everything works as it did with the original


Which has always been my experience with dd too over the last fifteen years or so.  This scenario was the first time it ever 'failed' (and the failure was not catastrophic, just interesting).

I am guessing that ddrescue (wrapped in ionice or not) would have exhibited the same issue probably, as it appears to be doing the same thing as dd under the hood?

Alan.

---

### Post by 4kh3RAm on 2016-08-04
> **carl4926 said:**
> It's an exact copy of sda
The entire HDD

Once restored, everything works as it did with the original

Thanks.

---

### Post by Alan5127 on 2016-08-04
Hi oldfred,

> **oldfred said:**
> The issue may not be dd, but UEFI.
But with gpt, you should only image the entire drive as gpt has GUID in both partition and both main & backup partition tables. If they get out of sync it can cause issues, but may be repairable with sgdisk.

But UEFI forgets NVRAM issues if a drive is disconnected. 
So if you boot with blank drive or remove ESP - efi system partition, or install another system, it may forget old entries and use a new default in boot order. And many UEFI seem to always find the Windows entry and make it first in boot order.

I always image the whole HDD, but your post made me wonder, so I imaged the whole drive, then the four individual partitions that appear to relate to Win10 (Recovery Partition, EFI System Partition, another Recovery Partition, and the main Primary Windows partition - the 'C' drive if you like).  I'm not sure why there are two recovery partitions - one is only 350MB, the other is 5GB, but I did them anyway using:

dd if=/dev/sdaX conv=sync,noerror bs=64K of=/media/..../sdaX.img

For what its worth, I did not backup the Ubuntu partitions, nor the data partition (except in the whole disk image which was my real backup!)

I then opened up Win10 and did some stuff (so that things have now changed including adding a simple txt file to the desktop as a marker), and then restored each of those four partitions individually.

It worked perfectly as expected with no issues, and the Grub boot menu offered me both Ubuntu and Win10 as normal.

So, for what it's worth, for my specific setup here and now, dd seems to be fine backing up individual partitions, and can restore them, but noting that there were no changes to the disk 'structure' in between, even though it is GPT and using UEFI.


Alan.

---

### Post by carl4926 on 2016-08-05
My use of ddrescue and ionice is simply down to best practice as a result of experience
A simple dd may work fine
However, since it may take the best part of a day to image a HDD and often I do it on behalf of a customer. 
I prefer to do it once

---

