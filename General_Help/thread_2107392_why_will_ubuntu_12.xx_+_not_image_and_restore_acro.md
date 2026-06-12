---
title: "why will ubuntu 12.xx + not image and restore? acronis / clonsezilla etc"
date: 2013-01-21
forum: General Help
---

### Post by thecheekymonkey on 2013-01-21
hi, for ages i have been using acronis true image home 2012 with ubuntu 10.10 and below, both 32 bit and 64 bit, creating images and restoring to same hardware and different hardware no problem, however now have updated to ubuntu 12.04 and 12.10 both 32bit and 64bit.

images fine, but upon restore get varying errors from reboot loops to grub error (unknown file system etc etc)

tried on different hardware, and sam, no go.

tried with clonezilla extactly same issues.

used new hardware to setup and do new images but same issue.


in fairness, if i image a machine and restore to same machine its fine, but if i restore to a different machine (even though identical hardware) wont work, same issue


any ideas?

cheers

---

### Post by sidzen on 2013-01-21
C'mon, you know better than try to mix 32-bit and 64-bit!

---

### Post by offgridguy on 2013-01-23
> **sidzen said:**
> C'mon, you know better than try to mix 32-bit and 64-bit!
Not sure what you are getting at ? I use both 32bit and 64 bit, depending on the computer.

---

### Post by orb9220 on 2013-01-23
Please clarify exactly the steps you do on what hardrive? What is it you are doing as an example?

As I use [Redo Backup]("http://redobackup.org/") which uses same engine under the hood as Clonezilla.
Just a lot easier and simple to use. And have zero issues or problems.

And full backup is my triple boot system 5 partitions Win7,Winxp & Linux.

And have installed different flavors on the linux partitions and then backed those up also on my external ntfs usb drives. So can swap and restore whatever flavor I want in 20 mins.

One thing to note if backing up only linux partitions then you have to also include where grub is install on 1st drive sda0? 1?

Personally I chain load grub as what to have my Win7 loader left untouched and install grub on / partition and just use easyBCD to insert the linux grub location in the win7 loader.
.

---

### Post by thecheekymonkey on 2013-01-24
> **orb9220 said:**
> Please clarify exactly the steps you do on what hardrive? What is it you are doing as an example?

As I use [Redo Backup]("http://redobackup.org/") which uses same engine under the hood as Clonezilla.
Just a lot easier and simple to use. And have zero issues or problems.

And full backup is my triple boot system 5 partitions Win7,Winxp & Linux.

And have installed different flavors on the linux partitions and then backed those up also on my external ntfs usb drives. So can swap and restore whatever flavor I want in 20 mins.

One thing to note if backing up only linux partitions then you have to also include where grub is install on 1st drive sda0? 1?

Personally I chain load grub as what to have my Win7 loader left untouched and install grub on / partition and just use easyBCD to insert the linux grub location in the win7 loader.
.

yeah, as i do a full backup it does the BR as well, works fine with ubuntu 10.10 32bit (havent tried 64bit 10.10) but anything above that, i.e. 12.04 or 12.10 both 32bit and 64bit doesnt want to work. i backup the same way, i have tried redo/clonezilla/acronis true image home (varying versions) all the same.

it will make the image, and it will restore the image but on reboot it comes up with a n error, either reboot loop before it gets to grub screen or grub error . yet the ubuntu 10.10 image, works 100% so im thinking something has changed with grub from ubuntu 10.10 to the newer verion 12+???????


also not sure what you mean about mixing up 32bit and 64 bit??  im not mixing anything up lol

---

### Post by orb9220 on 2013-01-24
Hmmm Strange as all my flavors and OS'es are 64bit except winxp.

Ubuntu 12.10,Mint 14 Cinnamon,Fuduntu 13.1 & Voyager 12.10 xfce.

And wasn't me about the mixing 32bit-64bit reference.
.

---

### Post by cordain54 on 2013-01-25
> **thecheekymonkey said:**
> hi, for ages i have been using acronis true image home 2012 with ubuntu 10.10 and below, both 32 bit and 64 bit, creating images and restoring to same hardware and different hardware no problem, however now have updated to ubuntu 12.04 and 12.10 both 32bit and 64bit.

images fine, but upon restore get varying errors from reboot loops to grub error (unknown file system etc etc)

tried on different hardware, and sam, no go.

tried with clonezilla extactly same issues.

used new hardware to setup and do new images but same issue.


in fairness, if i image a machine and restore to same machine its fine, but if i restore to a different machine (even though identical hardware) wont work, same issue


any ideas?

cheers

I am having the exact same issue with Ubuntu 12.04 and Linux Mint 14.1. (32 Bit).
Tried it on several machines with identical hardware.
I always end up in a boot loop.
Workes fine with Win7, Ubuntu 10.04.

I also tried restoring the image with Acronis 2013 trial, same result (you cannot create new images with the trial version).

---

### Post by cordain54 on 2013-01-25
I just installed Win7 and Ubuntu 12.04 alongside.
I made an image of the whole harddisk, and the recovery worked on a different machine. (could boot into both OS via grub)
Unfortunately, I can't explain why.

---

### Post by thecheekymonkey on 2013-01-27
> **cordain54 said:**
> I just installed Win7 and Ubuntu 12.04 alongside.
I made an image of the whole harddisk, and the recovery worked on a different machine. (could boot into both OS via grub)
Unfortunately, I can't explain why.


yeah its a difficult one, i dont know, ubuntu 10.10 works fine, but anything higher wont for me, no matter what hardware or image software i use, anyone any ideas?

---

### Post by thecheekymonkey on 2013-02-04
anyone?  cheers

---

### Post by Smokin Whale on 2013-02-21
Restoring a backup fails because it cannot backup the grub bootloader. You can however, backup and restore without grub (if it throws and error during the backup or restore process, simply ignore it).

You will then need a utility such as Boot Repair to re-write the grub bootloader.

It's very annoying. I wish there was a decent imaging tool for Ubuntu. Hence why I spend most of my time on Windows machines these days.

---

