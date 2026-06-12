---
title: "Problem after crash of .deb installation. Help!"
date: 2007-08-12
forum: General Help
---

### Post by dk@ on 2007-08-12
Hi! I have following problem.

I have downloaded latest .deb of Truecrypt. It was in .tar.gz archive. And I have started installation from Archive-manager window. During installation I'v closed Archive-manager (yes, it's stupid, but I thought it's already somewhere in temp dir... like in Win). Installation process was corrupted. I think, that some files were installed.

Now I following problems:

1) I can't continue installation just running truecrypt_4.3a-0_i386.deb. Every time there is message: 
> Couldn't  open  truecrypt_4.3a-0_i386.deb. Package might be corrupted or you are not allowed to open this file. bla-bla-bla... 

2) I can't run Synaptic. The message is:
> E: The package truecrypt needs to be reinstalled, but I can't find an archive for it.
E: Internal error opening cache (1). Please report.

3) I can't uninstall and reinstall Truecrypt via Console:
> work@work-desktop:~/Downloads$ sudo apt-get install truecrypt_4.3a-0_i386.deb
Password:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: The package truecrypt needs to be reinstalled, but I can't find an archive for it.
work@work-desktop:~/Downloads$ sudo apt-get remove truecrypt_4.3a-0_i386.deb
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: The package truecrypt needs to be reinstalled, but I can't find an archive for it.


How to:
- Completely uninstall Truecrypt and install it again?
- Repair Synaptic? 

Thanks!

PS: I run under 7.04.

---

### Post by chewearn on 2007-08-12
See here:
[http://ubuntuforums.org/showthread.php?t=518991](http://ubuntuforums.org/showthread.php?t=518991)

---

### Post by dk@ on 2007-08-12
Thank you!

> sudo dpkg --remove --force-remove-reinstreq truecrypt

works!

---

