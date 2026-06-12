---
title: "vim: delete from curpos to specific character"
date: 2007-12-26
forum: General Help
---

### Post by engine on 2007-12-26
According to the online help, I reckon that ```
d\>
``` should delete from the current cursor position up to and including the next greater-than angle bracket. But when I try it, all I get is "E488: trailing characters"
Question 1: what is E488 trying to tell me?
Question 2: if ```
d\> 
```isn't the right command, what should I be using?
Thanks in advance

---

### Post by heindsight on 2007-12-26
It looks to me as of you tried to type ```
d\>
``` 
on the vim command line (ie you pressed : and then entered the command).
vim is trying to interpret your command as the ```
:[range] d[elete] [x]
``` command and then sees the '\>' as unexpected trailing characters.

What you're trying to do can be achieved with the ```
["x]d{motion}
``` 
Normal-mode command which deletes text that {motion} moves over (into register x). 
To use this command to delete up to (but not including) the next '>' character you can type ```
d/>
```
Note that it's a forward slash not a backslash and the command is *not* preceded by a colon.

If you're new to vim, I can recommend that you work through the vim tutorial at least once,
it's a great way to learn some of the everyday commands. Just run the command ```
vimtutor
``` in a terminal.

---

