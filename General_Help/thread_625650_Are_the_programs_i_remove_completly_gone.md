---
title: "Are the programs i remove completly gone?"
date: 2007-11-28
forum: General Help
---

### Post by kdarkentity on 2007-11-28
It seems as if whenever i remove a package or a program that i don't like or need anymore my hard drive space increases rather than decreases. Why could tis be? Where do the files i removed go?, or are they deleted?

---

### Post by kpkeerthi on 2007-11-28
Thats is strange. I assume that you add and remove packages  using apt-get or aptitude. With that said, when you remove a package, the files get removed from the installed locations. However, apt caches the package (the .deb file) in /var/cache/apt which will be retained unless you instruct it to clean the cache.

---

### Post by Sef on 2007-11-28
> It seems as if whenever i remove a package or a program that i don't like or need anymore my hard drive space increases rather than decreases. Why could tis be?

When you remove a package or program, your hard drive space should increase.  

How do you remove them?

---

### Post by Cochise on 2007-11-28
to clear the apt cache and unneeded dependencies, open a terminal and type:

> sudo apt-get autoremove

This will remove dependences that are not needed anymore.

> sudo apt-get autoclean

This will clear the apt cache.

---

### Post by kdarkentity on 2007-11-28
I use both synaptic and add or remove to install and remove programs. I just went to /var/cache/apt and there is about 633 mb of files in there, however i believe that these files consist mostly of old program files before they were updated. How can i remove these files?

---

### Post by atlfalcons866 on 2007-11-28
sudo apt-get clean

---

### Post by kdarkentity on 2007-11-28
Thanks all that freed up about 700 mb of space, there may still be some junk left on my hard drive somewhere but im not too too worried about it at the moment.

---

