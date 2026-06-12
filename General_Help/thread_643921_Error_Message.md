---
title: "Error Message?"
date: 2007-12-18
forum: General Help
---

### Post by xveedsx on 2007-12-18
I am getting this error message:

E: Couldn't Find package jre-6u3-linux-i586

and I tried to install something else and it gave me the same error, but with its file name.

Any help would rock =)

Thanks Veeds!

---

### Post by taurus on 2007-12-18
Can you post the exact command you ran and the whole error message?  Are you trying to install Sun's java 1.6?

---

### Post by xveedsx on 2007-12-18
Yeah here:

veeds@veeds-laptop:~$ sudo apt-get update
[sudo] password for veeds:
Ign cdrom://Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016) gutsy/main Translation-en_US
Ign cdrom://Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016) gutsy/restricted Translation-en_US
Reading package lists... Done
veeds@veeds-laptop:~$ sudo apt-get install java
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package java
veeds@veeds-laptop:~$ sudo apt-get install jre-6u3-linux-i586
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package jre-6u3-linux-i586
veeds@veeds-laptop:~$ 


andddd here i sit, trying to install programs =) Idk, I have it on my desktop, would that matter? Is there a certain place in my hdd that I need it to be?

Thanks!

---

### Post by taurus on 2007-12-18
```
sudo apt-get install sun-java6-bin sun-java6-jre sun-java6-plugin
java -version
```

---

### Post by ajgreeny on 2007-12-18
As someone who is presumably new to ubuntu, if not linux, it would have been much much easier to open synaptic and search for **java** which would have found all those shown above.  **Synaptic** and/or **Add/Remove programs** is your best friend, so make use of it, and only try installing programs in other ways if it is absolutely necessary.

---

### Post by xveedsx on 2007-12-19
Alright I will try it when I get home. Thank you. 

Oh, and the reason why I always do it the hard way, is because I learn. Which is the whole point of installing ubuntu. I Just found out my friend has done a LOT of programming, and he knows so much its like holy crap. Haha, again, thank you.

---

### Post by xveedsx on 2007-12-19
Alright so Im home and here is what I did

veeds@veeds-laptop:~$ sudo apt-get install sun-java6-bin sun-java6-jre sun-java6-plugin java -version
apt 0.7.6ubuntu14 for i386 compiled on Oct 15 2007 20:39:10
Supported modules:
 Ver: Standard .deb
 Pkg:  Debian dpkg interface (Priority 30)
 S.L: 'deb' Standard Debian binary tree
 S.L: 'deb-src' Standard Debian source tree
 Idx: Debian Source Index
 Idx: Debian Package Index
 Idx: Debian Translation Index
 Idx: Debian dpkg status file
E: Command line option 'e' [from -version] is not known.
veeds@veeds-laptop:~$ 


and thats what I got. Also I DID try to go through applications ADD/REMOVE Java, and it just looks like its getting ready to install then it just blinks out. I got to check to see if it installed, andddd notta. Idk what happened.

Help? Hehe. Thanks for all the continued support.

---

