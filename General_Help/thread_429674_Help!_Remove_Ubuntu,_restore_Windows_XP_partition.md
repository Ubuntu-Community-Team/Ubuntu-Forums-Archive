---
title: "Help! Remove Ubuntu, restore Windows XP partition"
date: 2007-05-01
forum: General Help
---

### Post by songamericadj on 2007-05-01
Ok, here's the deal. I have nothing against Ubuntu, but in the interests of my computer acting funky, I would like to remove Ubuntu, remove the GRUB loader, and re-integrate the partition back to the same partition that I have Windows XP on, without losing Windows XP. If someone could help me with this, I would greatly appreciate it. Thanks in advance!

---

### Post by Herman on 2007-05-02
Hello songamericadj,
You probably did what most people do when they install Ubuntu and installed the IPL for the Grub bootloader in the bootloader part of your hard disk's  Master Boot Record, (which is good).
Only a small part of Grub actually gets installed in the MBR though. The most important and larger part of Grub lives in the Ubuntu partition. If you delete Ubuntu now (with a hard disk partitioning software such as [GParted -- LiveCD]("http://gparted.sourceforge.net/") or the like, you will be deleting the main part of the Grub bootloader too. When you do that you will find that you won't be able to boot any operating system. 
All you need to do is re-write the IPL for the bootloader for whatever other operating system you have -Windows XP in your case, to MBR, overwriting the now useless IPL for Grub.  There are lots of ways to do that, you can decide which is the easiest for you. Here's a link to a web page that will walk you through six different ways to do that. Just choose whichever suits your circumstances. [Un-install Page]("http://www.users.bigpond.net.au/hermanzone/p18.htm")
After you delete the Ubuntu partition with any partition editing software, you will have free space in your hard disk where Ubuntu was. Just use your partitioning software to resize Windows larger so it will take up the entire disk again if that's what you want.

Thanks for trying Ubuntu, sorry to read it didn't work well for you. Maybe try again with different hardware or when your circumstances change.

Regards, Herman :)

---

