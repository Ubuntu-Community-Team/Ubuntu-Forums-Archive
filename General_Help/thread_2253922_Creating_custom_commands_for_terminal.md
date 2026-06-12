---
title: "Creating custom commands for terminal"
date: 2014-11-23
forum: General Help
---

### Post by DVD-R on 2014-11-23
I'm dabbling with creating a few ultra simple custom commands for the terminal.
I've successfully created a few global variables.
My new variables are active as global variables and I can use them in any terminal.
Typing in the terminal cd $docs will take me to my Documents folder.
Typing in the terminal cd $desk will take me to my Desktop folder.

It then occurred to me that it would be cool if I could just type in docs, or desk to do the same thing.
That would require I create a command file named docs or desk that could be executed by the terminal.
Is there any documentation that anyone can point me to to show me how to make those files?

Very sincere thanks!
dw :-]

---

### Post by Lars Noodén on 2014-11-23
The usual way has been to assign aliases, but you can also assign functions.  When you have ones that you like, you can put them in ~/.bashrc.  
The ultimate reference would be the manual page for bash (type "man bash") but that will give you way more than you need at the beginning and is more of a reference work.

---

### Post by deadflowr on 2014-11-23
You mean you want something like aliases?
If so, then what you do is either add entries to your .bashrc file or create a .bash_aliases file and add line like so
```
alias docs='cd $docs'
```
save it, and restart the terminal.

ninja'd

---

### Post by DVD-R on 2014-11-23
Thanks!
Yes.... I found it by adding them as alias arguments in the ~/.bashrc file
They work great!!
Thanks!!! :-D

---

