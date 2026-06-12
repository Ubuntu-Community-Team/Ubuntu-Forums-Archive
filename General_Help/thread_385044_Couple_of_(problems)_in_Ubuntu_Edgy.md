---
title: "Couple of (problems) in Ubuntu Edgy"
date: 2007-03-15
forum: General Help
---

### Post by jaind on 2007-03-15
I'm running Ubuntu-6.10 as a dual-boot system with windows. 

1) My laptop's sound doesnt seem to work after the system has come out of hibernate/suspend mode in Ubuntu.
2) My laptop eats batteries when its I hibernate Ubuntu(like 10% of full charge a day). Windows hibernation is fine. 

Just wondering if there's a fix for these.

~~

---

### Post by vicky1984 on 2007-03-26
i have a similar problem, also running edgy. when i resume from hibernate the sound no longer works. another problem is when it is booting after hibernation i get a 'no swap signature' error and when i use FREE it says the swap size it 0. i've tried rebooting and shutting down the computer completely and it hasn't resolved the problem.

---

### Post by Austin_KW on 2007-03-26
Hibernate will not work on my laptop, but while testing it, it trashed my swap area. Do a 'mkswap /dev/hdaX' (X being your swap partition) to remake your swap fs and then 'swapon /dev/hdaX' and all should be fixed.

---

