---
title: "(SOLVED)Pretty sure I messed up /etc/apt/sources.list and I'm not sure how to fix it."
date: 2018-07-19
forum: General Help
---

### Post by Arminius on 2018-07-19
I type ```
sudo apt-get install program
```
it returns ```
E: Type 'sudo' is not known on line 54 in source list /etc/apt/sources.list
```
I type ```
sudo nano /etc/apt/sources.list.
```

and what comes up doesn't seem to contain anything?
```
GNU nano 2.9.3                              /etc/apt/sources.list.
```
Absolutely nothing else until the menu at the bottom.

---

### Post by deadflowr on 2018-07-19
remove the last dot
```
sudo nano /etc/apt/sources.list
```

---

### Post by Arminius on 2018-07-19
Thamnks, solved.

---

### Post by deadflowr on 2018-07-19
Bonus:
For what it's worth Ubuntu 18.04's apt has a new edit command to edit the sources.list file
```
sudo apt edit-sources
```
which will open the source.list file with you preferred editor, be it nano or vi or something else.
see
```
man apt
``` 
for more on apt commands, new and old.

---

