---
title: "Adept something, Crash?"
date: 2007-12-22
forum: General Help
---

### Post by Dojan5 on 2007-12-22
When i execute Adept, (Kubuntu Gutsy 7.10) i get the following error:
"The ATP database could not be opened! This may be caused by incorrect ATP configuration or some similar problem. Try running ATP-setup and ATP-get update in the terminal and see if it helps to resolve the problem"
I dont know what caused it, it just crashed third time i bringed it up...
And now it won't work.
[http://ubuntuforums.org/attachment.php?attachmentid=53950&stc=1&d=1198305414Snapshot]("http://ubuntuforums.org/attachment.php?attachmentid=53950&stc=1&d=1198305414")

---

### Post by Dojan5 on 2007-12-22
Sorry for soubleposting, Konqueror wont let me edit :mad:
Anyways, new problem encountered when trying to install a precompiled FireFox...
See attatchment

---

### Post by Dojan5 on 2007-12-22
Last post, i think...
When trying to do what Kubuntu want me to do...
Umm, yea, this comes up.
Correct me if im doing wrong.

---

### Post by pyronaut on 2007-12-22
trying using synaptic instead of adept....i find it easier to use

---

### Post by -grubby on 2007-12-22
```
sudo kate /etc/apt/sources.list
``` and remove line 74                       
(you may have to manually count)

---

### Post by Dojan5 on 2007-12-22
I tried to do it the way Nathan described, but i still get same problem.
And i don't have synaptic, and if i have to install it (which i think i would like to do) i'd only mess THAT up too...

---

### Post by Dojan5 on 2007-12-22
Sorry for double posting.
Still cant edit, think it is Konqueror..
Well, solved the problem, i realized that it wouldnt do anything because i modified the backup of the sources.list file on the desktop XD
Thanks!

---

