---
title: "Portable Multi OS"
date: 2008-01-18
forum: General Help
---

### Post by kingvandal on 2008-01-18
I have a portable 160gb hard drive and am looking to run Ubuntu and Windows XP side by side on the portable hard drive.  By this I mean I want to be able to take the harddrive to any system and plug it in a choose booting between windows or ubuntu.  I am a tech and we are in a primary microsoft env.  But I can see so many uses for Ubuntu.  So here is my question.  Is it possible?  If so, how?  I have seen many posts dual booting win and linux but none of them on a portable drive together without a primary computer.  Like I said above my goal is to be able to walk up to any computer plug in the the USB Portable drive runing windows and ubuntu and choose one and boot the ystem to the OS.

---

### Post by Mechanical on 2008-01-18
I could be very wrong on this and if I am I will be happy and set something up like this myself.  I don't think it is possible at all.  There are linux live cds and I have seen windows xp live cds that boot on just about any computer but its not a full blown installation of linux or windows.  The problem is with hardware changes from one computer to another.

---

### Post by narehart on 2008-01-18
This is completely possible as long as your motherboards BIOS allows you to boot from USB.  Of course I'm assuming your portable hard drive connects via USB.

---

### Post by kingvandal on 2008-01-18
Yes it is a botable USB.  Now you have serioulsy sparked my intrested.  Please illaberate..

---

### Post by xyphur on 2008-01-18
Although technically possible, you wouldn't want to do it. Windows would reboot about 15 or 20 times reconfiguring itself for each subsequent machine you plug it into, all while wiping the last machine's hardware config completely out. You'd spend more time booting into your 'portable windows' install than you would installing a fresh copy of windows on the machine's local hard drive and then finding and installing drivers for all of it's hardware. Believe me, it's not worth it.

If you want a useful bootable CD, grab Hiren's Boot CD. I believe the latest version is 9.3, but don't quote me on that though, it changes often.

---

### Post by kingvandal on 2008-01-18
I see.  Bah windows.  Gets my blood boiling daily!  Anyway I could really care less about running Windows on there I would prefere just Ubuntu but does it have the ability to access registery for resetting passwords etc?  I would love to have it be my "fix all" disc.  I guess all Ubuntu would really need to do would be reset windows passwords and be able to backup data from a windows partition to the portable drive.  Can Ubuntu do that?

---

### Post by Golden Phoenix on 2008-01-18
I think xyphur is right on this that Windows REALLY hates when you move it around.  If you did it, you may expect to have to verify it all the time if you place it between drastically different systems.

I have a idea, though:  Why not partition the drive so that you have it divided between ext3 and NTFS?  That way, you could place Ubuntu on the ext3 part, and you still have space on the drive (the NTFS part) that you could put stuff on that you use in Windows often.

Just a thought, since I've done such myself with a drive just that size down to a flash drive (DSL and PCLOS on the same stick with some space left for NTFS that has a program script that I can boot up to either in Windows).

---

### Post by xyphur on 2008-01-18
Yes, Ubuntu can access NTFS partitions. You'd be better served booting from the LiveCD and then using a USB drive to store backed up data.

For registry stuff, of course being that Ubuntu can access the partition the registry is located on, you'll have direct access to it, but because you won't have a registry editor, you'll be unable to edit keys/data in any given hive. If you're interested in windows password retrieval functionality, try ophCrack (a bootable CD that does to Windows passwords what the name implies).

---

### Post by xyphur on 2008-01-18
Golden Phoenix: you could also just install the ext2fs IFS driver in windows and then you'd have access to ext2/ext3 filesystems natively. Give the drive/partition a drive letter using the control panel applet, and instantly have read/write access to it like any other drive in Windows. No need to use an NTFS partition as temp file storage. Although that works, it's not the most elegant of solutions. ;)

[http://www.fs-driver.org/](http://www.fs-driver.org/)

---

### Post by kingvandal on 2008-01-18
OK I decided to use [UBCD]("www.ultimatebootcd.com").  Ran across this [Integrating any bootable Linux CD into Ultimate Boot CD]("http://web.archive.org/web/20041009201116/www.sadyc.net/anyCDintoUBCD.html").  Seems pretty straight forward.  Gets away from running Windows Directly and providing Ubuntu supports ISOLinux I will be able to run Ubuntu too.  Sound right guys/gals?

---

### Post by Golden Phoenix on 2008-01-18
Yup, the Live CD's for Ubuntu (and most other distributions) all use ISOLinux.

xyphur:  You're right on that, too.  There's lots of ways to adress this situation, which is part of why I've liked Linux for so long!

---

