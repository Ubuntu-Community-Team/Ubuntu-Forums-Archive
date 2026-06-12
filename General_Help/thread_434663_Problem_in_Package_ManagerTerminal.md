---
title: "Problem in Package Manager/Terminal"
date: 2007-05-06
forum: General Help
---

### Post by _Pieter_ on 2007-05-06
Hello,

The notification area gives the following error:

"  A error occured, please run Package Manager from the right-click menu or apt-get on a terminal to see what's wrong. The error message was: 'Error: Brokencount > 0'  "

Whenever I try to install anything with the terminal or add/remove.. , I get the following error message: 

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 

But, when I run 'dpkg --configure -a', it says:

dpkg: requested operation requires superuser privilege

What can I do? Any suggestions are more than welcome, but please keep in mind that I am completely new to Ubuntu and Linux, so please keep it simple:) 

Thanks!

---

### Post by Thingymebob on 2007-05-06
run **sudo dpkg --configure -a**

---

