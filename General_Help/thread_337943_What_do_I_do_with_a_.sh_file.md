---
title: "What do I do with a .sh file?"
date: 2007-01-13
forum: General Help
---

### Post by jloehrlein on 2007-01-13
Coming from windows total newb question but what do I do with a .sh file? As in I downloaded a program I want to use it came in a .sh file and I have no idea what to do with it.

---

### Post by PriceChild on 2007-01-13
```
sh ./<<name>>.sh
```will run the file.

Or ```
sudo sh ./<<name>>/sh
```will do it.

What program is it?

---

### Post by chavo on 2007-01-13
It's a shell script. You can either just run it with bash like this -> bash filename.sh or you can make it executable and run it -> chmod +x filename.sh && ./filename.sh.
Also if it's something you will be running quite often make it executable and stick it in your $PATH somewhere, like ~/bin. Now you can run it in a terminal by just using the filename.

---

### Post by bigken on 2007-01-13
you open a terminal and cd to where ever the file is ie cd Desktop the run it from there 

ken@stratocaster:~$ cd Desktop
ken@stratocaster:~/Desktop$ sudo sh ./name of file.sh
Password:

---

### Post by bodhi.zazen on 2007-01-13
> **chavo said:**
> It's a shell script. You can either just run it with bash like this -> bash filename.sh or you can make it executable and run it -> chmod +x filename.sh && ./filename.sh.
Also if it's something you will be running quite often make it executable and stick it in your $PATH somewhere, like ~/bin. Now you can run it in a terminal by just using the filename.

What chavo said, particularly 

chmod a+x file.sh

What is it ?

I am surprised no one cautioned against running unknown scripts as root !!

So, I'll do it then :p

[color=red]Don't run as root unless you trust the source[/color] :)

---

