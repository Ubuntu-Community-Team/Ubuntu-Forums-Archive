---
title: "[Q] Live usb creation"
date: 2013-01-04
forum: General Help
---

### Post by heWhoWearsAshes on 2013-01-04
I'm creating a live usb on an external hard drive I've got, and the thing that really irks me about the native ubuntu startup usb creator is that it only allows 4 gigs of user space. Any idea how can I get more space?

---

### Post by Zimmer on 2013-01-04
My question to you is 'Why a Live install with more space when you can install it properly to the external USB drive and have as much space as the disk will afford ?'

Also, if you really only want a LIVE install then create a separate partition for your data on the USB drive and 4gig should be sufficient for the  Live OS...

---

### Post by heWhoWearsAshes on 2013-01-04
Yeah, that's the thing, 4 gigs isn't enough for what I need it for. That's why I'm using the external hard drive. 

The reason I'm posting this is cause I had to re-install my live OS cause the old one ran out of space and created some sorta FS error on the disk after I ran an apt-get update/upgrade. I'm aware that I can have another partition for my user space, and I'll prolly end up doing that, but I don't wanna be so frugal with everything else.

Is there a cap to how much space a live OS can occupy?

---

### Post by haqking on 2013-01-04
> **heWhoWearsAshes said:**
> Yeah, that's the thing, 4 gigs isn't enough for what I need it for. That's why I'm using the external hard drive. 

The reason I'm posting this is cause I had to re-install my live OS cause the old one ran out of space and created some sorta FS error on the disk after I ran an apt-get update/upgrade. I'm aware that I can have another partition for my user space, and I'll prolly end up doing that, but I don't wanna be so frugal with everything else.

Is there a cap to how much space a live OS can occupy?

[http://www.pendrivelinux.com/create-a-larger-than-4gb-casper-partition/](http://www.pendrivelinux.com/create-a-larger-than-4gb-casper-partition/)

---

### Post by heWhoWearsAshes on 2013-01-04
Sweet, this is kinda what I was looking for and also kinda what zimmer said.

How does this work? The casper-rw file is where everything is stored normally?

---

### Post by C.S.Cameron on 2013-01-04
> **heWhoWearsAshes said:**
> Sweet, this is kinda what I was looking for and also kinda what zimmer said.

How does this work? The casper-rw file is where everything is stored normally?

The casper-rw file is where changes are stored on a persistent flash drive.

Besides for a casper-rw persistence file you can also have a home-rw persistence file, (just copy and rename an empty casper-rw file). It will store your home data.. this, plus the casper-rw file, will give up to a total of 8GB persistence.

You can also make an ext home-rw partition if you want a separate home partition, the home-rw partition can be reused when upgrading to a new version of Ubuntu, the casper-rw partition can't.

---

### Post by heWhoWearsAshes on 2013-01-05
I have two questions; can you just resize the casper-rw using dd? This link, [http://www.pendrivelinux.com/how-to-create-a-larger-casper-rw-loop-file/]("http://www.pendrivelinux.com/how-to-create-a-larger-casper-rw-loop-file/"), says you can. Is it safe?

And, when you create a casper-rw, or home-rw partition next to a live OS' partition, how will the OS know that it's there? Does it just know, or do I have to write it in somewhere?

---

### Post by C.S.Cameron on 2013-01-05
> **heWhoWearsAshes said:**
> I have two questions; can you just resize the casper-rw using dd? This link, [http://www.pendrivelinux.com/how-to-create-a-larger-casper-rw-loop-file/]("http://www.pendrivelinux.com/how-to-create-a-larger-casper-rw-loop-file/"), says you can. Is it safe?

And, when you create a casper-rw, or home-rw partition next to a live OS' partition, how will the OS know that it's there? Does it just know, or do I have to write it in somewhere?

Sometimes the stuff on pendrivelinux works, (but check for typos). Using dd is never safe in the wrong hands, one typo can wipe your computer.
Of course you can not make a casper-rw file larger than 4GB as size is limited by being FAT32.
I have not tried resizing but it s easy to mount casper-rw to access the files:

[http://ubuntuforums.org/showpost.php?p=7055983&postcount=2](http://ubuntuforums.org/showpost.php?p=7055983&postcount=2)

Ubuntu persistent seems to look for casper-rw in the lowest level first, I am running Ubuntu persistent on an EEE PC, when I boot using a persistent pendrive it sees the EEE's casper-rw partition first.

Just make sure the text.cfg file, (or txt.cfg file depending on version), mentions "persistent", if you installed using Startup Disk Creator. (if you installed using Unetbootin it is the syslinux.cfg file that mentions "persistent".

---

