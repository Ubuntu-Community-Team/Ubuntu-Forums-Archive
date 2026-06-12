---
title: "Kylix 3.0 Open running problems..."
date: 2005-06-02
forum: General Help
---

### Post by jookie on 2005-06-02
Hello,

I've downloaded the Borland Kylix 3.0 Open thing an I'm trying to get it running, but there were several problems:
[list=1]
[*]there was a dependency on libstdc++libc6.1-1.so.2, which I tried to fix as some forum said (to create a symlink on libstdc++.so.6 or something like that)
[*]there was also a dependency on libxaw.so.6, so I tried to install libxaw6, libxaw6-dev and then I've createt another symlink...
[/list]

The C++ Builder (Kylix) then runs allmost OK - in some cases it shows its windows correctly, but when I write an arrow to reference to the objects properties ('->') it crashes imidietly when trying to find out what properties and methods the object has.
The second type of trouble it sometimes got is that the menu fonts and other fonts used in Kylix are one pixel high (so it's just a bunch of pixels and it's unreadable) - this second problem seems like the problem with libxaw... 

Anyone has any idea how to fix this or what is the right forum to ask on?
Thanx... Please drop me an e-mail at jookie[et]szm[dod]sk if you find anything usefulll....

---

### Post by jookie on 2005-06-03
Ok, the menus are OK for now, but I still got the problem with that '->' thing... Anyone?
It says then:
/usr/local/bin/startbcb: line 27: 13157 killed                 /usr/local/kylix3/bin/bcblin $*

---

### Post by lvincent on 2005-06-16
kylix 3 is not really ideal for Ubuntu. im running kylix 3 but it is under RH9. and i did have a lot fixes and patches. you can search for kylix unofficial patches at google. im not sure if these patches is equivalent to kylix 3 for c++, since im after for kylix 3 for delphi.

lvincent

---

