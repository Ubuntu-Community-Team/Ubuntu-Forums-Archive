---
title: "remove ubuntu packages"
date: 2006-12-12
forum: General Help
---

### Post by eddygrinder on 2006-12-12
Hello there! 

I've got a question: I've tried ubuntu a couple of times but i want to remove all the packages that i don't need. 
e.g - i don't have internet, at my home, and i want to remove all the packages that are related with this, but i can't because the dependences. 

How could i install ubuntu and remove all the things that i don't want? 


Thx a lot!

---

### Post by ajgreeny on 2006-12-12
If you decide what you don't want and then use synaptic to remove the packages, the software will only remove dependencies which are totally superfluous to what is left behind.  You should not find anything with missing dependencies if you do it that way.  Any dependency packages still needed by other packages you have not removed will remain.

You will probably find that removal of some of the gnome packages will also mean removing *ubuntu-desktop*.  Don't worry about this too much, it is only a meta-package which is used by the system to ensure that everything in ubuntu is actually there.  If you really want to remove some of these it is of little consequence overall.

---

