---
title: "I'm trying to uninstall Ubuntu"
date: 2007-09-30
forum: General Help
---

### Post by JakeShoes on 2007-09-30
It's just not working for me. I'm not interested in dual booting (which is what all of the related threads talk about); I want to completely wipe the hard drive and install XP.

I have an XP disk, but whenever I'm trying to boot from it, it will begin to load and then say it's not safe to continue. 

I'm insanely unfamiliar with this OS or anything it has to do with, so a step-by-step guide on how to get XP back would be helpful. 

Cheers.

Edit: [http://dban.sourceforge.net/](http://dban.sourceforge.net/)

This is the program I want to use to wipe my hard drive, but I can't figure out which aspect of it to download or how to burn it to a CD. Not being able to run .exe's is something I'm not used to. It says in the readme:

"# cdrecord dban-1.0.7_i386.iso

Ensure that the /etc/defaults/cdrecord file is properly configured for your
computer."

But I don't know how to do that. Again, a step-by-step would be hugely helpful.

---

### Post by leonidas666 on 2007-09-30
> **JakeShoes said:**
> I have an XP disk, but whenever I'm trying to boot from it, it will begin to load and then say it's not safe to continue. 
In theory, it should work like this:
You boot with your windows XP cd, after accepting the EULA etc. you should come into some menu where you can setup the partitions of your hard disk. There you can simply choose to delete all the ubuntu partitions (which windows probably will describe "non-system" or "other" or something like that) and create new ntfs partitions for your windows installation. 
So i don't quite understand what you mean with "it's not safe to continue.". Is this the verbatim error message from the windows installer? In any case, since you plan to delete anything, i think you can safely proceed, but just to be sure post again exactly the message the installer gives you.

You only need special software for wiping the hard disk if you want to be very sure that no data can be recovered, e.g. when you plan to sell the hard disk. Just for installing windows it is not required.

P.S.: i don't think you'll get a step-by-step guide on installing windows in this forum :)

---

### Post by kellemes on 2007-09-30
You can also boot the Ubuntu-livecd or another GNU/Linux-livecd and use GParted to delete all the partitions of the drive you want to wipe. Windows-install should have no trouble creating the partition for itself.

---

### Post by Ub1476 on 2007-09-30
The XP cd says it's no safe to continue because it didn't spot your HD. You need to patch the newest drivers for your HD to make it work. Look at windowsreinstall.com forum, there should be a thread about how you can fix it there. I had the same problem so it should work for you:)

---

