---
title: "Wine + MDAC"
date: 2005-08-25
forum: General Help
---

### Post by Swad on 2005-08-25
I am trying to get MDAC 2.8 installed, but so far I just get errors.  I currently have wine and libwine deb packages installed from the offical Wine repository, and winetools from backports I believe.  I was successful in getting IE6 w/SP1 installed and some other misc. stuff.  I have had no luck with MDAC 2.8, though.  I've used various resources for information on getting stuff working in Wine including [this](http://www.frankscorner.org/index.php?p=ie6).  Anyway, has anyone had luck getting MDAC going in the latest Wine?  If so, are there any gotchas I need to be aware of?

Thanks for any information.  I'll keep looking through the various other Wine posts and HOWTOs here.

---

### Post by drdnl on 2005-10-27
I have the same problem, it refuses to copy the msvcrt.dll from one tmp dir to the system32, worst part is that it seems to be quite rare too. Anyone?

---

### Post by loyeyoung on 2006-12-07
This is an old thread, but I figured out how to solve. Problem is that there's already a copy of msvcrt.dll in system32. Move the file that's in c:\windows\system32 to c:\windows. If in your particular situation, the Wine version works better than the Microsoft version, after you have finished installing MDAC, move the MS version out of the way some place (in case you need it back), and copy c:\windows\msvcrt.dll (the Wine version) back to c:\windows\system32\.

Loye Young
Laredo, Texas

---

