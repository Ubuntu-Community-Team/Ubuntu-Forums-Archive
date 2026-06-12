---
title: "Console-only box! Beginner's questions."
date: 2005-09-19
forum: General Help
---

### Post by fresco on 2005-09-19
Greetings guys!
Here I am from newly installed Ubuntu without any wm and Xorg at all! It is very exciting to be in this situation - so many things to learn! :)

So here are my first questions:
1. Is it possible to run many programs within single tty? Each time I want to run several programs, I have to switch tty, log in and only then run application. It is so lame... :) There MUST be some other way! 
2. Are there basic Copy-Paste functions available within console? When you need to edit a big config file and add dozens of lines from other source, well, it's not so easy I must say... :)) 

It's all for now,
 Big Thanks!

---

### Post by SilentCacophony on 2005-09-19
I use **screen** and **gpm** for those abilities. Screen is a terminal multiplexer that uses key-bindings to control things, and gpm adds mouse cut-n-paste with the traditional linux highlight-then-middleclick method.

---

### Post by apswartz on 2005-09-19
After each command add an ampersand (&) and the program will run in the background. Then you can go on to the next program.

e.g.,
command &

---

### Post by fresco on 2005-09-19
Thank you both for help! Now I can do things much faster and smarter!

Here's a fresly-cooked question:

How can I specify filenames containing spaces? (e.g. ~/music/Oh Darling.mp3)

I've noticed that some applications use html - like paths. I've tried to write Oh%20Darling.mp3, but it didn't help. So I have typed ~/music/Oh*.mp3. Yeap, that helped, but it is acceptable only if filenames differ dramatically. But what to do if there are many files starting with the same word?  :grin:

---

### Post by apswartz on 2005-09-19
Use quotes around the whole filename.

---

### Post by ranf on 2005-09-19
[QUOTE=fresco]How can I specify filenames containing spaces? (e.g. ~/music/Oh Darling.mp3)[/QUOTE]
When you use command line completion then you see it uses backslashes to unquote special characters:
```
~/music/Oh\ Darling.mp3
```

---

### Post by fresco on 2005-09-19
Wow!!! Everything worked! Thank you all!   =D>

---

