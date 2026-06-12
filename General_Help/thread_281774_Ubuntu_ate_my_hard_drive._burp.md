---
title: "Ubuntu ate my hard drive. *burp*"
date: 2006-10-21
forum: General Help
---

### Post by emersony on 2006-10-21
just got a copy of the Ubuntu 6.06 DVD and popped it in for a test drive. 

Everything seemed pretty cool so I decided to create a partition for it with the gnome parted. It saw my  100gig HD as NTFS which it was, and also saw that there were only about 40 gigs worth of files on it. (also it has also just been defragged, so it was clean.) 

Using gparted to size partition 1 down to 50G & create a 2nd partion with ext3 fs: 

clicked apply, it churned, returned that it had failed and that it no longer recognised the main partition's file system. 
It now saw an unknown partion of 100G and a 2nd unknown partition of 0.0G [yike] 

Rebooting the computer, the original install of WinXP is of course now hosed since the partition table is gone. 

Except I would like to get my 40G's of data off this thing so I'd kinda prefer to get the previous partition table back, or anything that will enable me to get my data off. 

So any suggestions would be appreciated, still think Ubuntu is neat, but just want to fix my HD. 

no smileys, 

Emerson

---

### Post by podunk on 2006-10-21
Ouch!

I hope this will help:
[http://ubuntuforums.org/showthread.php?t=180607&highlight=Restore+Windows+Master+Boot+Record](http://ubuntuforums.org/showthread.php?t=180607&highlight=Restore+Windows+Master+Boot+Record)

---

### Post by emersony on 2006-10-21
Thanks Podunk, 

  That's actually the first thing I tried, fdisk /mbr from a dos boot disk. 

   It didn't seem to do anything and partition is still hosed. But yes that would be the obvious thing.

---

### Post by podunk on 2006-10-21
Double ouch! :-(

I read this a long time ago and book marked it just in case - you might give it a read 
[http://www.lifehacker.com/software/disk-recovery/geek-to-live--rescue-files-with-a-boot-cd-192982.php](http://www.lifehacker.com/software/disk-recovery/geek-to-live--rescue-files-with-a-boot-cd-192982.php)

---

### Post by emersony on 2006-10-21
Another good suggestion Podunk. I did already try that (it was an earlier version of knoppix, not 5.0.) and it won't mount the drive because it can't see anything it recognizes as a filesystem.

In the lifehacker example, the boot sector is below the partition table, so even though she can't boot off the drive, her PT is readable. 

There are commercial solutions to this problem, but it would be nice to be able to do it with an Ubuntu/Debian/Knoppix tool kit. 

Emerson

---

### Post by podunk on 2006-10-21
Well! darn. :-(

If it was me before I went the spin rite direction I'd try 2 things I think. I'd slave it into another computer that had linux on it and see if I could get it to mount. If I could I'd read the web like hell 

If that didn't work I'd make a decision about how important my data was. If it wasn't cut your wrists stuff I'd slave into a Xp machine and run check disk on it. I'd guess at a 50% chance of a complete non recover situation.

Of course if it was cut your wrist stuff I'd go download spinrite and get it over with.

Hate it for you. Wish I had the knowledge and skill to do more.:-(

---

### Post by Zimmer on 2006-10-21
[http://ubuntuforums.org/showthread.php?t=113630&highlight=dual+boot](http://ubuntuforums.org/showthread.php?t=113630&highlight=dual+boot)

If you can manage to obtaina  bootable cd of the software mentioned here (via a friend's PC ?) then you may be able to restore the MBR, or sort out the re sizing of the Windows partition... good luck..

---

### Post by MWAAAHAAA on 2006-10-21
Why don't you use fdisk and manually recreate your partition table. You had one big 100GB partition right? So that shouldn't be too much of a problem...

---

### Post by podunk on 2006-10-22
While searching for something else i found this:
[http://www.pcinspector.de/file_recovery/UK/welcome.htm](http://www.pcinspector.de/file_recovery/UK/welcome.htm)

which is free ware

You'll need to have a **working*** windows pc to slave your hard drive to.

also - on the page that led me to the above - they were talking about putting a flaky hard drive in the freezer for a few hours then putting it back in your machine. folks were swearing on it, be darned if i know!

---

### Post by emersony on 2006-10-23
thanks podunk that looks really interesting. I'm even hoping to have some time to decomile it and get under the hood. I've used the gnu part ed before and it just isn't as good as the commercial stuff for recovery. Hopefully this one will do the trick. (German engineering, heh.) 

Emerson

---

