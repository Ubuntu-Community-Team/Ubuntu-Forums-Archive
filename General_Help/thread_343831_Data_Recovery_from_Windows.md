---
title: "Data Recovery from Windows"
date: 2007-01-22
forum: General Help
---

### Post by rabidrabbit on 2007-01-22
I switched to Kubuntu 6.10 i386 after some time trying different distros. I wrote over my windows c drive after thinking i had moved all my needed data off. I completely forgot to get my sister's documents and music off (i recently switched her old ibm thinkpad t21 to ubuntu and have yet to transfer the files back). I need some way to get these files back, they were only about 800meg but I am dead otherwise.

Since you are here, this is another problem..

Cannot use the touch button thing (i don't know what to call it), volume controls work fine though.


thanks in advance.

---

### Post by crispy_420 on 2007-01-22
File recovery may be next to impossible. On install you basically wiped the drive. That comes with changing file systems. You went from fat32/ntfs to ext3. I'm sure there are tools to get that data back, maybe, but they won't be easy or cheap.

As far as "touchpad" thing, can't help you there. But my first guess is you may need to add something to xorg, like a driver. But that is just a guess.

---

### Post by Sef on 2007-01-22
Check out [TestDisk]("http://www.cgsecurity.org/wiki/TestDisk").

Check out [Trinity Rescue Kit]("http://trinityhome.org/Home/index.php?wpid=1&front_id=12").

Both are no cost.

---

### Post by crispy_420 on 2007-01-22
But keep in mind trinity has no gui.

TestDisk now that looks good and promising. And they mention you can get it on many different livecd's. To that I say it is worth a try as a livecd. No install, just a livecd and an external hard drive or other device. I wish BerryLinux used it. Just used that to recover a friends files from a screwed up WinXP laptop.

---

### Post by UniRecovery on 2007-02-12
Whatever you wish to do, make sure you DONT do the work on the original media, instead you should create a cloned image of the wiped drive then use any data recovery tools on the cloned drive and not on the original one.

---

