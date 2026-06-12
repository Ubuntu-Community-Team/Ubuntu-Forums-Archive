---
title: "[SOLVED] Backing up data from Hard Disk Whilst on Live CD"
date: 2008-01-05
forum: General Help
---

### Post by tim237 on 2008-01-05
My computer is currently only able to boot from Live CD. Whilst I'm hopeful the good the good folks at Ubuntu Forums will find some way to sort out my problem, I also want to back up the data on my hard drive, in case I need to reinstall etc. 

Problem is from the live CD I can't copy the contents of my drive which has all my ubuntu data on to my external hard drive. I basically keep getting error messages like this:

"/media/disk/etc/passwd-" cannot be copied because you do not have permissions to read it

I assume this comes about because I'm not logged in as myself. Is there anyway I can log myself in to get permission to copy this data?

Bear in mind I'm an absolute newbie, nothing is probably too simple to include!

---

### Post by Sef on 2008-01-05
Another option would be to download [Knoppix]("http://knoppix.com").  I have used it on computers to transfer data from a hard disk to a usb key.   Those computers would not boot up.

---

### Post by tim237 on 2008-01-05
Good idea, although I can't do this untill I can access another computer with a cd-rw, since I've got to have the live cd in. I'll try it when I can, but if anyone has any I can do now that'd be great.

---

### Post by louieb on 2008-01-05
Knoppix is great. I keep one laying around. 
But try one thing with the live CD. Open up Nautilus with root privileges.   
Open up the run dialog - Alt+F2
```
gksudo nautilus
```
See if that doesn't get you past the permission problem.

---

### Post by tim237 on 2008-01-05
I can only access the live CD's own file system this way, not the one on my computer.

---

### Post by louieb on 2008-01-05
Just tried it myself. Found a way to do it. Open up the partition(s) you want to copy stuff from and the destination too. 
Places > Computer as the regular user. 
Now run ```
gksudo nautilus
```

Click on filesystem and open the **/media** folder - Your hard drives partition(s) should be listed there. At lest thats the way it worked for me. 
Good Luck.

---

### Post by tim237 on 2008-01-07
Just in case anyone ever finds this post louieb's idea does work. Thank you very much to both you guys for your help.

---

