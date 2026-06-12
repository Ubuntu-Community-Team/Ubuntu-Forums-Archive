---
title: "Xubuntu Saves Commands?"
date: 2008-03-27
forum: General Help
---

### Post by everythingdaniel on 2008-03-27
Recently, I had a few graphics issues, and I had to boot into the command line to fix xorg.conf, however, during this fix-it session, I saw that the command line did something like most chat rooms do, it saves your last few "enters" and you can get to them by using the "up" arrow key.


this really struck me as odd, it even saves the commands from Terminal, Xterm, and a safe boot. It even has them back when the computer is powered down.


This really isn't a support question, but I would like more info on this interesting feature, like how many does it save? How long does it save? Just any info, and how-to would be nice.


Thanks!

---

### Post by fsmithred on 2008-03-27
I believe the default is that it saves the last 150 commands. When you get to 151, the old ones start scrolling off. You can find them in your home directory in a file called .bash_history.

---

### Post by mali2297 on 2008-03-27
It is a feature of **bash**. From the man page:
> 
HISTORY
       When interactive, the shell provides access to the command
       history,  the list of commands previously typed.  The text
       of the last HISTSIZE commands (default 500) is saved in  a
       history  list.   The shell stores each command in the his-
       tory list prior to parameter and variable  expansion  (see
       EXPANSION above) but after history expansion is performed,
       subject to the values of the shell variables  command_ori-
       ented_history and HISTCONTROL.  On startup, the history is
       initialized from the file named by the  variable  HISTFILE
       (default ~/.bash_history).  HISTFILE is truncated, if nec-
       essary, to contain no more than HISTFILESIZE  lines.   The
       builtin  command fc (see SHELL BUILTIN COMMANDS below) may
       be used to list or edit and re-execute a  portion  of  the
       history  list.  The history builtin can be used to display
       the history list and manipulate the  history  file.   When
       using the command-line editing, search commands are avail-
       able in each editing mode that provide access to the  his-
       tory  list.   When  an  interactive  shell exits, the last
       HISTSIZE lines are copied from the history list  to  HIST-
       FILE.   If  HISTFILE  is  unset, or if the history file is
       unwritable, the history is not saved.


In summary, the previous commands are saved in a hidden file **.bash_history** which is in your home folder. The commands are saved until they reach a preset maximum number of lines, then the oldest ones are deleted.

To see the max number of commands that can be saved in .bash_history, type
```

echo $HISTFILESIZE

```

---

### Post by everythingdaniel on 2008-03-27
Thanks guys! I will be looking more into this, great help!



P.S. - Reputation/Thanks has been added for both of you.

---

### Post by bapoumba on 2008-03-27
One I use a lot: <ctrl><r>, then enter letters from a command you entered previously. It will show up ^^

---

