---
title: "lubuntu software center problems"
date: 2014-06-23
forum: General Help
---

### Post by Luke_Lenci on 2014-06-23
I try installing software on my Acer net-book mini but all I get are errors installing (on most things) most, being something like this:
[ATTACH=CONFIG]254188[/ATTACH]

---

### Post by deadflowr on 2014-06-23
Moved to General Help

---

### Post by oldos2er on 2014-06-23
Did you try the suggestion to run ```
sudo apt-get install -f
```?

---

### Post by Luke_Lenci on 2014-06-23
Yeah it gave me a few problems saying things were unavailable.
Another screenshot:
[ATTACH=CONFIG]254195[/ATTACH]
Also, I believe I am root as I am the only user so shouldn't I automatically be root? If not then a link on how to become root would be helpful. ^_^

---

### Post by deadflowr on 2014-06-23
No, you are you.
You have the ability to run root level rights, using sudo.
[Ubuntu Root 101]("https://help.ubuntu.com/community/RootSudo")
try again with sudo
```
sudo apt-get install -f
```

---

### Post by Luke_Lenci on 2014-06-24
I feel like such a newbie. Thanks for the help deadflowr! :)

---

