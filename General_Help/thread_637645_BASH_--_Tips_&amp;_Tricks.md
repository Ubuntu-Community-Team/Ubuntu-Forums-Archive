---
title: "BASH -- Tips &amp; Tricks"
date: 2007-12-11
forum: General Help
---

### Post by subs on 2007-12-11
[SIZE=4][B]Bored of Spelling Mistakes....
[/B][/SIZE]Add
 > shopt -s cdspell
 to your .bashrc. 

Now spelling mistakes like ect instead of etc are ignored.

[SIZE=4][B]Saving BASH History
[/B][/SIZE]If you are typing commands in a terminal, later you open another one and use that for a while, the new terminal will not remember any of the commands typed in the first one. After which if you close the first terminal, and then the second will overwrite any of the commands typed in the first terminal. To fix it edit your .bashrc file and add the lines
> shopt -s histappend
PROMPT_COMMAND='history -a'
and then save the file. This makes the terminal append the history of the commands typed in the terminal and not overwrite it

:popcorn::popcorn:

---

### Post by K.Mandla on 2007-12-20
Moved to General Help.

---

