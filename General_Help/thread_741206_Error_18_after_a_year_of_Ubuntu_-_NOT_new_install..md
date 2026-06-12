---
title: "Error 18 after a year of Ubuntu - NOT new install. HELP!!"
date: 2008-03-31
forum: General Help
---

### Post by MindFork on 2008-03-31
I started with 6.04, upgraded to 7.10 when it was available and have been doing well with Ubuntu for over a year...until today.

I was in Thunderbird doing email and it started telling me it couldn't delete an email because it couldn't write to the trash folder...free up some disk space, etc.  I emptied the trash, but kept getting the message.  I closed t-bird, but it wouldn't reopen.  The desktop and various applications started getting frozen, so I closed them one by one (and saved an open document just fine).  I also removed a bunch of old podcasts just to be safe.  

Then I rebooted and get GRUB loading, please wait...
Error 18

GAAAHHH...

I checked in BIOS and things look fine.  Two 80 gig SATA hard drives, one with ubuntu, one as a back up drive (sadly, my back-ups are WAY out of date, so I can't just reformat the main HD).  NOTHING changed in the BIOS.  Nothing changed on the OS.  It just took a dump on me.

I loaded the live CD and booted from it.  24 gigs free on the hard drive.  I started an install process to see what my partitions looked like, and there isn't a dedicated boot partition.  (I let the installer do the partitioning on the entire HD when installing).  

I can't just reformat, because I don't have my data fully backed up.  I also can't copy it from one HD to the other in the CD boot mode because I don't have permissions to access the drives while in the CD mode.  That's a real pisser, right there.

Please help!  

Thanks,
MF

---

### Post by disturbedite on 2008-03-31
prolly a kernel upgrade "issue"...
when you get to the grub menu, press "e" to go into edit mode.
make sure the kernel is pointing to the correct partition.  (i.e. for me its (0,0)),

---

### Post by MindFork on 2008-03-31
Hmm... I can't even get into the grub menu by pressing e.  I tried several times, with rapid pressing of e and holding it down throughout the boot process.  On the grub screen it shows:

GRUP Loading stage1.5.

Then loading, wait, error...  Is GRUB broken?

---

### Post by forrestcupp on 2008-03-31
You could try [restoring grub](http://ubuntuforums.org/showthread.php?t=224351) with the LiveCD.

---

### Post by MindFork on 2008-03-31
Forrestcupp, I followed those instructions and it seemed to work fine, but when I rebooted I still get the same error. :(

---

### Post by MindFork on 2008-03-31
Desperation is setting in... Is there a way to install ubuntu again without formatting/repartitioning the hard drive?  Of course, fixing grub would be preferable, but I've gotta do something.

---

### Post by crazyone on 2008-03-31
you should be able to run in the live cd chmod 777 it may make it so the system might not work even after you are able to fix it but if u are jsut wanting the files right now u can sjut do that and back them up to you backup drive.

---

### Post by MindFork on 2008-03-31
> **crazyone said:**
> you should be able to run in the live cd chmod 777 it may make it so the system might not work even after you are able to fix it but if u are jsut wanting the files right now u can sjut do that and back them up to you backup drive. I couldn't find a way to chmod the directory from the live cd.  

Still, even more important than the data is getting GRUB to work again.  Anybody else have suggestions?  I'm willing to reinstall as long as my /home directory is preserved.

---

### Post by forrestcupp on 2008-04-01
When you boot to the Live CD, it should automatically mount the drive that has your /home.  You just need to find it and back up all of that data and reinstall Ubuntu.

Edit:
It's also possible that your Ubuntu drive is toast.  If that is the case, it doesn't matter how many times you restore grub, it ain't gonna work.

---

### Post by MindFork on 2008-04-01
> **forrestcupp said:**
> Edit:
It's also possible that your Ubuntu drive is toast.  If that is the case, it doesn't matter how many times you restore grub, it ain't gonna work.

You sir, are exactly correct.  The drive died.  Time to rebuild.

Thanks everyone for your advice.

---

