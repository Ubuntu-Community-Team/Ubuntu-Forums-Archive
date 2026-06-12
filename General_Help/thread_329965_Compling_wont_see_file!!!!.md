---
title: "Compling wont see file!!!!"
date: 2007-01-02
forum: General Help
---

### Post by oasmar on 2007-01-02
Hello, this is my first post and problem with ubuntu. I have created a file that needs to be compiled. I have called it loader and saved it as [COLOR="Lime"]loader.cpp[/COLOR] which is in my home folder. I open terminal and type [COLOR="Lime"]gcc loader.cpp[/COLOR] but all that i get is 

[COLOR="Lime"]gcc: loader.cpp: No such file or directory
gcc: no input files
[/COLOR]

I know it is ther because when i use [COLOR="Lime"]ls[/COLOR] it shows the file.

---

### Post by bodhi.zazen on 2007-01-02
> **oasmar said:**
> Hello, this is my first post and problem with ubuntu. I have created a file that needs to be compiled. I have called it loader and saved it as [COLOR="Lime"]loader.cpp[/COLOR] which is in my home folder. I open terminal and type [COLOR="Lime"]gcc loader.cpp[/COLOR] but all that i get is 

[COLOR="Lime"]gcc: loader.cpp: No such file or directory
gcc: no input files
[/COLOR]

I know it is ther because when i use [COLOR="Lime"]ls[/COLOR] it shows the file.

[color=red]gcc ./loader.cpp[/color]

---

