---
title: "cloning a partition"
date: 2007-01-26
forum: General Help
---

### Post by neill on 2007-01-26
hi

after much tweaking and adjustment i have my 6.06.1 installation just as i want it :) 

i have 2 HDDs - one for / and one for /home

both are backed up to an external drive nightly

what i'm concerned about is the / drive suffering a physical failure 

(having played for years and years with PCs without problems this has happened twice to me in the last year - luckily without data loss but a *lot* of effort to entirely restore the OS and apps)

can i do a bit-for-bit backup of / (actually of the entire partition i suppose) such that in the event of a drive death i could simply stick in a new drive and clone the old one from the backup ?

i take it it's not  simply a matter of copying back a previously backed up / ?

presumably there would then be boot issues with GRUB, even if all the files were intact - correct ?

or can i shortcut it - so if i get drive death i reinstall from CD and then copy across what i need to get back to where i want. in this case what **do **i need ?

(i know this sort of thing is possible in windoze -which i am trying hard to get way from - using proprietary software when just copying c: to the new drive don't work! damn the registry !!)

thanks for any advice or pointers

neill

---

### Post by laidback on 2007-01-26
neill,

I've used Gparted to create a copy of my / partition (whole disc for me) which I wrote to a USB HD which has partitions at least as big as the original. To check that it worked I then created another "original" on a separate HD, in other words copied the "backup" back onto a new bootable HD. I use caddies so this is quite easy for me as I can exchange HDs with ease. I then booted from this copy, all was well, it appears and performs as the original did. 

To provide further security I put this copy HD into another PC ( I have 2, a reserve that has been thrown out by somebody else) and switched on. I didn't really expect a fully working system but that is what I got, quite amazing. Both PCs are rather old AMDs running Athlons but have different mobos, ram, video cards etc.

You'll need to create a bootable Gparted cd, the Gparted web site has the ISO that you can copy down and burn (Google search will find it). You cannot copy HDs that are mounted so the basic idea is to boot from the Gparted cd and use it to copy over your regular HD onto another one. As I have a USB HD system as well as the standard IDE set up this simply meant copying from one HD to another. Gparted shows the way, it functions in much the same way as it would do if you ran a copy within Ubuntu.

This will not be the most space friendly way of backing up your system, and it takes a little time to set up, but once done it allowed me to create clones with ease. My copies take under 30mins, I'm using 10-12Gb discs. As it copies the entire disc I don't expect the time to increase as the disc fills up. I use Ubuntu 6.06LTS. It also means that the "backups" are available "online" as they are stored on my 250GB USB HD which can be mounted simply by switching it on, Ubuntu automounts these drives. I'm very happy with the setup and feel more secure than I have ever done before. The copies are stored in preformatted logical partitions of around 14Gb, slightly larger than the original just to be on the safe side.

As a by product a bootable Gparted cd allows disc management too, i.e. changing partition sizes etc.

Hope this helps.

Ubuntu rocks.

---

### Post by CocoAUS on 2007-01-26
You could make an image using [SystemRescueCd]("http://www.sysresccd.org/Main_Page").  It's a bootable CD, and it will make a bit-for-bit copy of whatever partition you want, giving you 3 options for compression (none, medium, or high).  It took about 10 minutes for me to backup my entire Ubuntu install this way, so if anything goes wrong, all I have to do is use the CD to restore the image I created.

Also, unlike other methods, this method doesn't copy empty bits.  Some backup programs copy the entire harddrive, but SRC only copies information.  In other words, if you have an 80 gig hdd with only 6 gigs of data on it, SRC will only image the 6 gigs of data, rather than making an entire 80 gig image.

It works great, and it's pretty easy to use.  Hope that helps.  If you've got questions, let me know.

---

### Post by neill on 2007-01-26
that sounds brilliant - exactly what i'm after

i've used gparted before off a CD to clear up old drives before reusing them so i'll give this a try

thanks very much for your help :D

---

### Post by neill on 2007-01-26
thanks too CocoAUS

with SRCD where do you store the image - on a USB drive ?

how is the compression done ? is that something you can decompress on the fly if you need the image or do you need to boot into SRCD first ?

neill

---

### Post by energiya on 2007-01-26
Use [Partimage]("http://www.partimage.org/Main_Page").
> 
Description: Partition Image is a Linux/UNIX utility which saves partitions in many formats (see below) to an image file. The image file can be compressed in the GZIP/BZIP2 formats to save disk space, and split into multiple files to be copied on removable floppies (ZIP for example), ... Partitions can be saved across the network since version 0.6.0.


---

### Post by gh0st on 2007-01-26
This is a really cool guide on backing up your system with PartImage. That's what's on the System Rescue CD. I found when I first tried PartImage it wasn't as straight forward as I thought.

[http://www.debianadmin.com/backup-and-restore-linux-partitions-using-partimage.html](http://www.debianadmin.com/backup-and-restore-linux-partitions-using-partimage.html)

You might find it useful.

---

### Post by kosmic on 2007-01-26
You can also use ***Rsync*** or ***dd*** comand ;)

---

### Post by wieman01 on 2007-01-26
Just if you need a HOWTO on Partimage, check this out:

[http://www.ubuntuforums.org/showthread.php?t=287522]("http://www.ubuntuforums.org/showthread.php?t=287522")

---

### Post by laidback on 2007-01-27
Isn't it great, as with other threads so much comes out of the first question that also helps others. Thanks to cocoAUS I now have a copy of the System rescue CD having downloaded the ISO last night. All I have to do is learn how to use it. First indications are that there is a lot within it including Gparted.

So much to learn...but with the Forum on hand it's fun and instructive. The links above will also prove useful, so thanks for those too.

Kindest regards.

Laidback :)

---

### Post by Dragon43 on 2007-03-07
> **kosmic said:**
> You can also use ***Rsync*** or ***dd*** comand ;)

Please, a step by step for a new guy.

I would like to use the dd but I have no clue how to do it.

Thanks....

---

### Post by Dragon43 on 2007-03-07
An update:

I finally got a copy / clone made using the "Ubuntu" live CD and used the terminal on that to get the clone of my 41 Gig's drives done in 57 minutes by using the command that **MrC** led me to with hints from a lot of people.  

I used {ubuntu@ubuntu:~$ sudo dd if=/dev/hda of=/dev/hdc bs=1M}  hda and hdc are the two physical places of my hard drives.  'a' is master on IDE 0 and 'c' is master on IDE 1.

I have the 'Rescue' CD now and the G4L CD and I will keep trying to get them to work for me also.  Lots to learn and now that I have a good copy of my work to this point, I'm using the back-up or clone HD now with the original in a drawer, I can now mess things up without fearing I will lose it all.....

I will add this back up to the ones I do on my Win boxes on a regular basis.

Thanks for all the help, suggestions and patience you have extended to this new guy.  I will be asking more questions you can be sure.

Dragon43

---

