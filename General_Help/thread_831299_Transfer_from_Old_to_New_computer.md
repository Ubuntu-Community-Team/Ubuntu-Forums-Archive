---
title: "Transfer from Old to New computer"
date: 2008-06-16
forum: General Help
---

### Post by Phototrek1 on 2008-06-16
Hi,  
   I just ordered a new laptop. My current laptop is a duel boot system win Xp and Ubuntu 7.10. I use Ubuntu a lot. I don't have  time too fuss. I have my Ubuntu partition/image tweaked perfectly and I don't want to spend hours and hours tweaking it again. I'm looking if there is a transfer app in Linux that i can use or if it is possible to convert my Linux partition into a VM image to use it later while I'm tweaking a new install.  I need this transfer method to be proven and trusted. I even thought about transferring the partition from the old hard drive to the new one. I'm just unsure if Ubuntu can handle the hardware change. Let alone going from 32bit to 64bit. Or should i just start from scratch.

Both are Dell
Old laptop Latitude Pentium M 1.2ghz 512mb HD 60gig wifi

New laptop Win XP Vostro Intel core 2 duo 1.8ghz 2gig HD 250gig wifi

---

### Post by dmizer on 2008-06-16
your ubuntu should be able to handle the new hardware without much problem.  for the most part, you'll probably only have to reconfigure your network and video.  it will be running in 32 bit instead of 64 bit, but for most practical purposes, this will be fine.  if you really feel the need to, you can upgrade to the 64 bit kernel later.

here is a good howto on backing up and restoring your ubuntu: [http://ubuntuforums.org/showthread.php?t=35087](http://ubuntuforums.org/showthread.php?t=35087)

i have used this method on several occasions.  however, if you want to keep your xp installation on your new laptop, that will significantly complicate things.

---

### Post by Phototrek1 on 2008-06-17
Thanks for the info, I'm still kind of new to the Linux world of doing things.  But The guide is very help full. 

Thanks,
Phototrek1

---

### Post by danerben on 2010-02-20
For anyone trying to transfer your Linux to a new hardware (no better howto found elsewhere so far):

It is actually quite unwise and unnecessary to transfer all the partition. All you have to do is transfer the linux filesystem except:

/dev (hardware settings) - so that there is no problem with different hw
/sys (will not go into details, just exclude it)
/proc (currently running processes)
/media (mount points for removable media)

You just make an archive of the rest using tar (as root) and then just unpack it on the new disk. All should be fine then.

---

### Post by The Real Dave on 2010-02-20
You could try using Clonezilla to copy one harddrive to the other. I understand about you not wanting to reconfigure everything again, but 7.10 is quite old. Chances are using a newer release your hardware will be better supported.

Seeing as your laptop can support it, I'd advise using the 64bit flavour. AFAIK there isn't much difference on the software end between x86_64 and x86, the reason why they closed the x86_64 forum. The speed difference between x86 and x86_64 for me was massive.

---

