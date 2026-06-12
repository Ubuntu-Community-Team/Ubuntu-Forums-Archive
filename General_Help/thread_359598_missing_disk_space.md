---
title: "missing disk space"
date: 2007-02-12
forum: General Help
---

### Post by craig.brisbane on 2007-02-12
Hi, I have a problem with missing disk space, being new to ubuntu and linux - I not sure how to find the problem.

I have a small network of computers at home, one win2000 (my partner uses) , a ubuntu desk top that I use and a ubuntu desktop which acts a central file storage. The problem is with the file storage computer.

The file storage computer has 6.06 ubuntu, it as 2 hard drives. On the first hd  is the  operating system and the second drive with  /home. Nothing else apart from mysql and phpadmin has been installed. For some reason the first hard drive with the operating system is 92% full - 55gb.

How can I find what is clogging up the system? 

thanks
Craig

---

### Post by Ramses de Norre on 2007-02-12
```
sudo du /|sort -n
```
That will give you a list with all files and folders in ascending order.

---

### Post by Kateikyoushi on 2007-02-12
You could check the size of directories to see which one takes up the space.

Coult try this as well to list big files, in this case which are bigger than 10MB.
```
sudo find / -type f -size +10000k
```

---

### Post by craig.brisbane on 2007-02-12
Hello Ramses and Kateikyouski. 

Thank you both for your replies - they both helped. I found a number of old deleted backup files in the root  .Trash directory under / - deleted them and now only have 5% usage of the HD.

Craig

---

### Post by B-Con on 2007-02-14
Thanks for those tips too, guys. I encountered this exact same problem (two days ago when this thread was originally created, but I just now found it) and just had a huge file sitting in my trash. I can't believe I missed it. |-(

---

### Post by GrumpyBob on 2007-02-14
I had a full disk, which turned out to be due to Beagle accumulating vast log files (some files >1Gb!).  Problem has stopped since I uninstalled Beagle, then reinstalled without the Evolution plugin.

Robert

---

