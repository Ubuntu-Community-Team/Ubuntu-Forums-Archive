---
title: "How To Move Ubuntu 14.04?"
date: 2014-08-18
forum: General Help
---

### Post by ken0069 on 2014-08-18
I've got a multi-boot system that has Ubuntu 14.04 on an old 40GB IDE hard drive.  Along with an IDE connector that computer has 4 SATA connectors on the motherboard of which 2 are occupied by Windows XP and 7 and one other is occupied by a SATA DVD drive.  I've found out via another system that I can run Ubuntu on a 32GB SATA solid state drive and it's much faster than anything else on the same hardware which brings me to this problem.  

Having said that I've purchased another 32GB SATA SSD and I want to transfer that running copy of Ubuntu 14.04 currently on that 40GB IDE drive to that new 32GB SSD but I have a problem getting clonezilla to move that partition from a 40GB drive to a 32GB drive even though I've used GParted to reduce the size of that Ubuntu partition to 25GB?  Any attempts to clone it result in errors because the "destination drive is too small".  

Oh, and I tried making an image of that 25GB partition via Ubuntu Live disk but the size still comes up to 40GB afterwards so that's not an option as it won't install on that 32GB drive either.

I'm on a limited bandwidth USB mobile broadband connection and hate to waste what little bandwidth that I have available on a clean install and 400+ MB of updates.  

So, is there a way to move Ubuntu to that smaller drive? 

Thanks

---

### Post by dragonfly41 on 2014-08-18
I've taken a note in case I hit the same problem in the future ..

meanwhile .. researching this .. does this guide help you  ..

[http://radu.cotescu.com/migrating-your-ubuntu-machine-to-a-ssd-drive/](http://radu.cotescu.com/migrating-your-ubuntu-machine-to-a-ssd-drive/)

---

### Post by tubos2 on 2014-08-18
Did you try clonezilla's advanced mode ?

---

### Post by ken0069 on 2014-08-18
@ dragonfly41, That link seems to be a little more "in depth" than I'm accustomed to doing, ie, I'm not really that good at command line stuff and was hoping for something that was simple, like Ghost is with Windows. 

@ tubos2, no I didn't use the advanced mode as I don't think I'm experienced enough with Linux to get into that.  I've used clonezilla a few times before but always just went with the "default" settings to date.  

"Real Life" dictates that I won't be able to put any time in this project until later in the week.  Maybe by then someone will have a "fix for idiots" that I can understand and can "get R dun" then. 

Thanks guys and if nothing else turns up I may just try one of these two suggestions and if all else fails then my monthly bandwidth allocation comes fresh again on the 27th of the month.  

@ dragonfly41 again, The other system I have the SSD in already will boot in about 15/18 seconds after P.O.S.T. and it shuts down in less than 3 seconds when I turn it off.  I chose the small SSD size mainly for price as I don't store ANYTHING on a Linux drive because it's a real PITA to get it off if the drive won't boot, been there, done that before.  I have a 1TB NTFS drive in that system for storage for both Windows and Linux.

---

### Post by ken0069 on 2014-08-23
[SIZE=3]Well, no one else has commented on this one but I did get it done today.  I will say I didn't find a "simple" way to do this though as it took me the better part of 4+ hours of trial and error before I was done.

I resized the partition on the new SSD to just a bit over the resized partition on that 40GB IDE drive, ie, both partitions were 25GB with the new drive being just a tick larger because I couldn't make it dead on?  I used a 14.04 live DVD to boot up so I could use both the disk utility and gparted.  Also formatted the new SSD in ext4.

Then I used an older version of Clonezilla to clone the partition over to the new SSD and that went well except Ubuntu wouldn't boot afterwards.  I had tried the latest version of Clonezilla last week but it didn't seem to work the same way this older version did when cloning partition to partition?  

While booted on the live DVD I tried several ways of reinstalling Grub that I found online but kept getting errors so one solution I found was installing Boot Repair.  So, I installed that and that program automatically configured Grub2 and when it was done, so was I as it would boot up in both Linux and Windows XP after it finished.  

So yes, you can clone a larger Linux drive to a smaller one but there are some "hoops" to jump through to get Grub2 and the system back up and running.  

Again, thanks to you guys for trying to help.  Your effort is/was greatly appreciated.  

Ken[/SIZE]

---

