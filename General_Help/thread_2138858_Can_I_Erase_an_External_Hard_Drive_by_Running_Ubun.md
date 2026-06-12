---
title: "Can I Erase an External Hard Drive by Running Ubuntu Live from a Flash Drive?"
date: 2013-04-25
forum: General Help
---

### Post by Jdanniel on 2013-04-25
Hello, everyone.  I am currently running Windows 8 Home Premium.

I've installed a 2-port USB 3.0 PCI card on my computer, and purchased two USB 3.0 external hard drives.  

I had three [sic] external hard drives.  I really don't need them anymore, so I copied their contents to the new externals.  I then formatted them.
I'm going to give them away, but before I do, I want to wipe them clean by generating random data on them.

There is a Windows-based freeware utility called Eraser that has always worked great for me.  However, it's just not working for me on Windows 8.
I've also tried a few other drive cleaning tools, but they get frozen about 1/3 of the way into the process.

So, I had an idea.  Maybe I can run Ubuntu Live from a DVD or USB flash drive, run a Linux-based drive cleaner, and clean the hard drives that way?
(I'm not a regular Linux user, but I do know how to create a bootable copy of Ubuntu and run it Live without installing it.)

I'm wondering if doing that would affect my Windows setup, though.  I'm also wondering how I would be able to install a Linux-based drive cleaner if I'm running Ubuntu Live from a flash drive?  Does a Linux-based drive cleaner even exist?

Is it possible to do this?  Is there a Linux-based drive eraser that would work on my externals without affecting anything else?

Is it even worth trying this?

Thank you for your help!  Jack D.

---

### Post by sudodus on 2013-04-25
I think the fastest way to wipe a drive completely is with hdparm (if you rely on the proprietary software/firmware in the drive). Look at this link, where also other methods are suggested and discussed

[[COLOR="#FF0000"]http://ubuntuforums.org/showthread.php?t=2124829[/COLOR]]("http://ubuntuforums.org/showthread.php?t=2124829")

---

### Post by Jdanniel on 2013-04-25
Thank you for the response.  I think I've heard of this utility, but probably ignored it because of the command line.  I'm not afraid of the command line, though, so I might try the Windows version before dabbling with Linux.

Thanks again.  Jd

---

### Post by sudodus on 2013-04-25
> **Jdanniel said:**
> Thank you for the response.  I think I've heard of this utility, but probably ignored it because of the command line.  I'm not afraid of the command line, though, so I might try the Windows version before dabbling with Linux.

Thanks again.  Jd

The method with ***hdparm*** described in that link is running the ***command line within Ubuntu linux*** (booted from a live CD/DVD/USB drive). ***DBAN*** is an independent live system (probably linux-based), with text based menus.

---

