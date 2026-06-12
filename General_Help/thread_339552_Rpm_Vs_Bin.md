---
title: "Rpm Vs Bin"
date: 2007-01-15
forum: General Help
---

### Post by Mba7eth on 2007-01-15
Hi everyone , 

I Just wondering which is better to download and why if you have a choose of a package in the following format : 
            1- rpm 
            2- bin



It's all years :)

 Mba7eth

---

### Post by ~LoKe on 2007-01-15
The rpm equivalent in Debian based distribution is .deb.  RPM is for Fedora and whatnot.

In Ubuntu, you can't use rpm's without using alien.

So, you're best off using .deb, or, if you must, .bin.

---

### Post by meng on 2007-01-15
What are you trying to install. Perhaps there's an Ubuntu or (ahem) Debian package available. The two choices you give are not preferred!

---

### Post by Mba7eth on 2007-01-15
may i ask you again ~LoKe :) 
if you had the choice of .deb and .bin which do you choose and why ?

(PS: .rpm +alian = .deb) 


Cheers, 

Mba7eth

---

### Post by Mba7eth on 2007-01-16
meng i'm new to linux world in general. Yesterday i had an adventure of installing jre5.bin but i had a headack untill i found how i can add the plugins in firefox. So i just wanna know if it is better to use a .deb or .rpm+alien=.deb rather than .bin 


Cheers, 
Mba7eth

---

### Post by meng on 2007-01-16
loke realizes that rpm+alien=deb (already mentioned in earlier post) but unfortunately, the deb generated doesn't always work as it should.

If you are trying to install Sun's Java runtime environment, then look here instead (it is in the repositories, which is why I asked you the question!)
[https://help.ubuntu.com/community/Java](https://help.ubuntu.com/community/Java)

---

### Post by Mba7eth on 2007-01-16
I more thing guys .... now i opened the realplayer download page to download ... and i had a choice 
an rpm and a bin :) 

So does choosing rpm (and after converting it to .deb)**_ saves alot of headack ???_**

---

### Post by meng on 2007-01-16
[https://help.ubuntu.com/community/RealplayerInstallationMethods](https://help.ubuntu.com/community/RealplayerInstallationMethods)

---

### Post by Unterseeboot_234 on 2007-01-16
Rarely, can I get a .bin to work. XaraLX worked but only after I unzipped it with Terminal instead of double-clicking the desktop icon. The .deb seem to know where to install automagically. The .bin, if it works, will go anywhere and I suspect because it is not deep inside user/local/... whatever that it cannot find some of the sym-links. It is a combination of the three that installs software. Sometimes only a ./configure, make and checkinstall will install what you want. .debs, IMHO are the better choice, but they don't always work. Repositories --> Synaptic is easiest for ubuntu.

---

