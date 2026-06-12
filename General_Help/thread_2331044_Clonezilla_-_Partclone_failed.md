---
title: "Clonezilla - Partclone failed"
date: 2016-07-17
forum: General Help
---

### Post by 4kh3RAm on 2016-07-17
Installed Clonezilla to a flash drive.

md5sum was good.

When I tried to save a partition as an image, I got these messages:

1. Partclone failed
2. FS was not cleanly unmounted

How can I fix this ?

Got successful image by using this tip.

[https://sourceforge.net/p/clonezilla/bugs/167/](https://sourceforge.net/p/clonezilla/bugs/167/)

The image size is about 17 Gb.

The drive shows 44 Gb as in use.

I know the image is compressed.

Do those numbers look o.k. ?

---

### Post by sudodus on 2016-07-18
Files are more or less compressed, very much depending on what they contain. It is problably OK, that 44 GB were compressed to 17 GB, but there is only one way to be 100% sure:

Test the image by ***restoring it into another drive*** of at least the same size as the original drive. Do ***not*** take the risk to restore it to the original drive!

Test Clonezilla a few times and when you feel confident with it - how to run it, how to read and interpret the output - you can relax and rely on it without testing except when you want to use it to do something new (for example if there is a new file system or partition table).

---

### Post by 4kh3RAm on 2016-07-18
I have one other drive to test on.

It is only used for storing backup files. I will make sure those files are copied to my main drive.

If I restore image to 2nd drive, how does that work ?

How do I boot to it ?

---

### Post by sudodus on 2016-07-18
If you are cloning the whole drive (not only partitions) it should be straight-forward. Otherwise the imaging operation or restoring operation failed.

After restoring/cloning, everything on the target drive will be overwritten, and the target drive can replace the original drive. So you can unplug the original drive and plug in the target drive, restore, shut down, remove the Clonezilla drive and boot the computer from the cloned copy.

---

### Post by RobGoss on 2016-07-18
> **4kh3RAm said:**
> Installed Clonezilla to a flash drive.

md5sum was good.

When I tried to save a partition as an image, I got these messages:

1. Partclone failed
2. FS was not cleanly unmounted

How can I fix this ?

Got successful image by using this tip.

[https://sourceforge.net/p/clonezilla/bugs/167/](https://sourceforge.net/p/clonezilla/bugs/167/)

The image size is about 17 Gb.

The drive shows 44 Gb as in use.

I know the image is compressed.

Do those numbers look o.k. ?




> When I tried to save a partition as an image, I got these messages:

1. Partclone failed
2. FS was not cleanly unmounted



Are you trying to clone the whole drive?


After cloning is complete were are you trying to save your finshed cloned imaged? are you trying to save it to a external drive

If you're in fact using a external make sure that it is mounted and your machine can detect it. Choose that drive when saving your cloned imaged

---

### Post by 4kh3RAm on 2016-07-18
> **sudodus said:**
> If you are cloning the whole drive (not only partitions) it should be straight-forward. Otherwise the imaging operation or restoring operation failed.

After restoring/cloning, everything on the target drive will be overwritten, and the target drive can replace the original drive. So you can unplug the original drive and plug in the target drive, restore, shut down, remove the Clonezilla drive and boot the computer from the cloned copy.

That's a lot of work switching out drives.

No way to set that drive to boot from ?

> **RobGoss said:**
> Are you trying to clone the whole drive?


After cloning is complete were are you trying to save your fished cloned imaged? are you trying to save it to a external drive
If you're in fact using a external make sure that it is mounted and your machine can detect it. Choose that drive when saving your cloned imaged

I saved cloned image to a separate drive.

I want to test the image to make sure it actually works without messing up my current main drive.

I probably have to copy that image to my main drive before testing it since it would be overwritten.

Seems to make no sense to store image to it's own drive. 

I do not think the software would even allow it. Clonezilla has to lock the drive it is making an image of.

I ask all this because when I had Win XP, they had a program, Macrium Reflect that made disk images.

If my O.S. got corrupted, all I had to do was boot from a rescue flash drive and restore the image.

Good protection against malware, badly written programs, etc. :-)

---

### Post by sudodus on 2016-07-18
You should ***not*** have both the source drive and the target drive connected, when trying to boot from one of them, because they have the same UUIDs. It can cause severe and time-consuming problems.

But you can try to boot another computer from the target drive, and it should work, if there are no proprietary drivers.

> **4kh3RAm said:**
> I saved cloned image to a separate drive.

I want to test the image to make sure it actually works without messing up my current main drive.

I probably have to copy that image to my main drive before testing it since it would be overwritten.

Seems to make no sense to store image to it's own drive. 

I do not think the software would even allow it. Clonezilla has to lock the drive it is making an image of.

I ask all this because when I had Win XP, they had a program, Macrium Reflect that made disk images.

If my O.S. got corrupted, all I had to do was boot from a rescue flash drive and restore the image.

Good protection against malware, badly written programs, etc. :-)

Let us talk about four drives:

1. the Clonezilla boot drive (CD/DVD/USB)

2. the source drive with the original system

3. the drive (for example an external hard disk drive), where you store the Clonezilla image, a directory with several files

4. the target drive; you test the Clonezilla image by restoring to the target drive. This drive should be {the same size as or larger than} the source drive.

---

### Post by 4kh3RAm on 2016-07-18
They do NOT have the same UUID.

If they did, Linux could not differentiate them.

What distro are you running ? Does it show the same UUID for different drives ?

Did you have a question here ?

---

### Post by sudodus on 2016-07-18
If you clone a drive, the partitions in the target drive will have the same UUIDs as the corresponding partitions in the source drive. Otherwise it is not a clone. (If the software would be intelligent enough, it could change the UUIDs and all the corresponding references in system files, but I don't think Clonezilla does that.)

-o-

A question about where to store the image directory and its files? Not a question, I am only suggesting to keep it on a separate drive.

***Edit:*** Please notice that the Clonezilla image cannot be booted from as it is. It must be restored using Clonezilla - restored to another separate target drive.

---

### Post by sudodus on 2016-07-18
See these links for more details:

These links describe how I normally use Clonezilla (to save a disk image, and when necessary restore from the image)

[https://www.geekyprojects.com/cloning/how-to-use-clonezilla-tutorial/](https://www.geekyprojects.com/cloning/how-to-use-clonezilla-tutorial/)
[Save disk image - Clonezilla](http://clonezilla.org/show-live-doc-content.php?topic=clonezilla-live/doc/01_Save_disk_image)

The following link describes how to clone directly to another drive (instead of saving to an image)

[Disk to disk clone - Clonezilla](http://clonezilla.org/show-live-doc-content.php?topic=clonezilla-live/doc/03_Disk_to_disk_clone)

---

### Post by RobGoss on 2016-07-18
> [COLOR=#000000]I saved cloned image to a separate drive.[/COLOR]

[COLOR=#000000]I want to test the image to make sure it actually works without messing up my current main drive.[/COLOR]

[COLOR=#000000]I probably have to copy that image to my main drive before testing it since it would be overwritten.[/COLOR]

[COLOR=#000000]Seems to make no sense to store image to it's own drive. [/COLOR]

When creating the cloned image for your main drive you can save it to a external drive, and if you need to restore your system just put the **Clonezillia **disk into your machine and boot off of that** DVD or USB**, you will be given a option to choose which image you want to restore for your machine simply choose the **external cloned **image and follow the instructions

I've done it many times and it works like a charm for me so I don't see why you would have a problem but every individual has different methods

I do believe **Ubuntu 16.04** has another backup software program that is by default called **Deja backup** [https://launchpad.net/deja-dup](https://launchpad.net/deja-dup) I have not used it yet but from what I've heard it's a pretty good program if all you want to do is backup your files and folders

I prefer just using a cloning method because I don't keep a lot of important data on my machines so I mainly care about a good working system. I can have my system back up and running in about an hour or so if anything goes wrong

---

### Post by RobGoss on 2016-07-18
> [COLOR=#000000]Please notice that the Clonezilla image cannot be booted from as it is. It must be restored using Clonezilla - restored to another separate target drive.[/COLOR]

**Sudodus, **is correct you **cannot **keep the cloned image on the same drive that's being cloned because if something goes wrong you will loose everything

---

### Post by 4kh3RAm on 2016-07-18
> **RobGoss said:**
> When creating the cloned image for your main drive you can save it to a external drive, and if you need to restore your system just put the **Clonezillia **disk into your machine and boot off of that** DVD or USB**, you will be given a option to choose which image you want to restore for your machine simply choose the **external cloned **image and follow the instructions

I've done it many times and it works like a charm for me so I don't see why you would have a problem but every individual has different methods

I do believe **Ubuntu 16.04** has another backup software program that is by default called **Deja backup** [https://launchpad.net/deja-dup](https://launchpad.net/deja-dup) I have not used it yet but from what I've heard it's a pretty good program if all you want to do is backup your files and folders

I prefer just using a cloning method because I don't keep a lot of important data on my machines so I mainly care about a good working system. I can have my system back up and running in about an hour or so if anything goes wrong

Hopefully, one last question.

Doing a image restore has to be done right. I do not enjoy having to reinstall Ubuntu. :-)

So, when you restore an image, do you write it over your primary drive ?

Having big problem posting replies.

Lot of work typing. Getting this when trying to reply. 

> You don't have permission to access /editpost.php on this server.

---

### Post by RobGoss on 2016-07-18
> [COLOR=#000000]So, when you restore an image, do you write it over your primary drive ?[/COLOR]

The answer is **yes,** if you choose to restore your system using the** cloned image** it will replace your existing **OS **with the backup cloned images, so make sure Ubuntu is the only operating system on that machine because if it's a dual boot it will be much more complicated just a heads up   


Take a look at this video it will help you understand how to use Clonezilla it's one of my favorites 

**How to backup and restore with Clonezilla**
[https://www.youtube.com/watch?v=lfoSU1iVW1w&index=2&list=WL](https://www.youtube.com/watch?v=lfoSU1iVW1w&index=2&list=WL)

> **4kh3RAm said:**
> Having big problem posting replies.

Lot of work typing. Getting this when trying to reply.


> [COLOR=#000000]*You don't have permission to access /editpost.php on this server.*[/COLOR]

If you're referring to posting here on the forums it might be the server that Ubuntu is hosted on I would just give it a few minutes it should clear up.

---

### Post by 4kh3RAm on 2016-07-18
> **RobGoss said:**
> The answer is **yes,** if you choose to restore your system using the** cloned image** it will replace your existing **OS **with the backup cloned images, so make sure Ubuntu is the only operating system on that machine because if it's a dual boot it will be much more complicated just a heads up   


Take a look at this video it will help you understand how to use Clonezilla it's one of my favorites 

**How to backup and restore with Clonezilla**
[https://www.youtube.com/watch?v=lfoSU1iVW1w&index=2&list=WL](https://www.youtube.com/watch?v=lfoSU1iVW1w&index=2&list=WL)

Let's be clear on our definitions.

When I boot, I have 3 picks....Ubuntu and 2 versions of Puppy Linux.

I have 3 partitions on my PRIMARY hard drive.

Each has it's own O.S.

When I cloned my PRIMARY hard drive, I cloned the whole hard drive.(i.e. all 3 partitions)

---

### Post by RobGoss on 2016-07-18
> [COLOR=#000000]When I cloned my PRIMARY hard drive, I cloned the whole hard drive.(i.e. all 3 partitions)[/COLOR]


I didn't see any mention of you having **three partitions** on your primary hard drive this may change the instructions that were given a bit

 I'm no Clonezilla expert by no means, but if you're using **three partitions** I think you would have to clone each partition **separately **as an **individual operating system **in order to restore each one if needed[B]

Partition-1 Ubuntu 16.04
[/B][B]Partition-2 Puppy Linux
[/B][B]Partition-3 Puppy Linux

[/B]That way if anything goes wrong you can choose what ever operating system is corrupt or damaged and quickly restore them

---

### Post by 4kh3RAm on 2016-07-18
Thanks.

I will see if Clonezilla offers the option to save individual partitions.

---

### Post by RobGoss on 2016-07-18
> **4kh3RAm said:**
> Thanks.

I will see if Clonezilla offers the option to save individual partitions.

You should be able to even if you have to clone one at a time. If this is your first time using Clonezilla I would suggest learning how Clonezilla works before you attempt to clone your system

---

### Post by 4kh3RAm on 2016-07-18
> **RobGoss said:**
> You should be able to even if you have to clone one at a time. If this is your first time using Clonezilla I would get the feel of it before you attempt to clone your system

I have already cloned my system.

Clonezilla offers NO option to clone individual partitions.

It makes sense if you think about it.

---

### Post by howefield on 2016-07-18
> **4kh3RAm said:**
> Clonezilla offers NO option to clone individual partitions.

Of course it does. "saveparts" and "restoreparts" are the options for partitions.

---

### Post by sudodus on 2016-07-19
Clonezilla can create an image (a directory with several files, where the big files are compressed) of the whole drive also when there are several partitions and installed systems, linux as well as Windows (multi-boot drives). I have done it and I can restore working systems from such an image.

You can also create separate images of the partitions if you wish, and you must understand what difference it makes, when restoring from the image(s). An image of a partition is not a complete system. You will probably need other partitions and or a separate bootloader.

---

### Post by 4kh3RAm on 2016-07-19
Thanks for the detailed info.

---

