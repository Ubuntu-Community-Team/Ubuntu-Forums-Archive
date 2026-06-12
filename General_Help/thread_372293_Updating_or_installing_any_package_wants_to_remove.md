---
title: "Updating or installing any package wants to remove something else?"
date: 2007-02-28
forum: General Help
---

### Post by AAJ on 2007-02-28
another question :-

when i try to updating or installing any package it asks me every time to remove kommander 


Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Writing extended state information... Done
Building tag database... Done             
The following packages are unused and will be REMOVED:
  kommander 
0 packages upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 3863kB will be freed.
Do you want to continue? [Y/n/?] n
Abort.


I don't know why ??? i am using this software and it is tells me to remove it.

i am using Gnome Desktop

---

### Post by aysiu on 2007-02-28
Well, *aptitude* is smart, but sometimes it thinks it's smarter than it really is. If you're using Edgy Eft, you can use *apt-get* and still have the ability to remove unused dependencies. Are you using Dapper Drake?

By the way, since this is a new problem, I moved it to a new thread.

---

