---
title: "shell prompt bug"
date: 2014-07-18
forum: General Help
---

### Post by pomaznoy on 2014-07-18
HI all!!

in 12.04 I encountered a bug I thought will be fixed in 14.04 but it still remains. It is very hard to explain in words so I was not able to find the answer on the net. Strange behavior of the shell begins when I am operating with long commands and it becomes really annoying since I am using ipython for data analysis. Sometimes when I want to rerun long command I begin to scoll back using control-P (or up-arrow), but the command is not displayed correctly. It truncates the line and if I jump to the beginning of the command it places the cursor on the previous output.
This  picture  I hope will explain the problem (it is from the ipython shell but the issue can be in the normal prompt)

[IMG]https://dl.dropboxusercontent.com/u/60309347/Screenshot%20from%202014-07-18%2017%3A21%3A44.png[/IMG]

Any suggestions?

---

### Post by sudodus on 2014-07-18
Welcome to the Ubuntu Forums :-)

I'm no expert in this field, but maybe a few questions (and your answers) will get your thread going and making more people contribute.

- Is it the same behaviour in bash as in python?

- Is this behaviour coming, when lines are too long and cut into two at the right end of the window?

- Does it change when you change the size of the window (while still running python)?

---

### Post by sedawk on 2014-07-18
I know similar misbehaviour from different environments when dealing with long lines.
Try a different terminal like xterm, gnome-terminal, kterminal, ... (I' m not sure what the default is with ubuntu).
After resizing a terminal you should also run command line tool "reset" once.

---

### Post by pomaznoy on 2014-07-24
1. This problem is encountered mainly in ipython shell (though I remember such problems with just bash but can't reproduce it right now)
2. Usually it happens with long commands but I am not sure if it is the cause (according to this thread [http://unix.stackexchange.com/questions/105958/issue-with-terminal-prompt](http://unix.stackexchange.com/questions/105958/issue-with-terminal-prompt) problem can be with the symbols)
3. window size changing does make effect on the behavior. Resizing the window to default  size solved the issue

---

### Post by pomaznoy on 2014-07-24
I tried different terminals and don't know why but Uxterm is the one working without this "bug"  :p. All others display the same behavior
Maybe something with the Unicode chars?

---

### Post by sudodus on 2014-07-24
If you are happy with Uxterm, please click on **Thread Tools** at the top of the page and mark this thread as SOLVED.

---

### Post by pomaznoy on 2014-07-24
Marking as Solved. The reason why this is happening is still obscure though

---

