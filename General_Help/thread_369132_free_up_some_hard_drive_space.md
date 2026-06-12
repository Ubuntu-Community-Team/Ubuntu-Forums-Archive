---
title: "free up some hard drive space"
date: 2007-02-24
forum: General Help
---

### Post by nomowindows on 2007-02-24
hello fellow ubuntuers, I came across this cool little command and freed up 300MB on my hard disk. After you have updated and upgraded your system, ubuntu saves the packages even after they have been installed. You can get rid of the packages with the command   sudo apt-get clean 
Hope it works for all of yall too.

---

### Post by Athropos on 2007-02-24
You can also tell Synaptic to not keep packages after their installation ("Preferences->Files->Delete downloaded packages after installation").

---

### Post by nomowindows on 2007-02-24
thanks athropos. I am new to all this...but im learnin.

---

### Post by ~LoKe on 2007-02-24
There are more, too.
> loke@x04d:~$ sudo apt-get clean
loke@x04d:~$ sudo apt-get autoremove
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
loke@x04d:~$ sudo apt-get autoclean
Reading package lists... Done
Building dependency tree       
Reading state information... Done

---

### Post by nomowindows on 2007-02-24
thank you too Loke. LOL I thought i was a little ahead of the curve..but it looks like yall got it covered.

---

