---
title: "visual: error while loading shared libraries: libgtk-1.2.so.0: cannot open shared obj"
date: 2015-03-28
forum: General Help
---

### Post by jalis on 2015-03-28
when i am trying to visual the quicksort algorithm then this line show me {visual: error while loading shared libraries: libgtk-1.2.so.0: cannot open shared object file: No such file or directory
}  . I am using ubuntu 10.04 lucid i686 . plz help me to solve this problem .


thanks in advance .

---

### Post by Impavidus on 2015-03-28
It seems that libgtk-1.2 is not present on your system. gtk is not part of the server release, only of the desktop release. 10.04 desktop is no longer supported, meaning that it could be broken in many ways. Besides, 10.04 server only has a few weeks of support left. I suggest you move on to 14.04 LTS using a fresh install.

[Recommendations on EOL releases](http://ubuntuforums.org/showthread.php?t=2229730)

---

