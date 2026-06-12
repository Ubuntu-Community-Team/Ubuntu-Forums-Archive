---
title: "Issues with Phpmyadmin after upgrading to Xubuntu 19.04"
date: 2019-05-11
forum: General Help
---

### Post by samamclean on 2019-05-11
Hi all,

today I upgraded my laptop from Xubuntu 18.04, first to 18.10, then to 19.04

As part of the second upgrade, phpmyadmin was removed, and I'm absolutely confused and livid. 


I can't install phpmyadmin b/c it needs php7.2-mysql, and I can't install php7.2-mysql or mysqli and the error message that I get is 
"php7.2-mysql : Depends:  php7.2-common (= 7.2.15-0ubuntu3) but 7.2.17-0ubuntu0.18.04.1 is to be  installed"

is it possible to fix this so I can install phpmyadmin or has it been decided that the program will no longer be supported?

---

### Post by samamclean on 2019-05-11
So,

I managed to fix this issue. I had to add 

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) bionic-security main 

to my sources list, and then with that, I was able to access the php7.2-mysql package that was compatible with the newer version of php7.2 installed during the upgrade.

---

### Post by Tadaen_Sylvermane on 2019-05-11
Mixing releases is rarely a good idea. That being said I can't answer that question, however I can solve it.

Why did you upgrade from 18.04 in the first place? Was there a compelling requirement to do so or not If not then the answer is simply go back to 18.04. LTS exists to prevent exactly this kind of situation in my opinion. Saves you from having to change stuff every 6 months. A 5 year window gives plenty of time to test and sort out differences before upgrading a production system that you depend on.

Another option, forward port it. I don't know if this is a bad idea. Same process as backport but use the Bionic repos instead of a future release. I'd guess it would work, never tried it myself.

[https://wiki.debian.org/SimpleBackportCreation](https://wiki.debian.org/SimpleBackportCreation)

I use this to do personal backports on Ubuntu. Everything works the same, although I've never had rmadison work right, even on Debian. No clue what the point is of it, I just go straight to the webpage and get the dsc link and start with dget.

---

