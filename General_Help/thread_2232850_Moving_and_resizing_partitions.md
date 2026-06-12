---
title: "Moving and resizing partitions"
date: 2014-07-04
forum: General Help
---

### Post by Mike_Walsh on 2014-07-04
Good evening, one and all.

I've possibly put this in the wrong forum, but I couldn't see one specific to this type of question, so.....

I have Ubuntu 14.04 and Linux Mint, running in dual-boot config. on my elderly Compaq Presario desktop PC. I've been trying various combinations of distros over the last couple of months, and finally found the two I want to keep.

Originally, I wanted Mint as the primary O/S, with Ubuntu as the secondary one, but.... Well, Ubuntu was the first one I tried, and I keep coming back to it, because I REALLY like it.

This time round, I installed Mint first. I then installed Ubuntu second, sizing the partitions to approx 90 Gb for Mint, and 65-70 Gb for Ubuntu. HOWEVER; I would now like to make Ubuntu the larger partition, and Mint the smaller one. THIS is where it's getting me a wee bit confused:-

I've attached a screenshot of gparted, showing the current state of play. I've shrunk the Mint partition down to approx. 50 Gb. I now want to increase the size of /dev/sda6 (the Ubuntu partition) up to approx 90 Gb, and leave myself with about 15-20 Gb of free space....since it never hurts to have some free space to play with.

I shrunk the Mint partition from Ubuntu, which was straight-forward. HOWEVER; I'm unable to resize the Ubuntu partition from within Mint, because when Ubuntu got installed, it appears to have taken the swap file and put it in the extended partition, along with itself; the net result being that I can't do anything with the extended partition, because whichever O/S I'm using, the swap file is of course mounted and in use!

I'd prefer not to have to re-install either of them, since I've just managed to get all the programs and stuff installed which I would like to keep; I'd rather not go through all that again.

I realise that I'm showing my inexperience in this; I'd only just begun to experiment with the disk admin tools in Windows XP shortly before I moved to Linux.

Can any wiser heads help me with this, please? Is it possible to move the swap file OUT of the extended partition, and into the free space, in it's own small partition? I presume this would then allow me to resize the Ubuntu partition from within Mint.....or am I approaching this from the wrong angle?!?

Any advice would be very much appreciated. Thanks!

Mike.

---

### Post by coffeecat on 2014-07-04
Easy and brief answer. Boot up Mint on sda1, open Gparted, right-click on the sda5 swap partition and choose "swapoff". This will unlock the extended partition which you will then be able to extend into the unallocated space. You will then be able to resize the sda6 partition to 90+ GB. Please be warned that resizing the sda6 partition will probably take hours and has the potential for going wrong. As always - back up important data first.

---

### Post by Mike_Walsh on 2014-07-04
Hallo, coffeecat.

Thanks very much for replying.

Me being the impulsive so-and-so that I sometimes am, I decided to take a crack at this myself. I figured out that 'swapoff' probably de-activated the swap partition somehow, but of course I assumed that you had to copy it somewhere so you could re-use it, so I stuck it in the unallocated space. Then I had a go at extending the partition, and made a complete dog's dinner of it; at least (with your advice!) I NOW know exactly what to do if I have to do this sort of thing again...! And rather than risk things going wrong with the partition having to rewrite itself into a different physical location on the disk, I came to the conclusion that it would be quicker, and probably simpler, to re-install.

I'm in the middle of re-installing as I write this. We live and learn, don't we?

It's not a problem, because I've been in the habit of backing stuff up for so many years now, I've honestly lost track. I'm re-installing both of them again, only this time I've made sure I've got the partition sizes correct on the dual-boot install with Mint.

Thanks for your words of wisdom, and I'm sorry to have wasted your time!

(BTW, would you enlighten me on something, please? When I installed Ubuntu last time, as the secondary OS, why did it install itself into an extended partition, and put the swap space for BOTH OSs in there along with it? Why not a straight-forward partition? I would REALLY like to know...it's all info. for future scenarios![lol])

Regards, Mike.

---

### Post by monkeybrain20122 on 2014-07-05
You can clone both OSes with fsarchiver and then reformat/rearrange your drive in anyway you want with gparted with impunity and then simply retsore the OS's to the new configuration. Since uuid is preserved the boot configuration will be preserved even though the drive layout may have changed. Since you can't clone swap of course you have to fix it after reinstall if you have changed the swap partition (edit /etc/fstab and /etc/initramfs-tools/conf.d/resume if you hibernate)

I have done this many times, much faster and safer than using gparted to resize bootable partitions (as long as all are Linux OSes) 

[http://www.fsarchiver.org/QuickStart](http://www.fsarchiver.org/QuickStart)

---

### Post by coffeecat on 2014-07-05
> **Mike_Walsh said:**
> but of course I assumed that you had to copy it somewhere so you could re-use it, so I stuck it in the unallocated space.

Unnecessary. "Swapoff" does precisely that - temporarily disables the swap partition. "Swapon", which you will see when the swap partition is disabled, does the opposite. You can run swapon and swapoff from the terminal as well. 

> **Mike_Walsh said:**
> (BTW, would you enlighten me on something, please? When I installed Ubuntu last time, as the secondary OS, why did it install itself into an extended partition, and put the swap space for BOTH OSs in there along with it? Why not a straight-forward partition? I would REALLY like to know...it's all info. for future scenarios![lol])

If you are going to be using gparted, or any partitioning tool, you really need to know this. The use of extended and logical partitions is a way of getting around the limitations of a mbr partition table, specifically the limit of 4 primary partitions. Windows has to boot from a primary partition - OSs based on Linux can boot from either a primary or logical partition. My guess is that the Ubuntu installer defaults to using logical partitions even when they're not strictly needed to allow for future flexibility. Threads where the OP has become stuck, either because the OEM manufacturer has used up the full allowance of 4 primary partitions - *cough* HP *cough* - or where the OP has done the same through not understanding the limitations of mbr partition tables, are very common here.

An extended partition is simply a special type of primary partition which is used for the sole purpose of acting as a container for logical partitions. That is why you cannot format an extended partition with a filesystem. Primary, or extended, partitions are numbered 1 - 4. Logical partitions are numbered 5 and upwards. If you had told me that your swap partition was sda5, and you had told me nothing else, then I would have known that it was a logical partition from the number. Or rather, had I made the assumption that you had a mbr partition table. Things are different with a GUID partition table (GPT). You don't need to know about GPTs - yet - because you don't have one, but you need to know a little in case you come across theads/blogs/whatever about them and try to apply the advice there to your own situation. That would be unhelpful to you. GPTs allow 128 partitions - they are all "primary", or perhaps the distinction is irrelevant. GPTs are usually seen with newer UEFI machines. That's because later versions of Windows can run on GPT machines so long as they have UEFI, not older style BIOS. All (probably) preinstalled Windows 8 machines are GPT/UEFI. Linux systems can run on GPT and old-style BIOS. But, of course! Apple machines have been UEFI/GPT for years.

---

### Post by Mike_Walsh on 2014-07-05
Thanks, guys, for your advice.

Monkeybrain, I HAD considered cloning the OSs; I've got a 1Tb external Seagate HDD, which is barely 10% full; plenty of room! I was going to use Clonezilla, but the user interface is a bit confusing to a relative newcomer (to this kind of stuff, anyway)., so I decided to 'pass'... I might have a look at this other one you've mentioned (fsarchiver?), and see what I think of that.

Coffeecat, thank you very much for an extremely straight-forward and very clear explanation about the partitions! That's cleared up a lot of my misconceptions in one fell swoop.

I suspect that if I'm going to stay with Linux, which I intend to, then I'm going to have to get the hang of working with partitions sooner or later. There's SO many more distros I want to try out still...

I'm going to have a go with Virtualbox, see if I can install a couple of OSs on that. It's either that, or put them on separate partitions; I don't know of any other ways in which you can have multiple installations. 

One other thing, if I may. This business of the 'swap' space; if you have multiple installations on a hard drive, do they each require their own swap space, or can you get away with a single, common swap area?

(Actually, scratch that. If I put my thinking cap on, I ought to know the answer to that one; you probably CAN get away with a common swap area, since you can only boot a single, real-life O/S at a time. Virtual O/Ss, I'm not too sure about at the moment.....or is my reasoning flawed on what I've just said?)

Regards,

Mike.

---

### Post by stalkingwolf on 2014-07-05
I have a drive with 9 different Os's on it.  I have just one swap partition. My way of doing things is this. I partition the drive im using for testing os's with the swap first. the 4th partition i make a logical then the rest go in there. I have the luxury of having a box set up just for testing and little things. My Main box is dual booted with my two favorites.

Another option is to use usb drives for testing. its a bit slower but you can use them for filtering the ones you want to install.

---

### Post by monkeybrain20122 on 2014-07-05
> **Mike_Walsh said:**
> Thanks, guys, for your advice.

Monkeybrain, I HAD considered cloning the OSs; I've got a 1Tb external Seagate HDD, which is barely 10% full; plenty of room! I was going to use Clonezilla, but the user interface is a bit confusing to a relative newcomer (to this kind of stuff, anyway)., so I decided to 'pass'... I might have a look at this other one you've mentioned (fsarchiver?), and see what I think of that.

.

Clonezilla requires the partition to restore to to be at least as big as the original even if it has barely any data. I would use fsarchiver instead, it just clones the file system. It is easy to use with only two commands (with additional options), one to clone, one to restore.

---

### Post by Mike_Walsh on 2014-07-06
Hi, guys.

Stalkingwolf, yes, you're quite right of course; I could do it that way...I'd forgotten about that. (The number of distro's I've already installed to USB with UNetbootin...ah, me, I'm getting VERY forgetful...)

Monkeybrain, thanks for that. Have you by any chance got a link for fsarchiver, please? It CERTAINLY sounds a lot easier; and would make things a bit more convenient if I DO '****-up' again; which KNOWING me, I'm BOUND to do, sooner or later..!

Mike.

---

### Post by Mike_Walsh on 2014-07-06
Scratch that; it is, of course, in the Software Centre...doh!!

Cheers.

---

### Post by monkeybrain20122 on 2014-07-06
It is in the repo, but still a link to quick start may be helpful.

[http://www.fsarchiver.org/QuickStart](http://www.fsarchiver.org/QuickStart)

---

