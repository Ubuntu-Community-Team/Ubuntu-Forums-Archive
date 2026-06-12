---
title: "[SOLVED] How do I bind a command in ubuntu?"
date: 2008-01-27
forum: General Help
---

### Post by ataxicwolf on 2008-01-27
So I've written a python program which encrypts text files. Rather than running this by using:
python /home/ataxicwolf/python/encrypt.py
I would like to be able to simply type into the terminal:
encrypt
and then have it load the python program. Thanks for any help!

P.S: Is there any way to add parameters that it could pass on to the program?

Ex: I type in encrypt file.txt, file.txt, and then the python program could load those? Thanks again for any help :D

---

### Post by mortsahl on 2008-01-27
Open a terminal, edit .bash_aliases, add a line ...

alias encrypt /home/ataxicwolf/python/encrypt.py

save the file, close the terminal, open a terminal and type encrypt

---

### Post by p_quarles on 2008-01-27
Close. The syntax of a Bash alias works like so:
```
alias encrypt='python /home/ataxicwolf/python/encrypt.py'
```
And, yes, you can add any arguments/options/parameters that the command itself would take to the part inside the single quotes.

---

### Post by mortsahl on 2008-01-27
Yep .. that's what I get for typing without checking ... been a while since I edited my aliases file.

---

### Post by ataxicwolf on 2008-01-27
I opened my terminal, and typed in: sudo gedit .bash_aliases
it opened the text editor, (the inside of the file was empty for the time being) and then added
the line: alias encrypt='python /home/ataxicwolf/python/encrypt.py'
When I typed encrypt into the terminal, it claimed that the command could not be found.

---

### Post by p_quarles on 2008-01-27
Run:
```
gedit .bashrc
```
Then, add or uncomment the following three lines:
```
if [ -f ~/.bash_aliases ]; then
. ~/.bash_aliases

fi
```
Save, then, close and open the terminal again for the change to take effect.

---

### Post by ataxicwolf on 2008-01-27
yay! it works. Thanks a bunch for the help guys :D

---

