---
title: "Before I seal the deal...what about virtualization?"
date: 2007-07-09
forum: General Help
---

### Post by joelkm on 2007-07-09
Hey guys, been using Ubuntu for a couple days...love it!  Right now I am dual booting with Vista but I am contemplating going 100% Ubuntu.  I just have one questions, I need to be able to run Solidworks, Photoshop, Quickbooks for work.  Should this all work properly under Virtual Box etc?  I have a pretty powerful machine and I am willing to run XP virtualized.

Thanks a mill!

---

### Post by vayde on 2007-07-09
I have not found any problems running programs out of VirtualBox.  Even my company's idiotic vpn policies work great through VirtualBox.  
Look here for more info.
[http://doc.gwos.org/index.php/VirtualBox](http://doc.gwos.org/index.php/VirtualBox)

Good luck, and you can always catch us on Freenode irc in #ubuntuforums-beginners if you need help walking through a VB installation.

Cheers.

---

### Post by joelkm on 2007-07-09
Great, now I'm not sure how this technology works.  But as you know Photoshop and Solidworks are quite resource intensive.  I have a 512MB Quadro 2500M graphics card, once my Xp drivers are installed for this under VM should  it run close to native speed?

---

### Post by vayde on 2007-07-09
I have not personally tried either program, so I can't say for sure.

My best advice is to install the VirtualBox into your Ubuntu installation, and see for yourself.  Don't nuke the Windows partition until you're sure all works as you need it to.

Make sure you install the 'guest additions' into the virtual machine when you set it up.  VirtualBox is a great product, but without the guest additions it's a little clunky.

Make sure you install the additions into the GUEST OS, that is the virtualized OS, Win XP in this case, not the host, Ubuntu.  Someone did that recently, it was... memorable.

Hop onto irc, assuming you're familiar with that (I wasn't at first), and we can talk you through it if necessary.

---

### Post by srunni on 2007-07-09
I don't think you can install graphics drivers under a VM (other than for Parallels, on Mac, that is), but you don't need that. I have used XP under VMware Server and run both Solidworks 2007 and Photoshop CS2 and CS3, with the virtual machine having 256 MB ram (I think). I have a 3.0 GHz Pentium D processor.

---

