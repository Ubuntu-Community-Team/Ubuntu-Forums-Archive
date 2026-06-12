---
title: "I can not open python  .py files with double click"
date: 2019-02-09
forum: General Help
---

### Post by feesgo on 2019-02-09
I have several python .py files 

I opened it and ran it   when I   double click with my mouse

Nowadays my python .py files does not open and run anymore when I   double click with my mouse


To fix this troble I have:

* place 

#!/usr/bin/env python 

in the fist line on my .py files (its always have been there)

* chmod +x my_file.py

* set python3 as default application to open .py files

* set python2 as default application to open .py files

* set env as default application to open .py files


All this mess start when   I set GEDIT as default program to open .txt files and other files of type "plain text document" from NEMO FILE MANAGER.

[IMG]https://i.imgur.com/QJDq5MQ.jpg[/IMG]

How can I fix this mess?

---

### Post by again? on 2019-02-09
Check your setting in **nautilus > preferences > behaviour > executable text files**

Quite a while ago nautilus changed the default setting to "Display Them"....used to be "ask what to do".

---

