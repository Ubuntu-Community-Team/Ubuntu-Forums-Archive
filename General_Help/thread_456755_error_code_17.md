---
title: "error code 17"
date: 2007-05-28
forum: General Help
---

### Post by zzfive on 2007-05-28
ok.. heres an interesting problem i am booting both xp and ubuntu when grub loads it spits out error 17 but funny part is ive had it working for months and turned it off one day and the next morning it started giving me the error. i know the error is dealing with grub being unable to mount but what could cause this? could it be a bad hdd

---

### Post by louieb on 2007-05-28
Latest round of Feisty Updates broke GRUB on more that 1 computer. 
So 1st question is did you install the last set of updates? It included a kernel update. 
You'll need a live CD to diagnose and fix.  
Rather that reinvent the wheel look at this thread 
[http://ubuntuforums.org/showthread.php?t=456742&highlight=grub+error+17](http://ubuntuforums.org/showthread.php?t=456742&highlight=grub+error+17)
it should help **confused57** is pretty good at fixing stuff.
If that doesn't help use the live CD to post you fdisk -l output.
and a listing of your /boot/grub/menu.lst here. and i'll try and help.

---

### Post by der_joachim on 2007-05-29
Hmmm... The last time I saw an error 17, it was because Partition Magic hosed the MBR. Fortunatelyw an error 17 is easy to fix. [This wiki page]("https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows") will show you how.

---

