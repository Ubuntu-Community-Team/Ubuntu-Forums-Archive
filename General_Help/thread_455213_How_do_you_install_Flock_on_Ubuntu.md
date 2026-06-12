---
title: "How do you install Flock on Ubuntu?"
date: 2007-05-26
forum: General Help
---

### Post by DcThePurger on 2007-05-26
If I'm correct, then you have to use terminals? What is the "cd" command that I need to type in the terminal?

---

### Post by DcThePurger on 2007-05-26
hello?

---

### Post by shen-an-doah on 2007-05-26
cd changes directory.

So "cd /home/andy/downloads" takes me to my downloads folder. If you're unsure what a command does, use whatis, e.g "whatis cd", or for more complete instructions, use man, e.g "man cd".

Edit: I've just discovered that man and whatis tell you nothing about cd. Oh well, they're useful for other stuff...

---

### Post by Cows on 2007-05-26
How do you exit the man page.. because when I type
```
man <command>
```

It opens up the man in terminal and I can read it but the problem is when I want to exit the man to go back to my terminal window I can't ( I don't know the key ) so I have to close my terminal and open up another one.

---

### Post by shen-an-doah on 2007-05-26
Ctrl+z stops any command in a terminal.

---

### Post by imjustabill on 2007-05-26
You can get the .deb here:
[http://www.getdeb.net/release.php?id=891](http://www.getdeb.net/release.php?id=891)

---

### Post by Cows on 2007-05-26
> **shen-an-doah said:**
> Ctrl+z stops any command in a terminal.

Ok thanks :).

---

### Post by WW on 2007-05-26
Don't use ctrl-Z.  ctrl-Z "stops" the program, but only in the sense that the process is pushed to the background and control of the terminal returns to the shell.  The program is still there.  To bring it back after pressing ctrl-Z, enter the **fg** command in the terminal.

To exit **man**, just hit **q**.

---

### Post by DcThePurger on 2007-05-27
It didn't help when I typed that command in using my account name. Just to let you know that the flock tarball file is on my desktop.

---

