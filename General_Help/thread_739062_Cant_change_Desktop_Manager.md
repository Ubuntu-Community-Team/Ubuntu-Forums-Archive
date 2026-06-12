---
title: "Cant change Desktop Manager"
date: 2008-03-29
forum: General Help
---

### Post by Dojan5 on 2008-03-29
I have a problem.
Since i installed enlightenment i havent been able to change the Desktop Manager.
I have GNOME and Enlightenment installed, but i cant use GNOME.
There is no menu on the login-screen that i can choose desktop manager. And i dont know how to change Login screen in E... Im using E17 DM and GNOME something, i cant remember....
Please help, there are things i need to do in GNOME, but... Yaa...

---

### Post by gobbles414 on 2008-03-29
> **Dojan5 said:**
> I have a problem.
Since i installed enlightenment i havent been able to change the Desktop Manager.
I have GNOME and Enlightenment installed, but i cant use GNOME.
There is no menu on the login-screen that i can choose desktop manager. And i dont know how to change Login screen in E... Im using E17 DM and GNOME something, i cant remember....
Please help, there are things i need to do in GNOME, but... Yaa...

Look at the bottom left of your login screen and go *Options => Select Session => GNOME*. You'll be asked if you want to make GNOME your default desktop manager, or use it just for the current session. Make whichever choice you feel is appropriate for your situation. Does this work?

---

### Post by Dojan5 on 2008-03-31
> **gobbles414 said:**
> Look at the bottom left of your login screen and go *Options => Select Session => GNOME*. You'll be asked if you want to make GNOME your default desktop manager, or use it just for the current session. Make whichever choice you feel is appropriate for your situation. Does this work?

There isnt one.
Thats why i asked for help on the forums...

---

### Post by Oldsoldier2003 on 2008-03-31
> **Dojan5 said:**
> There isnt one.
Thats why i asked for help on the forums...

try 
```
metacity --replace
```

---

### Post by smartboyathome on 2008-03-31
> **Oldsoldier2003 said:**
> try 
```
metacity --replace
```

That won't work if you haven't logged in. Instead, try control+alt+f1, log in, and then type startx.

---

