---
title: "My Computer is broked"
date: 2008-06-08
forum: General Help
---

### Post by Wasistlos on 2008-06-08
I've been using Windows XP along with Ubuntu on a single computer on a single hard drive dual booting for a few weeks now.  Unfortunately I couldn't get Ubuntu to work with my wireless network card so I decided to uninstall it.

I booted up Ubuntu using a live CD then I repartitioned my computer to add the Ubuntu and Swap space partitions to my Windows XP partitions.  Thinking everything was all fine and dandy afterwards, I turned off the PC took out the live CD and restarted my computer.    My computer then booted to Grub but gave me an "Error 22".  I suppose some important files for Grub to work were probably on the Ubuntu partition.  Anyways, Grub did not display my Windows XP partition, nor any partition for that matter, so I decided to grab live CD and my Windows XP cd.

After toying around with things for awhile and looking for advice on various forums I ended up screwing it up worse.  Here is what I have ended up doing.

1.  Deleted my Windows boot.ini file (rebuilt this though)
2.  Ran Fixboot under the Windows XP recovery console multiple times (probably screwed something up)
3.  Ran Fixmbr under the Windows XP recovery console multiple times (again probably screwed something up)

Anyways, after all this I rebooted my computer and Grub doesn't even load to give me an error, probably because I reinstalled the master boot record with the Windows XP recovery console.  When I turn my computer on all that happens is that it hangs.  It has a blinking - sign and then after a few seconds the - sign moves down a couple inches on the sceen and keeps blinking.  Nothing happens.

I can still boot to Ubuntu using the live CD and I can see that all my documents, files, and windows settings and files are installed and fine.  Any help please and thank you!

---

### Post by housam on 2008-06-08
If you can get the [[COLOR="Red"]_super grub disk _[/COLOR]]("http://www.supergrubdisk.org/index.php?pid=12"), you can fix your boot loader and boot windows.

You can read this valuable [[COLOR="Red"]_document_[/COLOR]]("http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html") by Herman, it will help you.

---

