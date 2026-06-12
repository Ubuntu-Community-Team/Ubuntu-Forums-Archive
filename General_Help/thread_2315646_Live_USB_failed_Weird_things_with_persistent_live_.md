---
title: "Live USB failed? Weird things with persistent live USB..."
date: 2016-03-01
forum: General Help
---

### Post by gordan-vrbanec-vepar on 2016-03-01
So i made a live USB for a friend with Ubuntu on it because he deosn't have his own computer but uses a company computer where he can't install or use anything except the programs they installed before he got it. It's Windows 7 with admin password required for almost everything.

Long story short, i made it persistent, and i used "mkusb" to create it. Great, now he has a system he can use to do whatever (he needed it mostly for Blender)...

Weird thing... Yesterday he came to me saying it's not working, it's not booting up. So i take the USB to have a look at it, and well, it's not booting up. Windows says the drive needs to be formatted to be used, and Ubuntu live CD that i have doesn't even recognise it. Gparted on the other hand does, and all it read was an empty raw volume with no file system or partitions (there were 3)...

So i'm scratching my head trying to figure this out and i have no idea what happened. The USB is usable after partitioning and formating, it didn't fry or die or something. The partitions and the file system were just gone. 

It's a good thing he didn't have any too important files there, so i made another live USB, and i'm now wondering. Is it better to just install Ubuntu on the USB or create another one with mkusb? I tried to make a persistent live USB manually but for some reason it never recognised the *>4GB casper partition that i made, and it just wouldn't boot up, it always went straight to initramfs... I'd be much happier if i can partition it and do it myself, but it just doesn't work so i use mkusb...

I tried actually just installing the system on the USB but this caused the system to be horribly slow and unresponsive, while the live one was just like being installed on a hard drive - well, until this happened...

So what's better? Should i just redo the live USB install with mkusb and hope this deosn't happen again, or should i try to install it directly on an USB?
Installing it would be better because live USB didn't recognise all of his laptop's hardware and i had to fix and install a lot of stuff to be usable, and even then i couldn't get the sound to work. On the other hand, installing it on an usb (from his laptop) would have the benefits of all the correctly recognised hardware (it doesn't need to be portable, it's just for 1 computer), and i'd have less issues to deal with. But it's so slow... 

Any tips on what i should do? What's better for constant use? Live USB or installed on an USB?
And what should i do to make it faster if i were to install it directly?

---

### Post by sudodus on 2016-03-01
Your friend had tough luck. There are a few issues that are worth discussing here.

A pendrive has a ***limited lifetime***, and a persistent live system is not writing as often and much as an installed system.

***File system corruption*** is a common problem with pendrives. This can happen in different scenarios, for example but not only, if you unplug the drive without unmounting it. There are often buffered data, that are not written until pushed by the unmount command. If a memory cell in an important position dies, it can also cause corruption. But the pendrive can recover, because there is a system (built into the pendrive) that can distribute wear and replace bad memory cells with good cells (extra memory cells provided for that purpose).

Sometimes it helps to repair the partition table or a file system with ***testdisk***. Even if that is not possible, you can recover important files with ***photorec***.

So it is important to take ***frequent backups*** of your personal files in the pendrive. But I have a pendrive, that has been working as a persistent live drive for a long time now, including a fair amount of writing. I use it for iso-testing the new daily iso files during the development of the next Lubuntu version, 16.04 LTS.

If you want to make a more reliable system to your friend, you can install a system into an ***SSD in an external enclosure***, a 'USB disk'. SSDs are more shock proof than hard disk drives with mechanical parts.

---

### Post by gordan-vrbanec-vepar on 2016-03-01
Thank you for your input.

I'll install a persistent live USB on it again then if it doesn't write that much. I imagine it doesn't since it's way faster than installing it directly...

Yes, i know USB's have limited lifetime, but i've never had this happen to me before, to have a corrupted file system and partitions.... I mean, it's a fairly new USB, it can't be that short lived, even with an OS there. I guess it just was tough luck. :(
Luckily he didn't have anything important there except a few browser bookmarks that i'm sure he can find again.

As for the SSD thing, i doubt he'll get the SSD just for this.

If this happens again, i'll try to use "testdisk" to recover a partition table. Maybe that could have saved the system now, i just didn't know about it. Thanks, i'll keep it in mind in the future.
And i'll remind him to save all his data to another usb, just in case this happens again.

---

