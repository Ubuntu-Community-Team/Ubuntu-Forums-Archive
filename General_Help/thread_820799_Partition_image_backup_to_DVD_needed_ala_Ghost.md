---
title: "Partition image backup to DVD needed ala Ghost"
date: 2008-06-06
forum: General Help
---

### Post by errolgreer on 2008-06-06
****I use Ghost 2003 to backup individual partitions as images in Windows. I need to create an image on DVDs of my Ubuntu 8.04 partition in order to restore it to a new hard drive, with all settings as they now work. My machine is trible booted with XP, Vista and Ubuntu, the latter on a different physical drive. Ghost 2003 seems to back up this drive, but I'm told that it won't work as Ext3 gets screwed up by Ghost 2003. (It worked with the older Ext2, I believe.) Something easy to use which can restore later from the DVDs to a new (bigger and faster) hard drive, but also to have a backup for security. Any suggestions ? Some apps can only image the entire computer which doesn't help as I have 250 Gigs of stuff in total.

Many thanks

Errl

---

### Post by briandu on 2008-06-06
You can use PartImage and create files of your linux to DVD and it will spool the files off to DVD as long as you are prepared to feed them.

---

### Post by errolgreer on 2008-06-16
Can I download the Partimage file from XP (I presume it is an ISO file?) and create a bootable CD using Nero from XP. Then boot from it to create the image of my Ubuntu harddrive onto DVD's, from which I could then restore 8.04 ? Would the Image DVD be bootable ? I really need help here as I am new to Ubuntu. I have 2 DVD drives available on my system.

---

### Post by errolgreer on 2008-09-04
An update to this post

I have found a program called Image for Windows which is much cheaper than Ghost. I have Windows and Ubuntu in a multiboot setup. It backs up the Ubuntu 8.04 partition and restores it very well. The backup image gets created on one or more bootable DVDs and by booting from these, it brings back the Ubuntu partition perfectly.

---

### Post by Wolfhere on 2008-09-06
Yes, there is a problem with Ghost and backing up linux partitions. I have Ghost 12 and cannot restore. I am glad to hear about Image for Windows (includes Image for Dos and image for Linux. If it works in Ubuntu, that is all I need. Thanks again:guitar:

---

