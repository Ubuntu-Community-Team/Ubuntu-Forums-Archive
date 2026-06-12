---
title: "Skype shows up in Chinese"
date: 2012-12-17
forum: General Help
---

### Post by kpuz on 2012-12-17
Hi, I just installed Skype 4.1 for linux and it works fine on my administrator account. However, on another user account on the same computer, the software starts in Chinese and is therefore impossible to use.

I'm thinking this is a language support problem but I'm not sure how to fix it. Any help is appreciated.

---

### Post by slixz85 on 2012-12-17
> **kpuz said:**
> Hi, I just installed Skype 4.1 for linux and it works fine on my administrator account. However, on another user account on the same computer, the software starts in Chinese and is therefore impossible to use.

I'm thinking this is a language support problem but I'm not sure how to fix it. Any help is appreciated.

I really don't know if this could fix it but I suggest installing localepurge "sudo apt-get install localepurge" then terminal will ask you which languages to keep and run through the whole list and make sure assuming you use english only that en and en_us ones are checked only then hit tab and click ok. then right after in terminal just type "sudo localepurge" and it will run through your programs and take out everything associated but english. I use this cause I only know english plus over time it cleans hundreds of MB from your system.

---

### Post by slixz85 on 2012-12-17
also you might no have to but if it dont instantly work try to reinstall skype but I would do that anyway besides aint too hard to "sudo apt-get purge skype" to remove it and configuration then "sudo apt-get install skype" to install of course.

---

