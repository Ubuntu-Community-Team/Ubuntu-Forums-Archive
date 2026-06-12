---
title: "Coloured bash prompt, now I get tput error when using scp"
date: 2013-02-10
forum: General Help
---

### Post by CaptainMark on 2013-02-10
Today I used this website to colourise my bash prompt [http://www.kirsle.net/wizards/ps1.html](http://www.kirsle.net/wizards/ps1.html), now when using scp I get this error, the copy will still go through okay though ```
tput: No value for $TERM and no -T specified
```Does anyone have any idea why I get this error, the website doesn't hint that I might have any such problem, I might have to redo the prompt manually using the method I've used before, I just thought it would be nice to be able to generate them automatically and save some time

---

### Post by CaptainMark on 2013-02-11
After some grueling googling I'll post my finding heres, mainly so I can come and find the workaround easily if it happens again. 
When the .bashrc or .bash_profile is run and no tty is used the command " export PS1=..... " throws the error because there is no screen to print a bash prompt to, instead use

tty -s && export PS1="...."

this way the export PS1 is only used if a tty is detected, failing that use the \e[1;30\e[m method for coloring

---

