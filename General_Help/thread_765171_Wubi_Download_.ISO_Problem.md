---
title: "Wubi Download .ISO Problem"
date: 2008-04-24
forum: General Help
---

### Post by puner on 2008-04-24
I downloaded 8.04 today using torrent since it was the faster way.

But when using wubi, it wants to download 8.04 by itself. Is there anyway it can use the one that I downloaded?

Also, which is Wubi still installing the beta 8.04 when today was the official release?

---

### Post by Fraghdad on 2008-04-24
I got the same problem. I tried to install Kubuntu-KDE4 with wubi rev.501. I put the iso and wubi in one folder, but it started downloading anyway.

I'm running Xp and the filename of the iso is:
kubuntu-kde4-8.04-desktop-i386.iso

---

### Post by puner on 2008-04-24
^ Thank you.

All you need to do is put the wubi installer and the downloaded ISO in the same folder.

Wubi will see the ISO, and use it.

---

### Post by timekills on 2008-04-24
I have found this incorrect.  There must be a hash check it does, because I have downloaded the CD ISO and the DVD ISO, from a number of sites, all with confirmed hash checks, and it chooses not to use the ISO.

I have tried with the downloaded ISO name (i.e. ubuntu-8.04-desktop-i386.iso) and by changing the name to hardy-desktop-i386 and using the --32bit force, and all of them proceed to download the iso again.  

Not only have I wasted the download in advance, but wubi - although it is supposed to be using a metalink to speed up the download process - is maddeningly slow in downloading the iso.

So, is there a way to force it to use the iso, or confirm you have the RIGHT iso?

Thanks!

---

### Post by FrostiEE on 2008-04-24
Try running Wubi with --skipmd5check

---

### Post by puner on 2008-04-24
> 
Can I use an existing ISO/CD instead of letting Wubi download a new one?

Yes, physical CDs will be detected automatically, pre-downloaded ISOs should be placed in the same folder as wubi.exe. You can find the latest ISOs here


[Source]("http://wubi-installer.org/faq.php")

---

### Post by ago on 2008-04-24
please post the wubi log in your user temp folder (%temp%) as well as c:\ubuntu\metadl_log.txt

---

### Post by screwballl on 2008-04-25
holy slow download batman.... through Wubi, it gets to 80% at a decent pace, typically 200kbps (I have a 10Mbps connection)... then after that it slowed to 30-34kbps and took an hour to get 2% downloaded... trying to download the iso from the official link and it is going about 100kbps... my downloads are normally 1000-1200kbps.... trying to get the offical version from the ubuntu front page, says "too many connections, try again later".... I would have figured that the bandwidth would have been increased to handle this for a week or so...

edit ah yes much better... just kept clicking the link until it finally connected (after about 20 tries)... and here it comes at 600-650kbps... sped up to 1100kpbs and downloaded in minutes...

---

### Post by kentigens on 2009-06-25
Hey guys, i know why its not doing the right thing. You have to put both the wubi.exe and .iso under DESKTOP. not just  a random folder. It actually worked for me,  ...sweeet

---

