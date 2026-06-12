---
title: "Help Ubuntu wont boot - ERROR"
date: 2007-05-19
forum: General Help
---

### Post by Cloudedbrains on 2007-05-19
**GREAT ANOTHER PROBLEM !!!!!!!!!**

I keep getting the following when trying to boot to Ubuntu so am on XP right now !!!!

> Your session only lasted 10 seconds. If you have not logged 
out yourself, this could mean that there is some installation problem 
or that you may be out of disk space. Try logging in with one it the 
failsafe sessions to see if you can fix the problem.

I have the suspicion its disk space but got no clue how to sort it !!!!

---

### Post by taurus on 2007-05-19
Boot into recovery mode from GRUB menu and at the prompt, check your disk space with

```
df -h
```
And if / is full, 100%, then you need to free up some space before you can log in with

```
aptitude clean
df -h
```

---

### Post by Cloudedbrains on 2007-05-19
Its full :(

So how do I sort it out ???

---

### Post by taurus on 2007-05-19
```
aptitude clean
df -h
```

---

### Post by Cloudedbrains on 2007-05-19
Did that and still getting same error - is there away to allocate more space to it as it just seems to have filled the space I allocated at install ???

---

### Post by taurus on 2007-05-19
Can you post the output of this command after you run "aptitude clean"?

```
df -h
```

---

### Post by Cloudedbrains on 2007-05-19
Ok tried it again and am back under Ubuntu but is there a way to stop it happening again by enlarging the disk space ???

Forgive me for being dumb but I am new to this !!!

---

### Post by taurus on 2007-05-19
It depends on how your partitions set up.  How much space did you allocate for / anyway?  Also, when you delete something with nautilus, you are not actually removing it.  There is still a copy in the trash bin so you need to empty your trash to recovery that space.

---

### Post by Cloudedbrains on 2007-05-19
Had to lower the disk space on install to get it to go past 33% install !!

I think it was 4gig and 4 gig I allocated under the advanced options (installed using Wubi) !!

But its sitting on a partition of over 48gig all to itself if I can get it too use it !!

---

### Post by Cloudedbrains on 2007-05-19
This is what partition manager shows me :(

[IMG]http://i112.photobucket.com/albums/n200/Cloudedbrains/Screenshot-2.png[/IMG]

---

### Post by strabes on 2007-05-19
Use the [gparted live CD](http://gparted.sourceforge.net/livecd.php) to grow your / partition

---

### Post by Cloudedbrains on 2007-05-19
According to Gpart thought the partitions are fine but it still spat the dummy over the "Disk Space" :o

---

