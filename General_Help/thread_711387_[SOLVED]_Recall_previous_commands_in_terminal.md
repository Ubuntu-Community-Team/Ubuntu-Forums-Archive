---
title: "[SOLVED] Recall previous commands in terminal"
date: 2008-02-29
forum: General Help
---

### Post by tstack77 on 2008-02-29
Is  there an add-on or different terminal app that can remember/recall previous commands written by the user. I have been using !! to recall the last command but I would love to have a larger history that can recall more (kind of like a favorites list).

Does this exist?

---

### Post by kish on 2008-02-29
does the command history work for your requirements?

---

### Post by spupy on 2008-02-29
Type
```
history
```
Each command in history has a number. Type this (for example)
```
!497
```
to execute command with number 497. "!" + history number.

Another thing: Press Ctrl+R and start typing. Bash will search the command history for the last command line including what you type, and autocomplete it. 
For example, if you have "firefox" in your history, pressing Ctrl+R and starting to type "fire", or "fox" or "refo" will autocomplete to "firefox".

---

### Post by RedSquirrel on 2008-02-29
You can also press the up/down arrow keys to go through commands.

You can search the history using grep:

```
history | grep xterm
```

to see the commands you have issued with "xterm" in them. ;)

---

### Post by soldats on 2008-02-29
there is also a way to use the pgup/dn keys to navigate via a few search terms like xset (pgup) would bring up the last command via xset ie. xset dpms force off which turns off my screen. there is a file to edit that makes it work that way. ill try to find it. also if you type the beginning of a command and hit "tab" twice it should bring a list of availiable commands. usually typing a part of a command and hitting tab will complete the last known sequence so just experiment. ill look for a  link fo r you.

---

### Post by y-lee on 2008-02-29
You might consider reading [The Definitive Guide to Bash Command Line History]("http://www.catonmat.net/blog/the-definitive-guide-to-bash-command-line-history/") closely. Bash is a very powerful tool and you can change how many items are stored in the history file. :)

**HISTFILESIZE** controls how many history commands to keep in the history file
To see what it is set to

```
 echo $HISTFILESIZE
```


To set it to 1000, use

```
  export HISTFILESIZE=1000
```


**HISTSIZE **controls how many history commands to keep in the history list of current session.
To see what it is set to

```
  echo $HISTSIZE
```


To set it to 1000, use

```
  export $HISTSIZE=1000
```

---

### Post by tstack77 on 2008-03-03
Great! I had no idea all this was possible and it does suite my needs!

THANKS!

---

### Post by bodhi.zazen on 2008-03-03
There is also a search function.

At the command line hit Ctrl-R

Type a few letters of the command, hit Ctrl-R to cycle through additional matches (if the first one is not he one you want)

Hit Enter to execute the command

---

