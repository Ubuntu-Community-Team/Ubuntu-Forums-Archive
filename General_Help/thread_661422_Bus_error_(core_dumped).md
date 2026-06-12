---
title: "Bus error (core dumped)"
date: 2008-01-07
forum: General Help
---

### Post by gilbert27 on 2008-01-07
Hi!!
Under Kubuntu Gutsy, I have this bug! 

root@localhost:~# ldconfig
Bus error (core dumped)
root@localhost:~# dpkg --configure -a
Paramétrage de libc6 (2.6.1-1ubuntu10) ...

Processing triggers for libc6 ...
ldconfig deferred processing now taking place
Bus error (core dumped)
dpkg: le sous-processus post-installation script a retourné une erreur de sortie d'état 135


apt-get , synaptic, adept_manager ...etc doesn't work anymore! 

Any ideas how to solve this problem? 

Thanks!

---

### Post by gilbert27 on 2008-01-08
Solved!!!

the solution was found here :::&#12288;[http://ubuntuforums.org/showthread.php?p=4040893](http://ubuntuforums.org/showthread.php?p=4040893)

I had to do :::: 
> strace ldconfig

the culprit was "libncursesw5" .... so I had to reinstalled it! 

and  
> ldconfig 

and 
> dpkg --configure -a 

Now everythings works fine again! 

It seems that K/Ubuntu is not perfect! ... still have some bugs to deal  with  once in a while!

---

### Post by RichardCookson on 2008-01-18
I have a similar problem whenever I run apt-get or synaptic

I've followed the instructions and the problem seems to be libc6-i686

The problem is I can't re-install it. Neither apt-get or synaptic will work. Is there any other way to reinstall this package? Is there any way I can use a repair disk to reinstall without losing all my home directory?

---

