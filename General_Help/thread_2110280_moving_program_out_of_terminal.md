---
title: "moving program out of terminal?"
date: 2013-01-29
forum: General Help
---

### Post by alphaamanitin on 2013-01-29
Hey Guys,

Is it possible, and if so what is the easiest way, to open a program and move it from the terminal so that when I close the terminal the program stays open?  

For instance, I don't like to open thundar with gksu and navigate to my file and open it.  I would prefer to open it in the command line, but I don't want to have to keep the command line open.  So basically, what would I add to this command to allow me to close the terminal after opening:```
gksu leafpad /root/whatever.file
```Thanks 

AlphaA

---

### Post by Cheesehead on 2013-01-29
Use the 'screen' or 'byobu' applications to keep a terminal session alive between logins.

---

### Post by Gotti on 2013-01-29
Have you tried hitting ctrl+z to suspend it then typing "bg" to put it in the background? Then you should be able to close the terminal by typing "exit" (Sometiems hitting the x on the box will still close the backghround application.)

---

### Post by srekcahrai on 2013-01-29
```

gksu leafpad /root/whatever.file &

```
Now you can press Ctrl + C and close the terminal.

---

### Post by stinkeye on 2013-01-30
-
```
gksu leafpad /root/whatever.file **& disown**
```
Allows you to just close the terminal.

---

### Post by Habitual on 2013-01-30
> **alphaamanitin said:**
>  I don't want to have to keep the command line open.  So basically, what would I add to this command to allow me to close the terminal after opening:```
gksu leafpad /root/whatever.file
```

```
gksu leafpad /root/whatever.file ; exit
```?

---

