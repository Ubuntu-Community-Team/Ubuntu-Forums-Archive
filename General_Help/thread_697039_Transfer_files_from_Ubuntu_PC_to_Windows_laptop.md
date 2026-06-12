---
title: "Transfer files from Ubuntu PC to Windows laptop"
date: 2008-02-14
forum: General Help
---

### Post by SnappedManX6 on 2008-02-14
The title pretty much says it all.. I'm an Ubuntu newbie; just installed it and XP wouldn't boot up, so I tried to fix it but I ended up killing them both.

Though now that I think of it, it'd be cooler if someone could help me fix it instead :D

Anyway, if I don't manage to fix it, could someone tell me how I could easily, and quickly move files across these two?

---

### Post by jken146 on 2008-02-14
The easiest way is to boot into Ubuntu.  You can access your NTFS partition from there no problem.

---

### Post by eggdeng on 2008-02-14
Take a look at
[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html]("http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html")

---

### Post by SnappedManX6 on 2008-02-15
When using SGD, it gives me an error 15 when trying to boot my Linux partition.. I think that what I accidentally did was put my Linux and XP partition together.

Is this possible to fix? I mean, I still have my Ubuntu Live CD and SGD.

And by easiest way to move the files, I mean something other than taking a USB drive and send the files bit by bit.

---

### Post by strabes on 2008-02-15
Simply reinstall grub on the computer from which you're receiving that error. There's a link about grub in my signature.

---

### Post by SnappedManX6 on 2008-02-15
When doing 'find /boot/grub/stage1', it tells me: Error 15: File not found

Then I tried 'setup (hd0)'. It said: Error 17: Cannot mount selected partition

I think I'm just gonna look for some old USB flash drive and copy all my files to the laptop and reinstall everything :| . Damn people stealing my 4 GB flash drives...

---

