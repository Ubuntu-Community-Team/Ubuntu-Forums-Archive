---
title: "error 22: no such partition grub problem."
date: 2008-04-28
forum: General Help
---

### Post by onesojourner on 2008-04-28
I am dual booting xp and ubuntu. I have tried every thing short of wiping my hdd and all the partitions and starting fresh. I have tried to [reinstall grub from a live cd]("http://ubuntuforums.org/showthread.php?t=224351")two times and I have tried to fix my problems with super grub disk. I am totally unable to boot into ubuntu and I can only boot windows through super grub disk. Could some one tell me where I could find grub and just delete it. I just tried a fresh ubuntu install and it says it failed to install grub so I am assuming the grub install on here is full of errors. How can I find it to delete it/correct the problem. I need to be able to either do this from windows or a live cd.

---

### Post by adrian15 on 2008-04-29
> **onesojourner said:**
> I am dual booting xp and ubuntu. I have tried every thing short of wiping my hdd and all the partitions and starting fresh. I have tried to [reinstall grub from a live cd]("http://ubuntuforums.org/showthread.php?t=224351")two times and I have tried to fix my problems with super grub disk. I am totally unable to boot into ubuntu and I can only boot windows through super grub disk. Could some one tell me where I could find grub and just delete it. I just tried a fresh ubuntu install and it says it failed to install grub so I am assuming the grub install on here is full of errors. How can I find it to delete it/correct the problem. I need to be able to either do this from windows or a live cd.

Please check: [Linux Installation does not boot - Solution](http://www.supergrubdisk.org/wiki/Linux_Installation_Do_Not_Boot) and tell us if the solution for you was to use the apt-get not-internet connected solution or the repartitioning.

Thank you very much.

adrian15

---

### Post by Arwen on 2008-04-29
You could try to boot in ubuntu with [GAG]("http://gag.sourceforge.net/").
It's supposed to let you log in there..
Check [this]("https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows")
out if you haven't done it yet.
Grub files are in /boot/grub and menu.lst has the partitions that are mounted,maybe you should take a look at it.

---

### Post by adrian15 on 2008-04-29
> **Arwen said:**
> You could try to boot in ubuntu with [GAG]("http://gag.sourceforge.net/").
It's supposed to let you log in there..


**No it is not. GAG only boots Linux partitions is a boot loader has previously installed into the Linux partition boot sector which it is not the case in a default installation as far as I know.**

adrian15

---

### Post by Arwen on 2008-04-29
I don't know details about it but it always helps me out of grub mess and errors so I thought it's worth trying.

---

### Post by adrian15 on 2008-04-29
> **Arwen said:**
> I don't know details about it but it always helps me out of grub mess and errors so I thought it's worth trying.

And what GAG options do you use? What was your problem... and what these GAG steps fix?

Did you ever had to install Grub or Lilo into your partition boot record or not?

Thank you very much.

adrian15

---

### Post by Arwen on 2008-04-29
I had BSD,ubuntu and XP in my hd and XP was the last to install so it erased the previous bootmanager.I simply installed GAG with CD and added the OSs I wanted to boot as in the [screenshot]("http://gag.sourceforge.net/pics.html").
Since then I haven't reinstalled grub as I booted from GAG.
Not to mention,it was my case and I may just have been lucky.That is to say it's just a suggestion and I hope someone has a better solution.

---

### Post by onesojourner on 2008-04-29
thanks for the replies. I gave up and wiped everything. I had a storage partition that was currupted (ext3) I tried to reformat that but it kept failing so I am farmatingit to ntfs and then I will try to go back to ext3.

---

### Post by adrian15 on 2008-04-30
> **Arwen said:**
> I had BSD,ubuntu and XP in my hd and XP was the last to install so it erased the previous bootmanager.I simply installed GAG with CD and added the OSs I wanted to boot as in the [screenshot]("http://gag.sourceforge.net/pics.html").
Since then I haven't reinstalled grub as I booted from GAG.
Not to mention,it was my case and I may just have been lucky.That is to say it's just a suggestion and I hope someone has a better solution.

I've talked to the GAG developer and it seems that it needs a boot loader in the partitions' boot sector so... 

Might I suppose that ubuntu installation both installes grub to the mbr and to the partitions's boot sector?

Can anyone confirm this?

adrian15

---

