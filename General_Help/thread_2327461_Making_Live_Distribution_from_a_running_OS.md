---
title: "Making Live Distribution from a running OS?"
date: 2016-06-11
forum: General Help
---

### Post by ken55 on 2016-06-11
I just finished setting up an HTPC build in Lubuntu (Sickrage, Plex, etc. ) and would love to be able to throw this on a thumbdrive to be able to let friends see what i've setup and/or let them install it.

Is there an application or a way of doing this?

Thanks,
Ken

---

### Post by Bucky Ball on 2016-06-11
Why do you want to do it from a running install? There are many was to do it without the OS running, in fact, advisable. Cloning a running install can create oddities so wouldn't advise it (did it once and not again). 

You can do it using Clonezilla or fsarchiver, to name a couple. Do a search for Clonezilla, and fsarchiver, along with a lot of other handy things to have around, can be found on the SystemRescueCD. 

You can make a bootable CD/USB of either then boot from that, clone the / partition, clone it back to your target USB, boot from that and fix the boot manager if you need to, then you're done. Sounds simple enough ... :) 

One thing to remember: UEFI or BIOS boot? Your USB is probably going to boot in one or the other. I don't know anything about the ins and outs of all that, but you'll probably need to research and consider.

Just ask if you have questions. There are other ways of cloning partitions, but I've only ever used those two (successfully).

---

### Post by ken55 on 2016-06-11
Thanks for the response, Bucky Ball!

I didn't literally mean "running". I'm just saying cloning the OS that I have running at the moment, the one I am currently using that has all the bells and whistles that I have installed and setup, and making it into a LIVE bootable thumbdrive that someone can just plug and play. 

Unless I am misunderstanding you, you are just telling me to clone the drive, which really isn't what I am looking to do. 

Thanks,
Ken

---

### Post by sudodus on 2016-06-11
If you have only the free drivers (have not installed any proprietary drives, for example for the graphics chip and wifi chip), it might work very well to simply clone the current installed system for example with ***Clonezilla*** as indicated by Bucky Ball. This method works in order to clone to a target drive that is of exactly the same size or larger (but not to a smaller target drive).

Such a cloned drive works in many other computers with linux, which is very different from Windows, where the licensing locks an installed system to a particular computer.

There are other tools and methods to make a working copy in a smaller drive too, for example ***fsarchiver*** and the ***One Button Installer***. The One Button Installer works if your system consists of a root partition and a swap partition, but not if the partition table is more complicated.

It is also possible to do manually, what is done with fsarchiver and the One Button Installer, for example with ***rsync*** or ***tar*** plus ***grub-install*** and some manual tweaks.

-o-

It is possible but more complicated to create a a live drive for this purpose. Then what you do is making a 're-spin' (a simple kind of own linux distro based on Ubuntu's repositories).

---

### Post by ken55 on 2016-06-11
Thanks for the response sudodus. 

"[Respin]("http://www.remastersys.org/")" is what I am looking for, i think.. Unless you know of something better or easier for a noob ;)

Ken

---

### Post by Bucky Ball on 2016-06-11
No. I'm suggesting you clone the partition then clone that using the USB as the target partition. Quite a different fish.

---

### Post by ken55 on 2016-06-11
> **Bucky Ball said:**
> No. I'm suggesting you clone the partition then clone that using the USB as the target partition. Quite a different fish.

Will that make it live bootable?

---

### Post by Bucky Ball on 2016-06-11
Don't see why not. You're cloning a bootable partition image.

As I say, I've used both Clonezilla and fsarchiver to clone and create bootable partitions. If it doesn't boot first time, fixing boot should be relatively easy (Boot Repair or simply reinstalling grub can be your friend here).

I migrated my old hard drive to an SSD about a year ago and used Clonezilla to clone my Ubuntu and WinXP partitions, swapped drives, cloned them back to the SSD and was done. I needed to use Boot Repair to fix boot and that was that. It was a while ago, but probably just reinstalled grub.

(Used fsarchiver to do the same on my laptop and went without a hitch.)

---

### Post by ken55 on 2016-06-11
> **Bucky Ball said:**
> Don't see why not. You're cloning a bootable partition image.

As I say, I've used both Clonezilla and fsarchiver to clone and create bootable partitions. If it doesn't boot first time, fixing boot should be relatively easy (Boot Repair or simply reinstalling grub can be your friend here).
 I feel like we aren't on the same page. Or maybe we are and it's just me..lol 

When I say "live bootable" I mean creating "[FONT=arial]a version of the operating system that can be booted from a [/FONT][B]CD (or a DVD or, in some cases, a USB drive) without actually being installed on the computer's hard drive."  

[/B]
Is that what you are saying as well?
Thanks,
Ken

---

### Post by Bucky Ball on 2016-06-11
You have tweaked your install to just where you want it and now you want to put it on USB or CD/DVD and make it portable. Correct? Please confirm if not.

If so, I'm saying clone your tweaked install / partition to a USB or disk, fix the boot, and there you have it. Portable.

I'm also mentioning that all computers are not going to be using UEFI (for now) so you need to think about that and make sure your portable boot device caters for all situations re. the hardware you intend using it on. Does it boot in UEFI mode? If your USB ONLY boots in UEFI and the device you want to use it on doesn't use UEFI mode, your USB/disk is not going to work. 

This is something I know little about, I could be off the mark, but better find out.

---

### Post by ken55 on 2016-06-11
> **Bucky Ball said:**
> You have tweaked your install to just where you want it and now you want to put it on USB or CD/DVD and make it portable. Correct? Please confirm if not.

If so, I'm saying clone your tweaked install / partition to a USB or disk, fix the boot, and there you have it. Portable.

I'm also mentioning that all computers are not going to be using UEFI (for now) so you need to think about that and make sure your portable boot device caters for all situations re. the hardware you intend using it on. Does it boot in UEFI mode? If your USB ONLY boots in UEFI and the device you want to use it on doesn't use UEFI mode, your USB/disk is not going to work. 

This is something I know little about, I could be off the mark, but better find out.

Yes, I guess we are on the same page. I understand what you are saying now,  I'll have to give that a shot. 

Thank you,

Ken

---

### Post by Bucky Ball on 2016-06-11
[This might help]("https://rbgeek.wordpress.com/2013/04/14/how-to-use-clonezilla-to-backup-hard-drive-and-create-recovery-iso-image/") with Clonezilla. You'll have to go back and follow the steps to make the original clone using your / as the source. 

[SystemRescueCD]("http://r.duckduckgo.com/l/?kh=-1&uddg=http%3A%2F%2Fwww.sysresccd.org%2F") has [fsarchiver]("http://www.fsarchiver.org/QuickStart") on it along with Gparted and a heap of other tools.

You'll probably need Boot Repair or some boot manager tweaking either way. 

Incidentally, fsarchiver may look a bit complicated, but it is actually really easy when you have a good look at the two commands you need, one to create the archive and the other to restore it. Just a matter of getting the source/targets right in each case.

---

### Post by ken55 on 2016-06-11
> **Bucky Ball said:**
> [This might help]("https://rbgeek.wordpress.com/2013/04/14/how-to-use-clonezilla-to-backup-hard-drive-and-create-recovery-iso-image/") with Clonezilla. You'll have to go back and follow the steps to make the original clone using your / as the source. 

[SystemRescueCD]("http://r.duckduckgo.com/l/?kh=-1&uddg=http%3A%2F%2Fwww.sysresccd.org%2F") has [fsarchiver]("http://www.fsarchiver.org/QuickStart") on it along with Gparted and a heap of other tools.

You'll probably need Boot Repair or some boot manager tweaking either way. 

Incidentally, fsarchiver may look a bit complicated, but it is actually really easy when you have a good look at the two commands you need, one to create the archive and the other to restore it. Just a matter of getting the source/targets right in each case.

Will do some playing around tonight and report back and let you know how it goes.

Thanks again,
Ken

---

### Post by Hedon James on 2016-06-11
I personally prefer Systemback to create LiveCD ISOs of my remixed distros.  See if this is more to your liking, specifically Figure B - Live System Create:

[http://www.techrepublic.com/article/create-a-live-system-iso-for-your-ubuntu-based-linux-machines-using-systemback/](http://www.techrepublic.com/article/create-a-live-system-iso-for-your-ubuntu-based-linux-machines-using-systemback/)

---

### Post by Bucky Ball on 2016-06-12
> **Hedon James said:**
> I personally prefer Systemback ...

Looks interesting. Might give it a try for backing up my desktop and laptop later on today. ;)

---

