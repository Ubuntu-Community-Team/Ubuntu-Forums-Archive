---
title: "Is it possible to make a echo popup in gnome?"
date: 2007-04-11
forum: General Help
---

### Post by Dr_Deadmeat on 2007-04-11
Hi...

I just wondered if it is a shell program or a command that makes a popup with the text you want in gnome (or kde) just like echo does in a terminal. I want to use it because I am using a bit ssh on my computers, and it would be cool just to be able to do it. :guitar:

---

### Post by heimo on 2007-04-11
Try with zenity.
```
sudo aptitude install zenity
```Then:
```
zenity --info --text='Hello World!'
```Will popup a window with "Hello World!".

Be sure to check lots of different options
```
 zenity --help-all
```

EDIT: Or did I misunderstand what you're looking for?

---

### Post by Dr_Deadmeat on 2007-04-12
It was excactly what I was looking for... Thanks a lot, you made my day =)

---

