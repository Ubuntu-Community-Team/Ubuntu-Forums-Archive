---
title: "Is it possible to do a read-only install?"
date: 2007-06-19
forum: General Help
---

### Post by LodeRunner on 2007-06-19
I've been reading [these]("http://ubuntuforums.org/showthread.php?t=71567") [threads]("http://ubuntuforums.org/showthread.php?t=71567") with great interest, but I'm still not entirely sure if what I have in mind is possible.

Basically, I would like to install Ubuntu to a 4 GB USB drive, install all my applications and configure my desktop to my liking, then set it to read-only and have it function as a live CD.  

The "...as a live CD" bit is the tricky part.  Live CDs use SquashFS (and, presumably, ramdisking) which allows applications to create as many files as they need without actually touching hard (or flash) disks.    This is a problem because:

1. SquashFS uses built-in compression, which should be unnecessary if I use a 4 GB drive and strip out a lot of unnecessary apps (I'll use Xubuntu if I must.)  This compression results in a pointless performance hit.

2. There doesn't seem to be an option to use SquashFS (or another read-only file system) in a regular install of Ubuntu,  and other than reconstructor (which doesn't seem configure everything I'd like to configure, e.g. desktop settings, Firefox extensions) there doesn't appear to be a handy way to customize an Ubuntu LiveCD.

Someone else suggested simply doing a normal Ubuntu install (without a swap partition), customizing it to my liking and then marking everything as read-only, but it couldn't possibly be that simple... could it?  I mean, LiveCDs are actually allowed to create and modify files on the fly (they simply do it in RAM alone) whereas marking everything read-only would prevent every single program from making any changes at all, and I'm thinking that would most likely break some stuff (or at least inundate me with errors.)

It's not just about prolonging the life of my flash drive--I'm mainly interested in doing this from a security standpoint.  I want to be able to hash my thumb drive and be able to verify that absolutely nothing is being written to it (after the initial configuration.)  I prefer to use a flash drive (instead of Live CD or DVD) for performance reasons. 

On a more general note, how does SquashFS work--what exactly is / based on when you boot an Ubuntu LiveCD? It's shown as containing 5+ gigs of files, and I only have 2 gigs of ram so obviously it's not a straight ramdisk... sooooo, is SquashFS somehow combining uncompressed files from the LiveCD with ramdisked files (such as those created when I save a file to the Desktop) ?  Or is /home ramdisk and everything else based on the contents of the CD (and thus, truly read-only)?

EDIT: *Apparently* you can create files anywhere on /, so I guess it's somehow blending the decompressed-on-the-fly files from CD with ramdisked files.

---

### Post by smoker on 2007-06-19
hi, not sure about all the technical points you need info on, but this is a good link that may give you some of your answers: [http://www.pendrivelinux.com/](http://www.pendrivelinux.com/)

personally, i have puppy linux on a flash drive, and not that i have had any security problems, but if i had, i could reinstall again in a matter of minutes.

best of luck

---

### Post by LodeRunner on 2007-06-19
> **smoker said:**
> hi, not sure about all the technical points you need info on, but this is a good link that may give you some of your answers: [http://www.pendrivelinux.com/](http://www.pendrivelinux.com/)

personally, i have puppy linux on a flash drive, and not that i have had any security problems, but if i had, i could reinstall again in a matter of minutes.

best of luck

Yeah, I toyed around with Puppy and Damn Small Linux a while back--nice, but I really want something Ubuntu-based. 

Pendrivelinux does have a guide for Ubuntu, but the line "By utilizing multiple partitions, the user can save all changes and settings back to the flash thumb drive" to me implies that it's just a liveCD-type install with an added writable /home directory (mounted from a different partition.)  A step in the right direction, but that still wouldn't allow you to (permanently) install additional programs.  An interesting link nonetheless, thanks.

As far as security goes, there can be nothing more secure than having an OS that is completely write-protected.  You're basically immune to all types of malware (at least, no malware would be able to install itself permanently--I plan on using a drive with a physical write-protect switch) and there isn't a single permanent log, swap file or record of use anywhere.  I agree that this level of security and privacy is excessive for most people, but it wouldn't really get in the way of my regular day-to-day net surfing/coding/document editing (I store most of my stuff online) and it'd be nice to have the peace of mind.

---

### Post by smoker on 2007-06-19
> **LodeRunner said:**
> As far as security goes, there can be nothing more secure than having an OS that is completely write-protected.  You're basically immune to all types of malware (at least, no malware would be able to install itself permanently--I plan on using a drive with a physical write-protect switch) and there isn't a single permanent log, swap file or record of use anywhere.  I agree that this level of security and privacy is excessive for most people, but it wouldn't really get in the way of my regular day-to-day net surfing/coding/document editing (I store most of my stuff online) and it'd be nice to have the peace of mind.

have a look at this, as most of your stuff is stored online:
[http://cl33n.com/](http://cl33n.com/)

---

