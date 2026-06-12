---
title: "Partition problem"
date: 2007-01-20
forum: General Help
---

### Post by cjoey19 on 2007-01-20
Hi guys, i have a problem, i was reinstalling windows xp and like a fool i messed up the partitions..

Ubuntu edgy was on my second harddrive on the forth partition (sdb4?) and now its on the 3rd partition... so grub wont boot ubuntu, i got myself a live cd and editted menu.lst and now it boots but reaches some error... so what should i do now? reinstall ubuntu?


(btw, i have a separate /home partition, so if i reinstall ubuntu and mounts that as my home partition will all my settings and apps remain?)

---

### Post by Wofl on 2007-01-20
what exactly does the error tell you?



PS: yes you can reinstall and remound the /home partion. just make sure you mount it, but dont make it format it

---

### Post by floke on 2007-01-20
If you haven't spent loads of time configuring ubuntu then a reinstall might be a good option, sinec it only takes around 20 mins. I would delete the partition where your ubuntu is along with the swap file (i.e turn them into free spaces) and then reinstall onto that. You can then remount your home partition (though its always good to back up important docs before partition hard drives etc.).

BTW: Am far from an expert on reinstalling or anything so don't know if this is the 'proper' way to do it, but I've installed/reinstalled a number of times with this method and have had no problems.

Good luck.

---

### Post by cjoey19 on 2007-01-21
the only reason i'm reluctant to reinstall ubuntu is the fact that i spent a few weeks configuring everything, (i'm a noob) from my 5 intellimouse buttons, wine, beryl, other eye candies... is there any way for me to backup all that and restore them without the painstaking process of doing it all again?

btw, the error message says mount /dev/sdb6 on / failed, and similar mount failures... so any  ideas to solve this problem without reinstalling and configuring ubuntu? (or maybe a way to backup all the apps, settings and stuff and restore them after the reinstall?)

---

### Post by Wofl on 2007-01-21
hmmmm

maybe it would help if you edit your fstab file

boot up the live cd and open a terminal

try to somehow find out what is moved to where. maybe you remember some files

then edit your /etc/fstab to reflect these changes.

BUT BE VERY CAREFULL

messing this up could mean that you cant boot backup no mater how...

mach it up beforehand by issuing
```
cp /etc/fstab /etc/ftab.backup
```

then use gedit to edit the file. 
```
gedit /etc/fstab
```

if this messes it up bigtime, then restore the backup with
```
cp /etc/fstab.backup /etc/fstab
```

and then try again

---

