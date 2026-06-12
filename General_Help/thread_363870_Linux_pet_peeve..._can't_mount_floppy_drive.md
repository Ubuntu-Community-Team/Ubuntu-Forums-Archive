---
title: "Linux pet peeve... can't mount floppy drive"
date: 2007-02-17
forum: General Help
---

### Post by tiger.woods on 2007-02-17
This is why I personaly think Linux doesn't stand a chance in taking over windows... 

Can someone point out to me what I'm doing wrong. I'm running Ubuntu Edgy and trying to mount the floppy drive #sudo mount /dev/fd0 /media/floppy and getting the following error.

mount: dev/fd0 is not a valid block device

Just struggling with some of the basics...

---

### Post by solar george on 2007-02-17
Try from within gnome (or what ever you are using) using the file manager (nautilus for gnome)

---

### Post by Maestro23 on 2007-02-17
Thread might help: [http://www.ubuntuforums.org/showthread.php?t=362703&highlight=floppy+drive](http://www.ubuntuforums.org/showthread.php?t=362703&highlight=floppy+drive)

---

### Post by kircher on 2007-02-17
is the floppy drive in /etc/fstab? I thought you could only use the mount command for devices that are listed in there.

Edit: Actually, my bad, the floppy drive is in fstab. On my machine anyhow

---

### Post by gradedcheese on 2007-02-17
> This is why I personally think Linux doesn't stand a chance in taking over windows... 

That's a bid knee-jerk, no?

kircher -- no, you can mount anything you want explicitly.  fstab defines what's mounted automatically (mount -a) and how it's to be mounted.  Generally, you need to specify a file system:

sudo mount **-t vfat** /dev/fd0 /media/floppy

when you mount.  Floppies are FAT16 unless otherwise formatted, fvat handles that.

---

### Post by dbott67 on 2007-02-17
You can always just add the '**disk mounter**' icon to the toolbar.

1. Right-click the top toolbar
2. Select '**+ Add to Panel..**.'
3. Select '**Disk Mounter**' from the '**System & Hardware**' section.

-Dave

---

### Post by meng on 2007-02-17
Yeah, that's a real OS-killer, especially since floppy drives are considered obsolete. :D

---

### Post by tiger.woods on 2007-02-17
> sudo mount -t vfat /dev/fd0 /media/floppy

It mounted, thanks, but I don't permission to write to it.... ha!ha!ha! so many hoops to jump through to copy a file or 2... frustrating!

> Yeah, that's a real OS-killer, especially since floppy drives are considered obsolete.

Hence the reason it should be easy... why can't it just identify when I load a floppy to mount it on it's own...

---

### Post by gradedcheese on 2007-02-17
> 
It mounted, thanks, but I don't permission to write to it.... ha!ha!ha! so many hoops to jump through to copy a file or 2... frustrating!


Look, I'm usually very polite on this forum and I don't mind helping new users and all that.  However your attitude is really terrible.  So I am going to tell you a few things and let you decide what you want to do: 

1) You don't know much about 'mount' (which is perfectly ok) and this is why you are frustrated.  

2) hint: no-write without sudo is the default behavior, you are welcome to mount a file system as read/write by users, it's very easy to do.  Or you can "sudo cp file_name /media/floppy/" if you prefer.

3) we can either discuss this in a more pleasant manner (hint: I am not "dell tech support") and I will happily explain to you how to use 'mount' and fstab so that you don't have to 'jump through hoops' or you can read about the tools you're using and solve the problem.

---

### Post by tiger.woods on 2007-02-17
gradedcheese,

You are correct and I apologize to the forum for my behavior you've got to admit that it's a fairly convoluted process to read/write to a floppy...

I'd like to opt for option 3... with a more upbeat attitude.

My current fstab is as such:

/dev/   /media/floppy0    auto   rw,user,noauto   0    0

---

### Post by meng on 2007-02-17
> **tiger.woods said:**
> /dev/   /media/floppy0    auto   rw,user,noauto   0    0
/dev/**fd0**   /media/floppy0    auto   rw,user,noauto   0    0

---

### Post by gradedcheese on 2007-02-17
Ok, reading the fstab entry left to right:

1) this is the device name, in this case it should be "/dev/fd0"
2) this is the mount point (which is fine)
3) this is the file system, which should be vfat, but 'auto' means "figure it our yourself" (also ok)
4) these are options, I suggest "rw,user,noauto" which means "read/write, users have access".  'noauto' says "don't assume there's a disk in the drive", essentially.
5) these last two are 'dump' and 'pass' options, I think for a floppy 0 0 is fine.  'dump' is irrelevant, and 'pass' means that the drive will be checked on boot by fsck (which you don't want)

so, please try:

```

/dev/fd0 /media/floppy0 vfat rw,user,noauto 0 0

```

EDIT: or what meng suggests, which is fine too especially if you'll use some non-FAT floppies.  You will want to use FAT on your floppies if you expect Windows to read them -- Windows has pretty much no support for file systems that aren't its own (FAT and NTFS) out of the box unlike, say, Linux ;)

---

### Post by solar george on 2007-02-17
Have you tried using the disk mounter applet in gnome - that should give you read/write access to the drive.

---

### Post by tiger.woods on 2007-02-17
> EDIT: or what meng suggests, which is fine too especially if you'll use some non-FAT floppies. You will want to use FAT on your floppies if you expect Windows to read them -- Windows has pretty much no support for file systems that aren't its own (FAT and NTFS) out of the box unlike, say, Linux 

Point taken.

> /dev/fd0 /media/floppy0 vfat rw,user,noauto 0 0

So, does that then allow any "user" to mount and rw to the floppy?


SolarGeorge,

I'm running Kubuntu, I would assume it has a disk mount application as well?

---

### Post by meng on 2007-02-17
Under System > Admin > Users and Groups, you can set user privileges including whether or not they have access to floppy drives.

---

### Post by tiger.woods on 2007-02-17
Just so that I'm clear.

I still must mount and unmount the floppy before it's ready for use correct? It will not automount when a disk is inserted?

TW,

---

### Post by gradedcheese on 2007-02-17
it should automount it for you, much like a CD-ROM.  The 'auto' option (vs 'noauto') just tells it whether to try and mount at bootup (which only makes sense for permanently-connected hard disks and the like).  So 'noauto' is actually appropriate here.

There's a side note though: I don't think that PC floppy drives tell the OS that there's a disk in the drive (someone please correct me if I'm wrong).  If that's correct, then the OS has to periodically check the drive.  I am not sure if Linux does that anymore, it used to (that's probably what the 'disk' applet they are suggesting does) but it might not now that few people use these drives.  The old Apple Macintosh, on the other hand, had its own floppy controller, and that one would tell Mac OS that there's a disk.

---

### Post by aysiu on 2007-02-17
I've retitled the thread to more accurately describe the problem.

---

### Post by 3rdalbum on 2007-02-17
(I apologise - my post was very insensitive and completely unhelpful. Good luck getting your floppy drive working.)

---

### Post by Maestro23 on 2007-02-17
> **3rdalbum said:**
> Because you can't use your 1.44 megabyte floppy disk drive? I mean no disrespect, but that's going into my blog under "Worst reason yet why Linux isn't ready for the desktop".

[COLOR="Red"]Now, where did I put that stack of punchcards?[/COLOR]

Too funny.:)

---

### Post by aysiu on 2007-02-17
Floppies and dial-up should be supported, but I'm hoping they're on their way out eventually.

---

### Post by jake3988 on 2007-02-18
Sorry if this has been mentioned already, but I mount floppies using the built-in floppy disc mount command:  fdmount.

```

sudo fdmount fd0 /media/floppy0

```

And viola, mounted floppy.

---

### Post by the79bomb on 2007-03-18
> **meng said:**
> Yeah, that's a real OS-killer, especially since floppy drives are considered obsolete. :D

Windows doesn't seem to think so.  They seem to have stock in floppy drives as they insist on keeping them alive just to install the RAID driver during OS install.

---

